

----
##### 연결 문서

- 
- 
- 
---

### Optional

- Optional에 앞서.. 
	
	- Null이란?
		- 자바에서 제공해주는 키워드
		- 참조형 타입의 기본 값으로 사용
		- null인 경우 할당되는 메모리가 없다.
		
	- NullPointerException 발생 케이스
		1. null 객체의 메소드나 필드를 접근하는 경우
		2. null을 throw 하는 경우
		   
	- NullPointerException을 피하는 방법
		- 참조 객체를 하용하기 전에 NPE를 방지하기 위해서는 null 체크를 하는 로직을 추가해야 한다. 
		- 매번 이렇게 Null 값을 체크하기보단 객체를 선언할 때 초기값을 사용하는 것을 권장
		  
	- Optional Class
		- 맞이할 수 밖에 없는 NPE이 발생하는 상황을 막기 위해 만들어진 클래스
		- Java 8부터 제공
		- Optional Class
		```java
		 java.util.Optional<T>
		```
		- 자바는 Optional <티>를 통해 Null을 안전하게 사용할 수 있게끔 기능을 제공
		- Optional<티> 클래스는 Null이 올 수 있는 참조 객체를 Wrapping하는 Wrappar 클래스 
		- 대표적인 Optional 사용처
			- Spring Data JPA에서 제공해주는 JPARepository
			  
	- Optional 생성
	```java
		// 객체의 선언은 Optional 클래스로 사용하고자 하는 
		// 레퍼런스 타입을 삽입하여 선언
		Optional<SampleObejct> sampleObject;
		Optional<String> optionalTextl;
		
		
		// 객체의 초기회는 empty. of ofNullable과 같은 메소드룰 
		// 통해 구현할 수 있다.
		
		// null값으로 초기화
		Optional<String> emptyObject = Optional.empty(); 
		
		//null이 아닌 경우
		Optional<String> textObject1 = Optional.of("Text"); 
		
		//null 또는 객체가 있을 수 있는 경우
		Optional<String> textObject2 = Optional.ofNullable(getText()); 
		```
		
		
	-  Optional의 다양한 메소드
		- Optoinal 클래스는 객체를 다루기 위한 다양한 메소드를 제공 
		- filter
			- 값 존재 O && 프레디케이트 일치 O : 값을 포함하는 Optional 반환 
			- 값 존재 X || 프레디케이트 일치 X : 빈 Optional 반환
		- map
			- 값 존재 O : 값이 존재하면 제공된 **매핑 함수**를 적용
		- flatmap
			- 값 존재 O : 인수로 제공된 함수를 적용한 결과 Optional 반환
			- 값 존재 X : 빈 Optional을 반환
		- isPresent / inEmpty
			- IsPresent는 최종적으로 연산이 끝나고 객체가 존재하는지 확인하는 기능 제공 
			- isEmpty는 IsPresnet와 반대로 객체가 존재하지 않으면 true를 리턴
		- ifPresent / ifPresentOrElse
			- ifPresent는 연산을 끝내고 객체가 존재한다면 그 객체를 입력값으로 주는 기능을 제공
		- get
			- 값 존재 O : Optional이 감싸고 있는 값을 반환
			- 값 존재 X : NoSuchElemnetException 발생
		- orElse
			- 값 존재 O : 값 반환
			- 값 존재 X : 기본값 반환
		- orElseGet
			- 값 존재 O : 값 반환
			- 값 존재 X : Supplier에서 생성한 값을 반환
		- the other things...


