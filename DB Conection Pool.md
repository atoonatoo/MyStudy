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
    - 
---