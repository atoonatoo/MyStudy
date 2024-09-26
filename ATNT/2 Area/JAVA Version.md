

----
##### 연결 문서

- 
- 
- 
---
- Introduction
	

- JDK 1.0a2
	- 1995년 5월
	- 언어 자체가 정식으로 발표된 날이다.
	- Oak라는 명칭으로 불리었다.
- JDK 1
	- 1996년 1월
	- 안정화 작업을 거친 1.0.2 버전에서 JAVA라는 명칭으로 바뀌었다.
- JDK 1.1
	- 1997년 2월
	
	- Inner Class 	  
	- JavaBeans
		- 자바로 작성된 소프트웨어 컴포넌트
		- Beans 규약
			1. 기본 생성자가 반드시 존재해야 한다.
			2. 모든 속성은 비공개이다.
			3. 속성에 접근하고 꺼내올 수 있는 getter, setter 메서드를 구성한다.
			4. Serializable을 구현한다.	   
	- RMI
		- Remote Method Invocation의 약자로 분산 어플리케이션을 구축하는 데 사용된다.
		- 한 시스템(JVM)에 상주하는 객체가 다른 JVM에서 실행 중인 객체에 엑세스, 호출할 수 있도록 도와주는 메커니즘이다.
		- 코드에서는 java.rmi 패키지를 통하여 제공된다.
	- Reflection
	- Calender 유니코드
- J2SE 1.2
	- 1998년 12월
	- 2부터는 약칭을 J2SE(Java 2 Standard Edition)로 표기하기 시작했으며, 이표기는 5까지 사용된다.
	
	- Swing GUI
	- JIT
	- Collection Framework
- J2SE 1.3
	- 2000년 3월
	- HotSpot JVM 
	- JNDI
	- JPDA
	- JavaSound
- J2SE 1.4
	- 2002년 2월
	
	- assert
	- 정규표현식
	- IPv6
	- XML API
	- JCE
	- JSSE
	- JAAS
	- Java Web Start
	- 
- J2SE 5
	- 2004년 9월
	  
	- 기능 변화
		1. 이때부터 버전 중 앞의 1을 빼버리고 표기하기 시작
		2. Generics
			- 5 버전의 가장 중요한 신규 기능
			- 기존에 컬렉션 프레임워크를 이요아여 발생할 수 있는 ClassCastException을 컴파일 시간에 검증할 수 있다.
			- 이러한 컴파일 검증 기능뿐만 아니라 코드에 대한 데이터를 명확하게 하여 가독성읖 높일 수 있다.
		3. Annotation
		4. Concurrency API
			- API를 사용하여 병렬 프로그래밍 혹은 멀티 스레드를 손쉽게 구현할 수 있다.
		5. Enumeration
			- 자바 개발자들은 데이터 구조를 더 쉽게 정의하고 사용할 수 있는 열거형(Enum) 기능을 원했고 자바 5에 추가되었다.
			- 이를 이용하여 클래스, 인터페이스 열거형으로, 소스 코드를 작성할 수 있다.
		6. Auto Boxin / Unboxing
			- 오토박싱/언박싱 기능을 통해 개발자가 기본형 데이터를 래퍼 클래스로 직접 변환하지 안아도 언어 차원에서 자동 변환이 가능하도록 보강되었다.
- Java SE 6
	- 2006년 12월
	  
	- 기능 변화
		1. 이때부터 표기가 J2SE에서 Java SE로 변경
		2. 가비지 컬렉터 G1(Garbage First) GC을 오직 테스트용으로만 사용하도록 추가하였다.
- Java SE 7
	- 2011년 7월
	
	- 기능 변화
		1. Diamond Operator <>
			- General Class 초기화 시 Type Interface를 지원하게 되었다.
		2. switch문에서 String 사용
			- Try-Catch 내에 선언된 Collection 등의 자원을 자동으로 close 처리한다.
- Java SE 8
	- 2014년 3월
	
	- 오라클 인수 후 첫 번째 버전이며, 2개 버전으로 나뉜다.(Oracle JDK, Open JDK)
	- 기능 변화
		- Lambda Expression
			- 메소드를 지칭하는 명칭 없이 구현부를 선언하는 익명 메소드 생성 문법이다.
			- 별도의 익명 클래스를 만들어서 선언하던 방식을 람다를 통해 대폭 간소화할 수 있으며, 함수형 프로그래밍, 스트림 API 그리고 컬렉션 프레임워크의 개선 등에 영향을 주었다.
		- Method Reference
			- 메서드 레퍼런스는 특정 메서드만을 호출하는 람다의 축약형이다.
			- 메서드 레퍼런스를 새로운 기능이 아니라 하나의 메서드를 참조하는 람다를 편리하게 표현할 수 있는 문법으로 간주할 수 있다.
		- Interface의 Default Methods
			- Java SE 8에서는 인터페이스에 디폴트 메서드라는 것이 추가되었다.
			- 인터페이스는 메서드 정의만 할 수 있고 구현은 할 수 없었지만, Java SE 8에서부터는 디폴트 메서드라는 개념이 생겨 구현 내용도 인터페이스에 포함시킬 수 있다.
		- Null 처리 Optional 추가
			- 이전까지 변수의 null 여부를 검사하고 대으아기 위해 많은 노력을 했다.
			- Java SE 8 Optional이라는 구조체를 제공해서 이전보다 간편하게 NPE(Null Pointer Exception) 이슈에 대응할 수 있다.
		- 새롭게 추가된 날짜와 시간 API
			- 기존 Date와 Calendar 클래스의 기능 부족과 비 표준적인 명명규칙, 그리고 일관되지 못한 속성 값의 문제를 해결하기 위해 새로운 날짜 API가 추가되었다.
		- Stream API
			- Stream이란 순차 / 병렬 작업을 지원하는 어떠한 순차적인 요소이다.
			- 쉽게 스트림을 데이터 컬렉션 반복을 처리하는 기능이다.
			- 람다 표현식, 함수형 인터페이스 그리고 메서드 참조를 이용한 최종 산출물이다.
			- 기존 컬렉션 프레임워크를 이용할 때보다 간결하게 코드 작성이 가능하다.
			- 병렬처리, 스트림 파이프라인 등을 통해 하나의 문장으로 다양한 처리 기능을 구현 가능하다.
		- PermGen Area 제거
			- Java 8 이전에는 초기 설정시 PermSize와 MaxPermSize를 설정해주어야 했으나, Java 8 부터는 Permanent Generation이 Metaspace로 대체 되었다.
			- Metaspace는 런타임 시 메모리 요구 사항에 따라 자체 크기를 조정하며, 필요하다면 MaxMetaspaceSize 매개변수를 설저아여 Metaspace의 양을 조절할 수 있다.
- Java SE 9
	- 2017년 9월
	  
	- 기능 변화
		- 모듈 시스템 jigsaw 
		- A New HTTP Clinet
		- Jshell - The Java Shell
		- Process API 개선
		- try - with-recources 개선
		- Diamond Operator
		- Interface Private Method
		- Optional To Stream
- Java SE 10
	- 2018년 3월
	
	- Local-Variable Type Interface
	- Garbage Collector Interface
	- Thread-Local Handshakes
	- Root Certificates
- Java SE 11
	- 2018년 9월
	
	- HTTP 클라이언트(JEP 321)
	- 새로운 String 메서드 추가
	- Lambda 파라미터로 var 사용
- Java SE 12
	- 2019년 3월
	
	- 문법적으로 Swich문을 확장
	- 가비지 컬렉터 개선, 마이크로 벤치마크 툴 추가, 성능 개선의 변경점이 있다.
- Java SE 13
	- 2019년 9월
	
	- switch문 개선을 위한 yield라는 예악어 추가
	- Text Block
- Java SE 14
	- 2020년 3월
	
	- Swich 표현(Standard)
	- record(preview)
	- 유용한 NullPointerExceptions
- Java SE 15
	- Text-Blocks / Multiline Strings
	- Sealed Classes - Preview
- Java SE 16
	- 2021년 3월
	
	- OpenJDK의 버전 관리 : Git
	- Unix-Domain Socket Channels
- Java SE 17
	- RandomGenertor (의사난수 생성기)

- JAVA에 추가된 모든 기능들