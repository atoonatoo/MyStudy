

----
##### 연결 문서

- 
- 
- 
---
##### Error vs Exception
- Error
	- 시스템이 종료되어야 할 수준의 상황과 같이 수습할 수 없는 심각한 문제를 의미
	- 개발자가 미리 예측하여 방지할 수 없다.
	  
- Exception 
	- 개발자가 구현한 로직에서 발생한 실수나 사용자의 영향에 의해 발생
	- 오류와 달리 개발자가 미리 예측하여 방지할 수 있기에 상황에 맞는 예외처리(Exception Handle)를 해야한다. 
	  
- Error vs Exception 상속 관계
	- ![[오류와 예외의 상속 관계.png]]
	
- Throwable
	- JAVA에서 예외를 처리하기 위한 최상위 클래스 
	- Throwable 클래스를 상속받은 자식 클래스들은 예외처리에서 사용하게 된다.
	- Throwable 클래스를 직접적으로 사용하는 경우는 없다.
		- 모든 예외의 조상이 되는 Exception 클래스와 모든 오류의 조상이 되는 Error 클래스의 부모 클래스이다.
	- Throwable 타입과 이 클래스를 상속받은 서브 타입만이 자바 가상 머신(JVM)이나 throw 키워드에 의해 던져질 수 있다. 
	
##### JAVA에서의 Error vs Exception

##### Error List
- 
- 
- 
##### Exception List
- 
- 
- 