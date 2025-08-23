---
created:
---

---
- [[0 Home]]
- [[2 Learning]]
---

- 개념 및 원리
    - DBCP는 백엔드 서버와 DB 서버의 TCP 기반의 통신에서 발생하는 열고 닫는 시간적 비용을 줄이고 서비스의 성능을 향상 시키기 위한 기술이다.
    - BE 서버와 DB 서버의 connection을 미리 연결하고 connection들을 관리한다.
    - BE 서버에 API 요청이 있을 경우 DB의 조회가 필요하여 쿼리요청이 필요할 경우 DBCP에 있는 풀에 놀고 있는 하나의 connection을 빌려온다.
    - 빌려온 connection을 사용하여 쿼리요청을 하여 원하는 데이터를 조회하고 쿼리응답이 끝나면 connection은 close connection 상태가 된다. 여기서 close connection은 제거가 되는 것이 아닌 pool로 반환되는 것을 의미한다. 
      
- 설정 방법
    - 스프링부트 2.0 이상 HikariCP , MySQL 기준
      
- DB 서버(MySQL) 핵심 설정
    - `max_connections`
        - client와 맺을 수 있는 최대 connections 수
        - 여기서 말하는 client는 DB 서버의 요청을 보내는 모든 것들을 client라고 한다.
        - 이를테면 현재 진행중인 프로젝트의 백엔드 서버가 client가 될 수 있겠다.
        - 가정
            - max_connections 수가 4, DBCP의 최대 connections를 4개까지 가질 수 있다고 가정할 때, 이런 상황에서 max_connection이라는 파라미터가 어떤 영향을 끼치는가?
            - 백엔드 서버에서는 트래픽이 많이 몰렸다고 가정할 경우, 요청을 처리하기 위해 바쁘게 백엔드 서버가 동작할 것이다. 
            - 바쁘게 움직이는 많큼 DB서버도 바쁘게 움직일 것이다. 
            - 그만큼 connection도 계속 바쁘게 사용되기 때문에 엄청나게 빠른 회전율이 발생할 것이다.
            - 그리고 이렇게 트래픽이 많이 몰려오면 백엔드 서버에 CPU, memory 사용량도 많아 질 것이다.
            - DBCP의 connection도 모두 사용하고 백엔드 서버 자체의 리소스 사용량도 많아지기 때문에
            - 결과적으로 백엔드 서버는 과부하가 올 것이다.
            - 이 문제를 해결하기 위해 서버를 한개 더 증설하겠다는 결정을 내린다.
            - 문제는 웹 어플리케이션을 활성화시키기 위해서는 DB서버와 DBCP를 미리 커넥션을 맺어야하는데 이미 기존 서버에 DBCP의 최대 connection을 맺은 상태이기 때문에, 미리 맺을 수 없게 된다.
        - 그렇기 때문에 `max_connection`은 신규 서버를 추가하거나 기존의 서버에 DBCP를 충분히 더 늘린다고 하더라도 에러가 발생하지 않고 정상적으로 동작할 수 있게끔 적절하게 충분한 값을 설정해야 한다.
          
    - `wait_timeout`
        - connection이 inactive(놀고 있을 때)할 때 다시 요청이 오기까지 얼마의 시간을 기다린 뒤에 close할 것인지 결정
        - 예외적인 상황을 목적으로 존재한다.
            - 비정상적인 connection 종료
            - connection 다 쓰고 반환이 안됨.
            - 네트워크 단절
        - 이러한 비정상적인 상황들은 DB 서버가 인지하고 있지 못하고 하염없이 연결되어 기다리고 있게 되고 이런 상태가 1개 2개 많아 지다보면 계속 리소스를 점유하게 되는 것이고 나중에는 DB 서버의 안좋은 영향을 끼칠 수 있기 때문에 적절한 시점에서 이 문제를 해결해줘야한다.
        - 이때 사용되는 파라미터가 `wait_timeout`이다.
        
- DBCP(HikariCP) 핵심 설정
    - 백엔드 서버에서 DBCP 설정에 어떤 것들이 있는지 살펴보자.
          
    - `minimumIdle`
        - pool에서 유지하는 최소한의 idle(놀고 있는 유후 자원) connection의 수
        - idle connection 수가 minimumIdle보다 작고, 전체 connection 수도 maximumPoolSize보다 작다면, 신속하게 추가로 connection을 만든다.
        - 즉, `maximumPoolSize` 파라미터가 `minimumIdle`보다 우선 순위가 높다는 것을 알 수 있다.
    - `maximumPoolSize`
        - pool이 가질 수 있는 최대 connection의 수
        - idle, active(in-use) connection 합쳐서 최대 수
    - HikariCP 공식 문서에는 minimumIdle의 기본 값을 maximumPoolSize과 동일하게 하는 것을 권장한다고 한다. (= pool size 고정)
        
    - `maxLifetime`
        - pool에서 connection의 최대 수명
        - maxLiftime을 넘기면 idle일 경우 pool에서 바로제거하고, active인 경우 pool로 반환된 후 제거
        - pool로 반환이 안되면 maxLifetime은 동작 하지 않는다.
        - 그렇기 때문에 다쓴 connection은 pool로 잘 반환시키는 것이 중요하다.
        - DB connection time limit보다 몇초 짧게 설정해야
          
    - `connectionTimeout`
        - pool에서 connection을 받기 위한 대기 시간
---