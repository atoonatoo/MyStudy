

----
##### 연결 문서

- 
- 
- 
---

##### 계층화 아키텍처 : 
- 계층화 아키텍처란?
	- 어플리케이션 내에서 특정 역할과 관심사(화면 표시, 비지니스 로직 수행, DB 관리)에 구분된다. 이는 계층화 아키텍처의 관심사의 분리를 의미한다. 각 계층은 각자만의 기능만을 수행하기 때문에, 높은 유지 보수성과 테스트에 용이 하다는 장점이 있다.
	  
- 4-Tier Layered Architecture
	- Pregentation Layer
		- 사용자가 데이터를 전달하기 위해 화면에 표시를 하는데에 주로 관심를 가진다.
		- 비지니스 로직이 어떻게 수행되는지 알 필요가 없다.
		- 대표적인 구성 요소 View, Controller
	- Business Layer 
		- 비지니스 로직을 수행하는 것을 주로 관심사를 둔다.
		- 화면에서 데이터를 출력하는 방법, 혹은 데이터를 어디서 가져오는지에 대한 내용을
		  알 필요가 없다. 
		- 대표적인 구성 요소 Service, Domain Model
	- Persistence Layer
		- 어플리케이션의 영속성 구현하기 위해, 데이터 출처와 그 데이터를 가져오고 
		  다루는 것을 주로 관심사로 둔다.
		  대표적인 구성 요소 Repository, DAO
		- Repository, DAO
	- Database Layer
		- 데이터 베이스가 위치한 계층을 의미한다.
		- Mysql, maria DB , OracleDevelopmen
		
- 수직적으로 구성된 격리된 레이어 (Layers of isolation)
	- 각각의 나뉘어진 수평 계층은 수직적으로 배치된다.
	- Layered Architecture의 주요 특징 중 하나
	- 이런 구조에서 특정 레이어는 바로 하위 레이어에만 연결된다.
	  
- 그냥 프레젠테이션 레이어에서 그냥 데이터베이스 레이어에 연결해서 정보를 가져오면?
	1. 프리젠테이션 레이어에서 직접 데이터베이스에 접속
	2. SQL에 대한 변경사항이 프리젠테이션 레이어에 직접 영향 미침
	3. 과도한 의존성이 발생
	4. 즉, 어플리케이션의 변경을 매우 어렵게 만듬
	   
- Layered Architecture를 잘 지킨다면?
	- 각 레이어가 다른 레이어와 독립적이므로 특정 레이어는 다른 레이어의 내부 동작을 모르게 된다.
	- 즉 각계층은 캡슐화되어 있고, 단일 책임을 갖는다. 
	- 따라서 특정 레이어는 다른 레이어에 영향을 주지 않고 변경될 수 있다.
  
- Layered Architecture 시나리오
	- 사용자가 특정 고객 정보를 요청한 상황을 가정하여, 
	  Layered Architecture 가 이 요청을 수행하는 시나리오를 정리해보자.
	  
	1. 사용자가 보고있는 화면(Customer Screen, 흔히 말하는 View 라고 할 수 있을 것 같다)에서 사용자는 고객 정보를 요청한다.
	2. 이 요청은 그 요청을 처리할 수 있는 모듈이 무엇인지 알고있는 Customer Delegate (흔히 말하는 Controller 라고 할 수 있을 것 같다) 로 전달된다. Customer Delegate 는 해당 요청을 처리하기 위해 Business Layer 의 Customer Object 로 요청을 다시 전달한다.
	3. Customer Object는 요청을 받고 비즈니스 로직을 수행하기 위한 데이터를 얻기 위해, Persistence Layer의 Customer dao 와 Order dao 에 요청을 보낸다.
	4. Persistence Layer 의 DAO들은 요청을 수행하기 위해 Database Layer 에 접근하여 데이터를 가져온다.
	5. 이 요청은 다시 반대로 Persistence Layer → Business Layer → Presentation Layer 로 전달되고 최종적으로 사용자에게 전달된다.
	
- 싱크홀 안티패턴을 주의하자 !
	- 싱크홀 안티패턴이란?
		- 특정 레이어가 아무런 로직도 수행하지 않고 들어온 요청을 그대로 
		  다시 하위 레이어로 내보내는 경우를 의미
		- 이런 흐름은 불필요한 리소스 낭비를 초래한다.
		- 전체흐름 중에서 약 20%가 싱크홀이라면 그럭저럭 나쁘지 않은 수준이라고 함