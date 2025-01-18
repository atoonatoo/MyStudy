


----
##### 연결 문서

- 
- 
- 
---

### Java 문법
	
- 문법의 나만의 정의
	- 메인 클래스
		개발자가 임의적으로 사용한 코드를 가동시키기 위한 시작점으로 
		메인클래스의 위치, 메인 클래스가 의미하는 바, 메인 클래스가 허용하는 범위 등을 
		알아 둘 필요가 있다.
	- 주석
		'//'를 텍스트 앞에 붙이면 그 글자를 코드로 인식하지 않는다.
		주석은 다양한 용도로 사용 되고 있다.
		코드에 관한 간략한 설명, 메모하기 위한 용도, 임시로 코드를 비활성화 하기위함 등
		다만, 협업을 하면서 주석으로된 코드를 남겨두고 PR을 보내는 것은 
		매우 안좋은 행위라는 것을 명심하자.
	- 자바의 명명 규칙
		카멜케이스는 개발자들이 협의한 문자의 명명 규칙을 의미한다.
		이는 가독성과 오해 및 착각을 방지하기 위한 일종의 협약이다.
		즉 실질적인 개발자가 이러한 카멜케이스를 지키지 않는 다는 것은
		매우 기본적인 것도 지키지 못하는 것이라는 것이기에 항상 습관화되고
		명심해두어야한다.
	- 자료형
		우리가 어떠한 데이터를 저장할 때 해당 공간에 어떤 타입으로 저장할지를 
		정하는 것이다.
		기본형에선 정수형 실수형 문자형 논리형
		참조형에선 배열형 인터페이스형 클래스형이 있다.
	- 변수
		우리가 데이터를 덮어쓸수 있는 공간을 의미한다.
		변수를 사용하려면 초기화와 선언이 필요하다.
	
- 인텔리제이 셋팅
	- 커뮤니티 or 얼티메이트
		- 커뮤니티 : 무료 , 지원 기능이 적다.
		- 얼티메이트 : 유료, 지원 기능이 많다.
	- Keymap: 윈도우 > 이클립스
		단축키를 이클립스 단축키로 바꿔주는 세팅이다.
	-  Font : 크기 조정
		작업할 때 보기 편한 크기 조정이 가능하다.
	- Plug In : rainbow brackets
		코드 블락의 색깔을 입혀서 코드의 범위를 구분하기 쉽게 한다.
	- JRA : 자바 가상 실행 환경
		자바가 어디서든 실행 가능하다.
		가상 컴퓨터이기 때문에 느린 언어이다.
		그래서 속도가 엄청 빠를 필요가 없는 프로그램인 
		웹 프로그램 등에서 사용한다.
	- Pakege : 폴더
	- Source File, Class : 파일
		
	- 자바 키워드 리스트
		- <https://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html>
	- 아스키 코드 리스트
		- <https://www.asciitable.com/>
	- 자바가 왜 어떤 환경에서도 실행이 가능하고 왜 JRA가 느린가?
	  
- 메인 클래스 / 주석 / 자바의 명명 규칙
	
	```java 
	
	// 메인 클래스
	
	package day0430;
		
	public class Ex01 {	    
		public static void main(String[] args) {
		System.out.println("Hello, WORLD!!!");
	   }
	}
	
	
	//주석(Comment)
	//주석이란 소스파일에 적혀져있지만
	//실제 컴파일 단계에서는 무시가 되는 글자들을 주석이라고 한다.
	//주석을 사용하는 이유는 자신이 쓴 코드에 대한 설명을 적기 위함이다.
	//주석에는 크게 한줄 주석과 여러줄 주석이 있는데
	// 한줄 주석은 // 부터 엔터지 전까지의 모든 글자들을 주석으로 처리한다.
	/*여러줄 주석은 /*으로 시작하고
	 */ //가 나오기 전까지의 모든 코드를 주식으로 처리한다.
	
	public class Ex02Comment {
	    public static void main (String[] args){
	        System.out.println("1번째 줄 출력");
	        System.out.println("1번째 줄 출력");
	        System.out.println("1번째 줄 출력");
	
	        //   System.out.println("1번째 줄 출력");
	        System.out.println("2번째 줄 출력");
	        System.out.println("3번째 줄 출력");
	        System.out.println("4번째 줄 출력");
	        //   System.out.println("5번째 줄 출력");
	        
	        /*
	        System.out.println("1번째 줄 출력");
	        System.out.println("2번째 줄 출력");
	        System.out.println("3번째 줄 출력");
	        System.out.println("4번째 줄 출력");
	        System.out.println("5번째 줄 출력");
	        */
	    }
	}
	
	
	
	/*
	자바의 명명규칙(Notation)
	 1. 공통 규칙
	     A. 자바는 대소문자를 엄격히 구분한다.
	     B. 자바에서 이름을 지을 때에는 이름 안에는 _를 제외한 
		    특수 문자를 넣을 수 없다.
	     C. 이름 중간이나 끝에 숫자가 나올 수 있지만 시작할 때에는 숫자를 넣을 수 없다.
	     D. 자바에서는 내부적으로 중요하게 사용되는 50여가지의 예약어(keyword)가 
		    존재하고 해당하는 이름으로는 이름을 지어줄 수 없다.
		    IDE들은 해당 키워드들을 특별하게 표시를 해주기 때문에
	        만약 여러분들이 지어준 이름이 특별하게 표시가 되면 
	        동의어를 사용하거나 아니면 변형을 가해주면 된다.
	
	 2. 낙타등 표기법(Camel back notation)
	    낙타등 표기법은 대소문자를 길이 사용할 때에 여러 단어로 이루어질 경우,
	    2번째 단어부터는 첫 글자를 대문자로 적어주는 방법이다.
	
	 3. 뱀 표기법(Snake Notation)
	    뱀 표기법은 모든 단어를 대문자로 나타낼 때에 단어 사이에 _를 넣는 방법이다.
	
	 4. 종류에 따른 이름 짓기
	     A. 클래스 : 첫글자를 대문자로 시작하고 낙타등 표기법을 사용하는 명사,
	     B. 패키지 : 해당 패키지 아넹 클래스들의 성격을 잘 나타내는 한 단어의 명사
	     C. 변수 : 첫 글자를 소문자로 시작하고 낙타등 표기법을 사용하는 명사
	     D. 상수 : 뱀 표기법을 사용하는 명사(무조건 대문자)
	     E. 메소드 : 첫글자를 소문자로 시작하고 낙타등 표기법을 사용하는 동사
	                프로그램 규칙상, 메소드는 반드시 이름뒤에 ()가 온다.
	                
	        ex) : 1. UNIT_PRICE : 상수
	              2. print() : 메서드
	              3. UserController : 클래스
	              4. userController : 변수
	*/
	public class Ex03Notation {
	      ex) : 1. UNIT_PRICE : 상수
	            2. print() : 메서드
	            3. UserController : 클래스
	        4. userController : 변수
	}
	```
	
- 자료형 / 변수 / 상수 / 기본형, 실수형 데이터 타입 / 기본형 데이터타입 문자형 , 논리형
	```java
	package day0430;
	/*
	자료형(Data Types)
	자료형이란, 우리가 어떠한 데이터를 저장을 할때에 해당 공간에
	어떤 종류의 데이터를 저장할 수 있는지를 지정하는 것이다.
	
	자료형에는 크게 2가지 종류가 있다.
	
	1. 기본형
	   기본형 안에는 또 4가지 종류가 있다.
	   A. 정수형
	      byte, short, **int**, long
	   B. 실수형
	      float, **double**
	   C. 문자형
	      char
	   D. 논리형
	      boolean
	
	2. 참조형
	   참조형에는 크게 배열형, 인터페이스형, 클래스형 3가지가 있다.
	*/
	public class Ex04DataType {
	
	}
	
	
	/*
	변수(Variable)
	변수란, 우리가 값을 여러번 덮어씌울 수 있는 공간을 변수라고 한다.
	변수를 사용하기 위해서는 선언과 초기화가 필요하다.
	
	변수의 선언방법 : 데이터타입 변수이름;
	변수의 초기화방법 : 변수이름 = 값;
	*/
	public class Ex05Variable {
	    public static void main(String[] args){
		    
	        //int 타입의 변수 myNumber를 선언해보자
	        int myNumber;
			
	        // myNumber는 현재 선언만 된 상태이므로 초기화를 하기 전 까지는 
	        // 사용을 할 수 없다.
			
	        // myNumber의 현재값을 출력하시오
	        // System.out.println(myNumber); -> myNumber에 아무런 값이 없으므로 
	        // 에러 발생
			
	        // myNumber에 5를 저장해보자
	        // 초기화, 할당, 저장 모두 프로그래밍에서는 같은 의미가 된다.
	        myNumber = 5;
	        System.out.println("myNumber에 현재 저장된 값");
	        System.out.println(myNumber);
			
	        //myNumber에 10을 저장해보자
	        myNumber = 10;
			
	        // myNumber에 현재 저장된 값을 출력해보자
	        System.out.println("myNumber에 현재 저장된 값");
	        System.out.println(myNumber);
	    }
	}
	
	
	/*
	상수(Constant)
	상수란, 한번 값이 초기화가 되면 더이상 새로운 값을 저장할 수 없는 공간을 뜻한다.
	
	상수의 경우, 선언할 때 맨 앞에 final이라는 키워드를 붙여주면 
	해당 공간은 상수로 설정이 된다.
	*/
	public class Ex06Constant {
	    public static void main(String[] args) {
	        // int 타입 상수 MY_NUMBER을 선언해보자
	        final int MY_NUMBER;
			
	        // 상수 MY_NUMBER에 20을 저장해보자
			
	        MY_NUMBER  = 20;
			
	        // MY_NUMBER의 현재 값을 출력해보자
	        System.out.println("MY_NUMBER의 현재 값");
	        System.out.println(MY_NUMBER);
			
	        // MY_NUMBER에 새로운 값 30을 저장해보자
			
	        // MY_NUMBER = 30; -> MY_NUMBER는 상수이므로 값을 더이상 저장할 수 없다.
			
	        // MY_NUMBER에 20을 저장하자 -> 컴퓨터의 = 은 
	        // 무조건 덮어씌우는 의미가 되므로 
	        // 현재 저장된 값과 새로운 값이 같던 다르던간에 무조건 에러가 발생이 된다.   
	    }
	}
	
	
	/*
	기본형 데이터타입
	
	01. 정수형 데이터타입
	정수란?
	소숫점이 존재하지 않는 숫자
	
	정수형 기본형 데이터타입에는
	byte -128~127까지 총 2^8개의 숫자
	short -2^15~2^15-1까지 총 2^16개의 숫자 -> 8비트 -> 1바이트
	int -2^31~2^31-1까지 총 2^32개의 숫자
	long -2^63~2^63-1까지 총 2^64개의 숫자
	4가지 종류가 있다.
	
	마음 편하게 +- 20억 내외의 숫자를 사용할 때에는 int
	그것보다 큰 숫자를 사용할 경우에는 long을 사용하자
	*/
	public class Ex07Integer {
	
	}
	
	
	/*
	기본형 데이터타입 02. 실수형 데이터타입
	실수란?
	소숫점이 존재하는 숫자
	float : 32비트의 실수체계
	double : 64비트의 실수체계
	*/
	public class Ex08RealNumber {
	}
	
	
	/*
	기본형 데이터타입 : 문자형
	char : 해당 공간의 1개의 글자만 저장한다.
	비록 char로 적어주면 "차"라고 읽으면? 아주 옛날에 코딩을 배운 사람
	"캐릭터"로 읽는 것이 맞다.
	값을 저장할 때에는 값을 ' '로 감싸준다.
	
	char의 경우, 실제로는 ASCII 코드 라는 특수한 문자값 표를 사용하기 때문에, 
	숫자로 글자를 표현할 수 있다.
	*/
	public class Ex09Character {
	    public static void main(String[] args) {
	        // char 타입의 변수 myChar에 65라는 값을 저장해라
	        char myChar = 65;
	
	        //myChar의 현재값을 출력해라
	        System.out.println("myChar의 현재 값");
	        System.out.println(myChar);
	    }
	}
	
	
	/*
	기본형 데이터타입 04. 논리형
	논리형 데이터타입은 boolean이라는 데이터타입만 존재하고
	boolean 데이터타입에는 딱 2가지 값만 저장 가능하다.
	true false
	*/
	public class Ex10Boolean {
	    public static void main(String[] args){
	        // boolean 변수 isTrue를 선언하고 true 값으로 초기화해라
	        boolean isTrue = true;
	        //isTrue의 현재 값을 출력해라
	        System.out.println("isTrue의 현재 값");
	        System.out.println(isTrue);
	
	        //boolean 변수 isFalse를 선언하고 false로 초기화해라
	        boolean isFalse = false;
	
	        //isFalse의 현재 값을 출력해라
	        System.out.println("isFalse의 현재 값");
	        System.out.println(isFalse);
	    }
	}
	
	```
	
- 형 변환 / 연산자 / 할당 연산자 / 비교 연산자
	```java
	package day0430;
	
	/*
	
	형 변환(Type Casting)
	
	형 변환이란, 특정 데이터타입의 값을 다른 데이터타입으로 바꾸는 것을 뜻한다.
	형 변환에는 2가지 종류가 있는데 암시적 형변환과 명시적 형변환 2가지가 있다.
	
	암시적 형변환(Implicit Type Casting)
	우리가 직접적으로 형변환을 하는 명령어를 적어주지 않더라도
	인터프리터가 알아서 형변환을 자동으로 해준다.
	더 작은 데이터타입의 값을 더 큰 데이터타입으로 변환하거나
	데이터 손실이 발생하지 않을 경우에 암시적 형변환이 발생된다.
	
	명시적 형변환(Exlicit Type Casting)
	명시적 형변환은 반드시 명령어를 적어서 강제로 형변환을 해주는것을 뜻한다.
	더 큰 데이터타입의 값을 저 작은 데이터타입으로 변환하거나 데이터 손실이 발생할 경우
	반드시 명시적 형변환을 통해서 형변환을 해주어야 한다.
	
	*/
	
	public class Ex11TypeCast {
	    public static void main(String[] args) {
	
	        //암시적 형변환
	        //1. byte의 값을 int 공간에 담아보자
	        //1-1. byte 변수 myByte를 선언하고 30을 저장해보자
	        byte myByte = 30;
	
	        //1-2. int 변수 myNumber를 선언하고 myByte의 현재 값으로 초기화해보자
	        int myNumber = myByte;
	        //1-3. myNumber의 현재값을 출력해보자
	        System.out.println("myNumber의 현재 값");
	        System.out.println(myNumber);
	
	        //2. 정수를 실수로 바꿔보자
	        //double 변수 myDouble에 myNulber의 현재 값을 저장해보자
	        double myDouble = myNumber;
	        System.out.println("myDouble의 현재 값");
	        System.out.println(myDouble);
	
	        // 명시적 형변환
	        // 명시적 형변환은 변환할 값 앞에 바꿀 데이터타입을 ()로 감싸서 저장한다.
	        // myNumber의 현재 값을 myByte에 저장해보자
	        myByte = (byte) myNumber;
	        // myByte의 현재 값을 출력해보자
	        System.out.println("myByte의 현재 값");
	        System.out.println(myByte);
	
	        //실수를 정수로 바꿀때에도 명시적 형변환이 필요하다.
	        //myNumber에 myDouble의 현재 값을 저장해보자
	        myNumber = (int)myDouble;
	
	        //번외, overflow, underflow 체험해보기
	        //myByte에 128을 저장하고 출력해보자
	        myByte = (byte) 128;
	        System.out.println("myByte의 현재 값");
	        System.out.println(myByte);
	        
	        //myByte에 -129를 저장하면?
	        myByte = (byte) -129;
	        System.out.println("myByte의 현재 값");
	        System.out.println(myByte);
	    }
	}
	
	
	/*
	
	연산자(Operator)
	
	연산자란 수학적 기호에 프로그래밍 기능을 정의한 것이다.
	연산자에는
	산술연산자, 증감연산자, 할당연산자, 논리연산자, 비트연산자
	5가지가 있지만 우리는 그 중에서 비트 연산자는 배우지 않는다.
	
	산술연산자
	산술연산자는 2개의 값에 대한 기본적인 산수 계산을 하는 연산자이다.
	+ - * / % 5가지가 있다.
	  
	*/
	
	public class Ex01Operator {
	    public static void main(String[] args) {
		    
	    // 1. 정수끼리 산술 연산
	    // int 변수 myNumber1, myNumber2를 선언하고
	    // 각각 5와 3으로 초기화해보자
		int myNumber1 = 5, myNumber2 = 3;
		System.out.println("myNumber1 + myNumber2 = " + 
		(myNumber1 + myNumber2));
		System.out.println("myNumber1 - myNumber2 = " + 
		(myNumber1 - myNumber2));
	    System.out.println("myNumber1 * myNumber2 = " + 
	    (myNumber1 * myNumber2));
	    System.out.println("myNumber1 / myNumber2 = " + 
		(myNumber1 / myNumber2));
		System.out.println("myNumber1 % myNumber2 = " + 
		(myNumber1 % myNumber2));
			
	    // 실수와 실수의 산술연산
	    // double 변수 myDouble1, myDouble2를 선언하고 각각 5.0과 3.0으로 초기화
	    double myDobule1 = 5.0, myDouble2 = 3.0;
	    System.out.println("myDobule1 + myDouble2 = " + 
	    (myDobule1 + myDouble2));
	    System.out.println("myDobule1 - myDouble2 = " + 
	    (myDobule1 - myDouble2));
	    System.out.println("myDobule1 * myDouble2 = " + 
	    (myDobule1 * myDouble2));
	    System.out.println("myDobule1 / myDouble2 = " + 
	    (myDobule1 / myDouble2));
	    System.out.println("myDobule1 % myDouble2 = " + 
	    (myDobule1 % myDouble2));
			
	    // 정수와 실수의 산술연산
	    // 이때에는 정수가 암시적 형변환을 통해 실수로 변환이 되어 
	    // 실수와 실수의 산술연산이 일어나게 된다.
	    // 국영수 점수를 저장할 int 변수 3개를 만들고 각각 90, 90, 91을 저장하자
	    int korean = 90, english = 90, math = 91;
	        
	    // 총점을 계산해보자
	    int sum = korean + english + math;
	        
	    // 평균을 계산해보자. 단 평균은 실수로 나와야 한다.
	    double average1 = sum / 3;
	    double average2 = sum / 3.0;
	    double average3 = (double) sum / 3;
			
	    // 평균을 출력해보자
	    System.out.println("평균점수 : " + average1);
	    System.out.println("평균점수 : " + average2);
	    System.out.println("평균점수 : " + average3);
			
	    // String
	    // String은 여러 글자를 다룰 수 있는 데이터타입이다.
	    // String 클래스의 값은 ""로 감싸서 나타낸다.
	    // String 클래스의 값은 + 연산이 가능하다.
	    // String 클래스의 값의 + 연산은 앞에 값과 뒤의 값을 이어서 
	    // 하나의 스트링으로 만들라는 연산이 된다.
	    // 만약, 다른 데이터타입의 값과 String 클래스의 값이 + 연산이 될 경우, 
	    // 다른 데이터타입을 String 클래스 값으로 변환하여 이어붙이게 된다.
	    }
	}
		
		
	/*
	할당연산자  
	
	오른쪽 값을 산술 연산한 값을 왼쪽 공간에 저장할 때 사용이 된다.  
	=, +=, -=, *=, /=, %=  
	  
	증감연산자  
	해당 연산자가 달린 공간의 값을 1씩 증가시키거나 감소시킨다.  
	++, --  
	*/
	public class Ex02Operator {  
	    public static void main(String[] args) {  
	    // int 변수 myNumber를 선언  
	    int myNumber;  
	    // 1. =  
	    // myNumber에 4를 저장  
	    myNumber = 4;  
	    // myNumber의 현재 값을 출력  
	    System.out.println("myNumber = " + myNumber);  
		  
		// 2. +=  
	    // 위의 연산자를 풀어서 쓰면?  
	    // myNumber = myNumber + 3;        
	    // myNumber += 3; 과 같은 형태가 된다.  
	    System.out.println("myNumber = " + myNumber);  
			  
	    // 2. -=  
	    // 위의 연산자를 풀어서 쓰면?  
	    // myNumber = myNumber - 3;        
	    // myNumber -= 5; 과 같은 형태가 된다.  
	    System.out.println("myNumber = " + myNumber);  
	    
	    
	/*
	증감연산자  
	
	증감연사자는 해당 변수의 값을 1씩 변화시키지만  
	변수의 앞에 붙냐 뒤에 붙냐에 따라서    실행 순서가 바뀐다.  
	앞에 붙을 때에는 가장 높은 우선순위를 갖고(=가장 먼저 실행되고)  
	전위 증감연산자 라고 부른다.  
	뒤에 붙을 때에는 가장 낮은 우선순위를 갖고(=가장 나중에 실행되고)  
    후위 증감연산자라고 부른다.  
	  
	int 변수 my Number1과 Number2를 선언하고 각각 5와 4로 초기화하자  
	*/ 
		int myNumber1 = 5, myNumber2 = 4;  
	    System.out.println("myNumber1++" + myNumber1++);  
	    System.out.println("myNumber1 : " + myNumber1);  
	    System.out.println("++myNumber2 : " + ++myNumber2);  
	    System.out.println("myNumber2 : " + myNumber2);  
	    System.out.println(++myNumber2 - myNumber1--);  
	    
		//화면에 출력되는 값과 출력된 후의 myNumber1, myNumber2의 값을 적으시오 
		 
	    }  
	}
	
	
	/*
	비교연산자  
	 
	비교연산자는 왼쪽과 오른쪽의 값을 비교를 하되  
	우리가 생각하는 것처럼 자동으로 어디가 더 큰지를 반환하는 것이 아니라  
	컴퓨터에게 왼쪽의 값이 오른쪽의 값보다 크니? 의 형식으로 질문을 하여  
	예/아니오 -> true/false 의 결과값을 받는 형식이 된다.  
	<, <=, >, >=, ==, !=  
	*/ 
	public class Ex03Operator {  
	    public static void main(String[] args) {  
	        // int 타입의 변수 myNumber1, myNumber2를 선언하고  
	        // 각각 4와 5로 초기화하자  
	   int myNumber1 = 4, myNumber2 = 5;  
	   System.out.println("myNumber1 < myNumber2= " + 
	   (myNumber1 < myNumber2));  
       System.out.println("myNumber1 < 3= " + (myNumber1 < 3));  
	   System.out.println("myNumber1 < 4= " + (myNumber1 < 4));    
	   System.out.println("myNumber1 <= myNumber2= " + 
	   (myNumber1 <= myNumber2));  
	   System.out.println("myNumber1 <= 3= " + (myNumber1 <= 3));  
       System.out.println("myNumber1 <= 4= " + (myNumber1 <= 4));    
	   System.out.println("myNumber1 == myNumber2= " + 
	   (myNumber1 == myNumber2));  
	   System.out.println("myNumber1 != myNumber2= " + 
	   (myNumber1 != myNumber2));  
	  
	// 단 비교연산자의 경우, 기본형 데이터타입의 값에 대해서만  
	// 정확한 결과가 나오고, 참조형 데이터타입일 경우,  
	// 부정확한 결과가 나올수도 있다.  
	  
	// 스트링 변수를 만들어보는데, 초기화 방법은 각각 다른 방법으로 해보자  
	   String string1 = "abc";  
	   String string2 = new String("abc");  
	   String string3 = string1;  
	  
	// 3개의 String 변수의 값이 같은지 확인해보자  
	   System.out.println("string1: [" + string1 + "]");  
	   System.out.println("string2: [" + string2 + "]");  
	   System.out.println("string3: [" + string3 + "]");  
	  
	   System.out.println("string1 == string2= " + (string1 == string2));  
	   System.out.println("string1 == string3= " + (string1 == string3));  
	   System.out.println("string2 == string3= " + (string2 == string3));  
	
	/*
	 JRE에는 크게 3가지 메모리 영역이 있다.  
     1. Stack : 변수의 값이 저장되는 공간  
	 2. Heap : 참조형 값이 저장되는 공간  
	 3. Method : 현재 실행시킬 코드가 줄 단위로 저장되어 실행되는 공간  
	  
	 참조형 변수와 기본형 변수의 차이  
	 기본형 변수: Stack 영역에, 현재 값을 2진법으로 변환한 값이 저장된다.  
	 참조형 변수: 
	 Heap 영역에 현재 값이 저장이 되고, 
	 Stack 영역에는 해당 값이 저장된 주소값이 저장된다.    
	
	 기본적으로 연산자는 힙 영역에 아예 들어가지 않고 
	 스택 영역에 값을 기준으로 연산을 한다.  
	 따라서, 비교 연산자로 스트링의 값을 비교할 시에는  
	 주소값 비교를 하기 때문에, 부정확한 결과가 나올수 있게 된다.    
	
	 따라서, 참조형 데이터타입 중, 클래스형 혹은 인터페이스형의  
	 값을 비교할 때에는 우리가 == 또는 != 이 아닌  
	 equals()를 통하여 비교를 해야 한다.  
	
	 equals는 다음과 같은 방법으로 사용한다.  
	 공간.equals(비교대상) 
	 equals를 통해서 비교를 해보자
     string1의 현재 주소값에 저장된 값이  
     string2의 현재 주소값에 저장된 값과 같습니까?  
    */
    
	System.out.println("string1.equals(string2): " + string1.equals(string2));     System.out.println("string1.equals(string3): " + string1.equals(string3));     System.out.println("string2.equals(string3): " + string2.equals(string3)); 
    System.out.println("abc.equals(string2): " + "abc".equals(string2));  
	    }  
	}
	```
	
- PrintF / Scanner / If / If Else / Else If 
	```java
	package day0501;  
	/*
	printf
	
	printf의 다양한 형식  
	우리가 필요에 따라서는 printf를 사용해서  
	우리가 원하는 내용을 콘솔에 지정한 형식으로 출력이 가능하다.  
	단, 우리가 웹 프로그래밍에 들어가게 되면  
	더이상 출력하는 곳이 콘솔이 아니기 때문에 사용되지 않는다.  
	*/
	public class Ex06Printf {  
	    public static void main(String[] args) {  
	        //정수 출력에 사용할 int 변수  
	        int number = 15;  
	        //1. 10진법 정수(Decimal)  
			  
	        //A. 10진법 정수를 그대로 출력해라  
	        System.out.printf("1-A. [%d}\n", number);  
	        //B. 10진법 정수를 오른쪽 정렬 5자리로 출력해라  
	        System.out.printf("1-B. [%5d}\n", number);  
	        //C. 10진법 정수를 왼쪽 정렬 5자리로 출력해라  
	        System.out.printf("1-C. [%-5d}\n", number);  
	        //D. 10진법 정수를 오른쪽 정렬 5자리로 출력하되, 
	        
	        //   왼쪽 빈자리는 0으로 채워라  
	        System.out.printf("1-D. [%05d}\n", number);  
	        System.out.println("===========================");  
	        System.out.println();  
	        System.out.println("===========================");  
	        
	        // 2. 실수  
	        // A. 실수 출력에 사용할 double 변수  
	        double myDouble = 3.141592;  
	        System.out.println("2. 실수");  
	        System.out.println("---------------------------");  
	        System.out.printf("2-A. [%f] \n", myDouble);  
	        System.out.println("===========================");  
	  
	        // B. 실수를 오른쪽 정렬 10자리로 출력해라  
	        System.out.printf("2-B. [%10f] \n", myDouble);  
	        System.out.println("===========================");  
			  
	        // C. 실수를 왼쪽 정렬 10자리로 출력해라  
	        System.out.printf("2-C. [%-10f\n", myDouble);  
	        System.out.println("===========================");  
			  
	        // D. 실수를 오른쪽 정렬 10자리로 출력하되 왼쪽 빈 자리는 
			//    0으로 채워라  
	        System.out.printf("2-D. [%010f\n", myDouble);  
	        System.out.println("===========================");  
			  
	        // E. 실수를 소숫점 2번째 자리까지 출력해라  
	        System.out.printf("2-E. [%.2f]\n", myDouble);  
	        System.out.println("===========================");  
	        System.out.println();  
	        System.out.println("===========================");  
	        System.out.println("3. 스트링(String)");  
	        System.out.println("----------------------------");  
	        
	        // A. String을 그대로 출력해라  
	        System.out.printf("3-A. [%s]\n", "abcdEFGH");  
	        // B. String을 모두 대문자로 출력해라  
	        System.out.printf("3-B. [%s]\n", "abcdEFGH");  
	        // C. String을 오른쪽 정렬 10자리로 출력해라  
	        System.out.printf("3-C. [%s]\n", "abcdEFGH");  
	        // D. String을 왼쪽 정렬 10자리로 출력해라  
	        System.out.printf("3-D. [%s]\n", "abcdEFGH");  
	        // 단, 왼쪽 빈 자리를 0으로 채워라는 0도 문자이기 때문에 불가능하다.  
			  
	        // 만약 printf로 여러개의 형식을 맞추어 출력해야한다면?  
	        System.out.printf("%2d %03d %08d\n", 1, 2, 3);  
	        
	        /*  
	        여러분들이 자유롭게 변수를 만들어서 다음과 같은 형식으로 
	        출력이 되는 코드를 작성해보세요.  
	        결과물 :
	        이름: ### 나이: 0##세  
	        국어 : 0##점 영어 : 0##점 수학 : 0##점  
	        총점 : 0##점 평균 : 0##.##점  
			*/  
			 
	        String name = "김동욱";  
	        int age = 32;  
	        int kor  = 89;  
	        int eng = 100;  
	        int math = 99;  
	        int total = kor + eng + math;  
	        double averege = (double) total / 3;  
			
	   System.out.printf("이름 : %s 나이 : %03d세\n", name, age);  
	   System.out.printf("국어 : %03d점 영어 : %03d점 수학 : %03d점
	   \n",kor,eng,math);  
	   System.out.printf("총점 : %03d점 평균 : %06.2f점\n", total,averege);  
	    }  
	}
	
	
	/*
	Scanner  
	
	자바에서 각종 입력(키보드, 파일, 데이터 스트림)을 처리할 때 쓰이는 클래스이다.  
	우리가 키보드 입력을 받기 위해서는 스캐너를 우리 클래스로 "수입"해야 한다.  
	기본형 데이터타입들과, 그 데이터타입들을 클래스화 시킨 "포장 클래스" 외의 
	모든 클래스는 사용할 때 반드시 "수입"을 해야 한다.  
	  
	스캐너 클래스를 수입하는 방법은 다음과 같다.  
	import java.util.Scanner;  
	임포트는 import 패키지.패키지.클래스이름 의 형식으로 이루어진다.  
	*/  
	import java.util.Scanner;  
	  
	public class Ex07Scanner {  
	    public static void main(String[] arms) {  
	        Scanner scanner = new Scanner(System.in);  
	        // 위의 new Scanner(System.in) 중 System.in은 
	        // 우리가 키보드 입력을 받을 것임을 지정해준 것이다.  
			  
	        //1. 정수 입력 받기  
	        // 우리가 키보드로부터 정수를 입력 받을 때에는 
	        // Scanner 클래스 변수에서 nextInt()를 실행시키면 된다.  
	        System.out.println("정수를 입력해주세요 : ");  
	        int number = scanner.nextInt();  
			  
	        // 우리가 실수를 입력받을때에는?  
	        // nextDouble()       
	        // System.out.println("실수를 입력해주세요 : ");  
	        double myDouble = scanner.nextDouble();  
			  
	        // 우리가 String 입력을 받을 때에는?  
	        // nextLine()        
	        // 단, nextInt(), nextDouble() 등 
	        // 숫자를 압력한 후에는  
	        // 반드시 nextLine()을 두번 적어야 정상적으로 작동한다.  
	        System.out.println("이름을 입력해주세요.");  
	        String name = scanner.nextLine();  
	        name = scanner.nextLine();  
			  
	        System.out.println("정수 반환값 : " + number);  
	        System.out.println("실수 반환값 : " + myDouble);  
	        System.out.println("이름 반환값 : " + name);  
	    }  
	}
	
	
	/*
	제어문(Control Statement)  
	
	제어문이란 특정 코드들의 실행 여부 혹은 반복 여부를 제어하는 특수한 코드이다.  
	제어문에는 크게 조건문과 반복문 2가지가 있다.  
	
	조건문 : 조건이 맞으면 코드들을 실행 조건문에는 if문이 있다.  
	반복문 : 조건이 맞는동안 코드들을 실행 반복문에는 for문과 while문이 있다.  
	  
	코드 블락(Code Block)  
	코드 블락은 한개의 {} 안에 있는 모든 코드를 한개의 코드 블락이라고 한다.  
	코드 블락 안에는 1개 이상의 다른 코드 블락이 들어갈 수 있다. 
	 
	코드 블락이 중요한 이유
	1. 변수 혹은 상수의 유효 범위와 연결되어있다.  
	2. 제어문에서 실행 혹으 반복시킬 범위의 코드를 묶는다.  
	  
	변수, 상수의 유효 범위(Life Cycle)  
	변수나 상수는 해당 변수/상수가 선언된 이후부터  
	해당 변수 상수가 속한 코드 블락이 종료 될때까지가 유효 범위가 된다.  
	해당 변수/상수가 유효한 동안에는 동일한 이름의 변수/상수를 또 다시 선언할 수 없다.  
	당연하지만, 해당 변수/상수가 유효한 범위의 밖에서는 더 이상 해당 변수/상수를 
	호출할 수 없다.  
	  
	if문  
	if문은 특정 조건식(=true/false가 나올 수 있는 코드)의 결과값에 따라서 
	해당 if문의 코드 블락을 실행시킬지 말지를 결정하는 조건문이다.  
	if문은 다음과 같은 양식을 가진다.  
	
	if(조건식){  
	    조건식이 true일때 실행시킬 코드  
	}  
    */
	 public class Ex09If {  
	    public static void main(String[] args) {  
	        // 조건식 check에서 사용할 int 변수를 만들고 3으로 초기화한다.  
	  
	        int number = 3;  
	        if (number > 0) {  
	            int number2 = 30;  
	            System.out.println("0보다 큽니다.");  
	            System.out.println("number2 : " + number2);  
	        }  
	        int number2 = 20;  
	        System.out.println("number2 : " + number2);  
	        System.out.println("프로그램 종료");  
	    }  
	}
	
	
	import java.util.Scanner;  
	  
	/*  
	사용자로부터 숫자를 입력받아서  
	0보다 크면 자연수 입니다. 가 출력 되는 프로그램을 작성해보시오.  
	*/  
	public class Ex10If2 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	  
	        //1. 사용자로부터 숫자를 입력 받는다.  
	        //2. if문을 사용해 사용자의 숫자가 0보다 큰지 확인한다.  
	        //2-1. 0보다 크면 "자연수입니다." 출력한다.  
	  
	        System.out.println("숫자를 입력해주세요 : ");  
	        int number = scanner.nextInt();  
	  
	        if (number > 0) {  
	            System.out.println("자연수입니다.");  
	        }  
	    }  
	}
	
	
	package day0502;  
	  
	import java.util.Scanner;  
	/*
	if- else 구조  
	
	if else 구조는, if문의 조건식이 false가 나왔을 때  
	실행시켜야할 코드가 있을 경우  
	esle를 연경시켜서  
	실행되게 만들어준다.  
	  
	if else 구조  
	if(조건식){  
	    true일때 실행시킬 코드  
	} else {  
	    false일때 실행시킬 코드  
	}  
	*/
	 public class Ex01IfeElse {  
	    public static void main(String[] args) {  
	        int number = 3;  
	        if (number >= 0) {  
	            System.out.println("자연수입니다.");  
	        } else {  
	            System.out.println("음수입니다.");  
	        }  
	    }  
	}
	
	  
	import java.util.Scanner;  
	/*
	if - else if 구조  
	
	만약 한가지 조건식을 체크 하고 나서  
	해당 조건식이 flase일 때 다른 조건식을 체크할 경우에는  
	우리가 else if를 사용하게 된다.  
	if - else 구조와 마찬가지로 실행되는 코드 블락은 
	조건식을 만족하는 한개의 코드블락만 실행이 된다.  
	  
	if - else if의 구조는 다음과 같다.  
	if(조건식1) {  
	    조건식1이 true일때 실행할 코드  
	}else if(조건식2) {  
	    조건식2가 true일때 실행할 코드  
	}else if(조건식3) {  
	....  
	} else {  
	    위의 조건식이 모두 false일 경우 실행될 코드  
	}  
	*/
	 public class Ex02ElseIf {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	  
	        System.out.println("나이 : ");  
	        int age = scanner.nextInt();  
	  
	        if (age < 8) {  
	            System.out.println("유치원");  
	        } else if (age <= 13) {  
	            System.out.println("초등학생");  
	        } else if (age <= 19) {  
	            System.out.println("고등학생");  
	        } else {  
	            System.out.println("성인");  
	        }  
	    }  
	}
	
	```
	
- While문 / Inloop / Random / for문
	```java
	package day0502;  
	  
	import java.util.Scanner;  
	  
	public class Ex08While {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	  
	        System.out.println("숫자 : ");  
	        int number = scanner.nextInt();  
	  
	        while (number != 3) {  
	            System.out.println("3과 다릅니다.");  
	            System.out.print("숫자 : ");  
	            number = scanner.nextInt();  
	        }  
	        System.out.print("3입니다.");  
	    }  
	}
	
	
	package day0502;  
	/*
	사용자로부터 점수를 입력 받아서 A~F가 출력되는 프로그램.  
	단 사용자가 올바르지 않은 점수를 입력하면 올바른 점수가 입력될때까지 
	다시 입력을 받으시오  
	*/
	import java.util.Scanner;  
	  
	public class Ex09While2 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	  
	        System.out.println("점수를 입력해주세요.");  
	        int scours = scanner.nextInt();  
	  
	        while (scours > 100 || scours < 0) {  
	            System.out.println("올바른 점수를 입력해주세요.");  
	            scours = scanner.nextInt();  
	        }  
	  
	        if (scours >= 90) {  
	            System.out.println("A");  
	        } else if (scours >= 80) {  
	            System.out.println("B");  
	        } else if (scours >= 70) {  
	            System.out.println("C");  
	        } else if (scours >= 60) {  
	            System.out.println("D");  
	        } else {  
	            System.out.println("F");  
	        }  
	    }  
	}
	
	
	package day0502;  
	/*  
	사용자로부터 키와 몸무게를 입력 받아서 비만도를 출력하는 프로그램  
	단, 사용자가 잘못된 값을 입력할 경우 올바른 값이 입력될때까지 다시 입력을 받으시오. 
	 */  
	import java.util.Scanner;  
	  
	public class Ex09While3 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        int scours = scanner.nextInt();  
	    }  
	}
	
	
	package day0502;  
	/*
	무한 반복문(Infinite Loop)  
	  
	무한 반복문은 조건식의 결과값이 항상 true가 나와서  
	영원히 반복되는 코드를 무한 반복문이라고 한다.  
	*/
	public class Ex11InfLoop {  
	    public static void main(String[] args) {  
	// 1. 조건식의 변수의 값이 바뀌지 않아서  
	//    항상 true가 나오는 경우 int number = 3;  
	//    while (number > 0) {  
	//    System.out.println("무한 반복문 1번");  
	//    System.out.println("number의 현재 값: " + number);  
	//    }  
    // 2. 항상 true가 나오는 조건식  
	//    while (1 > 0) {  
	//    System.out.println("무한 반복문 2번");  
	//    }  
	// 3. true        
	//    while(true){  
	//    System.out.println("무한 반복문 3번");  
	//    }  
	    }  
	}
	
	
	package day0502;  
	  
	import java.util.Random;  
	import java.util.Scanner;  
	  
	public class Ex13Random {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        Random random = new Random();  
	        boolean choice = true;  
	        int cnt = 0;  
	        int number = random.nextInt(100) + 1;  
	        while (choice) {  
	            System.out.println("정답은? : ");  
	            int answer = scanner.nextInt();  
	            cnt++;  
	            if (number == answer) {  
	                System.out.println("정답입니다 ! : " + number);  
	                System.out.println("트라이 횟수 : " + cnt);  
	                choice = false;  
	            } else if (number < answer) {  
	                System.out.println("DOWN !!");  
	            } else if (number > answer) {  
	                System.out.println("UP !!");  
	            }  
	        }  
	    }  
	}  
	
	
	package day0502;  
	  
	import java.util.Scanner;  
	/*
	for 반복문  
	
	for 반복문은 whule 반복문과는 다르게  
	특정 횟수 만큼 반복을 시킬 때 좀 더 자주 사용한다.  
	for 반복문은 다음과 같은 형식을 가진다.  
	for(제어 변수의 선언과 초기화; 조건식; 코드 반복 후의 제어 변수의 변화식) {  
	    반복할 코드  
	}  
	*/
	 public class Ex15ForLoop {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        for(int i = 1; i <= 4; i++){  
	            System.out.println("i의 현재 값 : " + i);  
	        }  
	    }  
	}
	
	```
	
- 배열 / 다차원 배열  
	```java
	  package day0507;  
	  
	/*  
	배열(Array)  
	배열이란, 똑같은 종류의 데이터타입을  
	한번에 여러개씩 제어할 수 있느 데이터타입이디.  
	  
	배열의 경우, 우리가 다음과 같은 방법으로 선언과 초기화를 한다.  
	데이터타입[] 배열이름 = new 데이터타입[길이]  
	그리고, 배열 안에 각각의 요소(element)를 접근할 때에는  
	인덱스를 통해서 접근을 하게 된다.  
	인덱스란, 해당 배열에서 몇번째 요소인지를 가르키는 번호인데,  
	사람은 첫번째, 두번쨰 ....으로 세지만  
	컴퓨터는 0번째부터 세게 된다.  
	  
	따라서, 인덱스의 최대 값은 해당 배열의 길이 -1이 된다.  
	  
	만약 유효하지 않은 인덱스를 접근하게 된다면,  
	ArrayIndexOutBoundsException이라는 에러가 발생하게 된다.  
	  
	배열의 n번째 인덱스에 있는 요소를 접근할 때(=값을 저장하거나 호출할 때)에는  
	배열이름[n] 으로 접근하게 된다.  
	*/
	public class Ex01Array {  
	    public static void main(String[] args) {  
	        //int 배열 intArray를 선언하고, 길이는 4로 지정  
	        int length = 4;  
	        int[] intArray = new int[length];  	  
	        
	        //우리가 만든 배열의 0번쨰 요소에 새로운 값을 저장해보자  
	        intArray[0] = 20;  
	        
	        // 기본형 데이터타입의 배열과, 참조형 데이터타입의 다른 점은  
	        // 기본형 데이터 타입의 배열은 선언과 초기화가 되면  
	        // 모든 요소는 0으로 초기화가 된다.  
	        // 참조형 데이터타입의 배열은 null이라는 값으로 초기화가 된다.  
			  
	        // 또한 배열의 인덱스는 우리가 변수를 넣어서 특정 요소를 가리킬 수 있다.  
	        // 그렇다면, 우리가 모든 요소의 값을 출력하고 싶다면, 
	        // 어떤 방법을 쓰면 될까?  
			  
	        // 배열의 모든 인덱스를 하나 하나 찍어보자  
	        // 배열의 길이는 해당 배열의 length 라는 송성값으로 저장되어 있다.  
	        // 어떤 변수 혹은 값의 속성값 또는 메소드를 접근할 떄에는  
	        // 변수.속성 or 변수.메소드로 접근하게 된다.  
	        // 따라서, 배열의 길이를 접근할 때에는 배열이름.length 라고 
	        // 접근을 하게 된다.  
	        
	        int idx = 0;  
	        System.out.println(intArray[idx]);  
	        idx = 1;  
	        System.out.println(intArray[idx]);  
	        idx = 2;  
	        System.out.println(intArray[idx]);  
	        idx = 3;  
	        System.out.println(intArray[idx]);  
			  
			// 인덱스 오류(ArrayIndexOutBoundsException이라는)가 발생한다.  
			// 배열은 0으로 시작하고 3까지만 반복되기에 4는 
			// 유효범위가 아니기 때문이다.  
			// 그렇다면 어떻게 코드를 짜야할까?  
			// for (int i = 0; i <= intArray.length; i++) {  
			// System.out.println(intArray[i]);  
			// }  
			  
	        for (int i = 0; i <= intArray.length - 1; i++) {  
	            System.out.println(intArray[i]);  
	        }  
			  
	        for (int i = 0; i < intArray.length - 1; i++) {  
	            System.out.println(intArray[i]);  
	        }  
			  
	        // null  
	        
	        // 널이란, 참조형 데이터타입이 가질 수 있는 특수한 상황으로써, 
	        // 스택 영역에 변수에는 주소값이 부여가 되었지만,  
	        // 힙 영역에 해당 주소에는 초기화가 되지 않아 
	        // 어떠한 값을 호출하거나 메소드를 불러올 수 없는 상황이다.  
	        // null일 경우, 속성값을 호출하거나 메소드를 호출할려고 하면  
	        // 무조건 ArrayIndexOutBoundsException이 발생하게 된다.  
			  
	        // String[] stringArray를 선언하고 크기를 3으로 초기화해보자  
			  
	        String[] stringArray = new String[3];  
			  
	        // 모든 요소를 출력해보자  
			  
	        for (int i = 0; i < stringArray.length; i++) {  
	            System.out.println(stringArray[i]);  
	        }  
			  
	        //stringArray의 0번쨰 요소가 "abc"와 같은지 비교해보자  
	        stringArray[0].equals("abc");  
			  
	    }  
	}
	
	
	package day0508;  
	
	/*  
	다차원 배열  
	
	우리가 배열의 정의를 다시 한번 살펴보자면  
	"똑같은 데이터타입 여러개를 모아둔 하나의 데이터타입" 이다.  
	즉, 배열 여러개를 모아둔 배열도 우리가 만들 수 있다.  
	이렇게 배열을 모아둔 배열을 
	우리가 2차원 배열, 3차원 배열이라고 부르게 된다.  
	다차원 배열의 경우, 선언과 초기화를 할 시에 다음과 같이 한다.  
	데이터타입[][] 이름 = new 데이터타입[배열의 갯수][각 배열의 길이]  
	단, 상황에 따라서는 각 배열의 길이는 우리가 따로 지정이 가능하다.
	*/
	public class Ex01MultiArray {  
	    public static void main(String[] args) {  
	        // 각 배열의 길이는 3이고  
	        // 그러한 배열이 5개 모인  
	        // int의 2차원 배열을 만들어보자  
	        int[][] multiArray = new int[5][3];  
	  
	        // multiArray의 0번째 인덱스에 있는것은 무엇일까?  
	        System.out.println(multiArray[0]);  
	        // multiArray는 int 배열이 모여있는 배열이기 때문에  
	        // 우리가 multiArray의 0번째 인덱스를 가리키면  
	        // 0번째에 있는 int 배열이 선택되는 것이다.  
	  
	        // 만약 우리가 multiArray의 2번째 배열의  
	        // 1번 요소를 가리키고 싶다면  
	        // 다음과 같이 적어주어야 한다.  
	        System.out.println(multiArray[2][1]);  
	  
	        // 우리가 만약 2차원 배열의 내용을 전부 출력하고 싶다면  
	        // 무엇을 써야할까?  
	        // 중첩 for문  
	        // multiArray.length -> multiArray가 가지고 있는 배열의 갯수  
	        for (int i = 0; i < multiArray.length; i++) {  
	            for (int j = 0; j < multiArray[i].length; j++) {  
	                //multiArray[i].length -> multiArray의 i번째 배열의 길이  
	                //multiArray[i][j] -> multiArray의 i번째 배열의  
	                // j번째 요소  
	                System.out.printf
	                ("multiArray[%d][%d]: %d\n", i, j, multiArray[i][j]);  
	            }  
	        }  
	        // 가변형 배열  
	        // 가변형 배열이란, 2차원 이상의 배열에서  
	        // 몇개가 모여있는 배열인지를 지정하지만  
	        // 각 배열의 길이는 사용을 할 때 따로 지정을 해서  
	        // 길이가 다른 배열을 모아두는 방법이다.  
	        
	        // int 배열이 4개 모여있는 2차원 배열 multiArray
	        // multiArray = new int[4][];  
			  
	        // 이 상황에서 multiArray[0]의 값은?  
	        System.out.println(multiArray[0]);  
			  
	        // 즉, 우리가 처음에 모여있는 각 배열의 길이까지 초기화한 경우,  
	        // ex) multiArray = new int[5][3]        
	        // 하나하나의 배열은 전부다 new int[3] 이 실행되서  
	        // null이 아닌 상태이지만,  
	        // 우리가 길이를 따로 지정하지 않았을 경우에는  
	        // 사용전에 반드시 초기화를 한번씩 더 해주어야 한다.  
	        // multiArray의 0번째 배열은 크기가 3인 배열로 초기화해보자  
	        multiArray[0] = new int[3];  
	        // 1번째 배열은 크기가 7인 배열로 초기화해보자  
	        multiArray[1] = new int[7];  
	        // 2개의 길이를 출력해보자  
	        System.out.println(multiArray[0].length);  
	        System.out.println(multiArray[1].length);  
			  
	        for (int i = 0; i < 4; i++) {  
	            for (int j = 0; j < 9; j++) {  
	                for (int k = 1; k < 7; k++) {  
	                    // k for문 마지막  
	                }  
	                // j for문 마지막  
	            }  
	            // i for문 마지막  
	        }  
	    }  
	}
	
	```
	
- Method / ScannerUtil / 호출 / 전역 변수 / 구조체
	```java
	package day0508;  
	// 메소드(Method)  
	// 메소드란, 우리가 반복적으로 실행되는 코드를  
	// 좀더 간단하게 실행시키기 위하여  
	// 코드를 모아서 하나의 명령어로 묶는 것이다.  
	// 이렇게 하나로 묶여 있게 된다면 우리가 해당 코드들을  
	// 처음부터 끝까지 다시 적어줄 필요 없이 해당 메소드의 이름만으로  
	// 그 코드들을 실행시킬 수 있게 된다.  
	  
	// 메소드는 다음과 같은 형식을 가지게 된다.  
	// public static 리턴타입 메소드이름(파라미터) {  
	//    해당 메소드가 실행시킬 코드들  
	// }  
	  
	// public, static: 일단은 지금 단계에서는 무조건 써주기  
	// 리턴 타입: 해당 메소드를 실행시킨 곳으로 보내줄 값의 데이터타입.  
	//      만약 아무런 값도 보내지 않는 다면 void 라고 적어주게 된다.  
	//      리턴 타입이 존재할 경우, 해당 메소드는 반드시 return 이라는  
	//      명령어를 통해서, 해당 타입의 값을 보내주는 코드가 있어야 한다.  
	// 메소드 이름: 소문자로 시작하고 낙타등 표기법을 사용하는 동사  
	// 파라미터: 해당 메소드를 실행시킬 때 혹시라도 외부에서 어떠한 값이 필요할 경우  
	//          우리가 파라미터에 변수를 선언하듯이 적어주게 된다.  
	//          그러면 해당 메소드는 그 외부의 값을 변수로 사용할 수 있다.  
	  
	// 메소드 오버로딩(Overloading)  
	// 메소드 오버로딩이란, 어떤 특정 목적을 가진 메소드들을 만들어야 할 경우  
	// 매번 이름을 다르게 만들어 주는 대신, 이름을 통일 시켜서  
	// 알아보기 쉽게 만들어주는 방법이다.  
	// 단, 한가지 주의할 점은 파라미터의 타입이 나오는 순서가 반드시 달라야 한다.  
	public class Ex03Method {  
	    public static void main(String[] args) {  
	        // 내가 int 값을 보내면  
	        // 화면에 "사용자가 보낸 int 값" 이라고  
	        // 표시해주는 메소드를 호출해보자  
			  
	        int a = 10;  
	        printUserNumber(a);  
	        int myNumber = 3000;  
	        printUserNumber(myNumber);  
			  
	        printUserNumber(450);  
			  
	        // 사용자가 호출하면  
	        // 80을 돌려주는  
	        // 메소드  
	        int value = return80();  
	        System.out.println("메소드가 보내준 값: " + value);  
	        System.out.println(return80()); 
	        // = 화면에 return80()의 결과인 80을 출력시켜라  
			  
	        // 사용자가 2개의 int 값을 보내주면  
	        // 해당 값들의 산술연산자의 결과값을 화면에 출력하고  
	        // 둘 중 더 큰 값을 돌려주는 메소드  
	        int result = compare(a, myNumber);  
	        System.out.println("result: " + result);  
	    }  
		  
	    // int a = myNumber의 현재 값;  
	    // int a = 450;    
	    // public static void printUserNumber(int a) { }
	        System.out.println("사용자가 보낸 값: " + a);  
	    }  
		  
	    public static int return80() {  
	        return 80;  
	    }  
		  
	    public static int compare(int a, int b) {  
	        System.out.printf("%d + %d = %d\n", a, b, a + b);  
	        System.out.printf("%d - %d = %d\n", a, b, a - b);  
	        System.out.printf("%d * %d = %d\n", a, b, a * b);  
	        System.out.printf("%d / %d = %d\n", a, b, a / b);  
	        System.out.printf("%d %% %d = %d\n", a, b, a % b);  
			  
	        if (a > b) {  
	            return a;  
	        } else {  
	            return b;  
	        }  
	    }  
	}
	
	
	package day0508;  
	  
	import java.util.Scanner;  
	  
	import util.ScannerUtil;  
	  
	// 우리가 입력할 때 도움을 줄  
	// ScannerUtil을 직접 체험해볼 클래스  
	public class Ex04ScannerUtil {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        // ScannerUtil을 안쓸 경우  
	        // 사용자로부터 숫자 3개를 입력받아보자  
	        System.out.println("0~10 사이의 숫자를 입력해주세요.");  
	        System.out.print("> ");  
	        int number = scanner.nextInt();  
	        while (!(number >= 0 && number <= 10)) {  
	            System.out.println("잘못 입력하셨습니다.");  
	            System.out.println("0~10 사이의 숫자를 입력해주세요.");  
	            System.out.print("> ");  
	            number = scanner.nextInt();  
	        }  
	        System.out.println("사용자가 입력한 숫자: " + number);  
			  
	        // ScannerUtil을 쓸 경우  
	        // 단, 외부 패키지의 있는 클래스를 호출할려면, 
	        // 반드시 import 해주어야 한다.  
	        number = ScannerUtil.nextInt
	        (scanner, "0~10사이의 숫자를 입력해주세요.", 0, 10);  
	    }  
	}
	
	
	package day0510;  
	// 값에 의한 호출과 참조에 의한 호출  
	  
	// 자바에서 파라미터로 값을 보내줄때  
	// 2가지의 호출이 일어난다.  
	// 값에 의한 호출: 기본형 데이터타입일 경우, 
	// 해당 변수 혹은 값이 복사되서 보내진다.  
	// 즉, 보내진 값은 복사본이므로, 다른 메소드에서 해당 값을 변경을 하더라도  
	// 원본에는 변경이 가해지지 않는다.  
	// 참조에 의한 호출: 참조형 데이터타입일 경우, 주소 값이 보내진다. 
	// 주소값이 보내졌기 때문에, 파라미터로 받은 메소드와 원본 모두 똑같은  
	// 힙 영역의 공간을 보게 된다.  
	// 따라서, 다른 메소드가 변경을 가하면, 힙 영역에 공간에 변경이 가해지고  
	// 원본도 마찬가지로 변경이 된다.  
	// 단, 해당 메소드가 다른 주소값을 부여하게 되면 변경이 되지 않는다.  
	// new 키워드: 해당 참조형 변수에 새로운 주소값을 보여한다.  
	public class Ex01Call {  
	    public static void main(String[] args) {  
	        int a = 10;  
	        System.out.println("callValue 전 값: " + a);  
	        callValue(a);  
	        System.out.println("callValue 후 값: " + a);  
			  
	        int[] array = new int[4];  
	        System.out.println("callRef 전 array[0]: " + array[0]);  
	        callRef(array);  
	        System.out.println("callRef 후 array[0]: " + array[0]);  
			
	        array[0] = 100;  
	        alloc(array);  
	        System.out.println("alloc 후 array[0]: " + array[0]);  
	    }  
		  
	    public static void callValue(int value) {  
		  
	        value++;  
	        System.out.println("callValue에서 value의 값: " + value);  
	    }  
		  
	    public static void callRef(int[] array) {  
	        array[0] = 20;  
	        System.out.println("array[0]: " + array[0]);  
	    }  
		  
	    public static void alloc(int[] array) {  
	        array = new int[5];  
	        array[0] = 20;  
	        System.out.println("alloc.array[0]: " + array[0]);  
	    }  
	}
	
	
	/*  
	전역 변수(Global Variable)  
	전역 변수란, 변수의 선언위치가 클래스의 최상단에 이루어져서  
	모든 메소드가 공통적으로 접근 가능한 변수를 전역 변수라고 한다.  
	  
	전역 변수 장점 : 모든 메소드가 사용 가능하다.  
	전역 변수 단점 : 모든 메소드가 사용 가능하다.  
	  
	따라서 현재 프로그래밍에서는 전역 변수의 사용을 매우 비추천한다.  
	전역 변수의 경우, 우리가 정확하게 값을 트랙킹하기 어려워지기 떄문이다.  
	  
	그렇다면 전역 상수는...?  
	상수는 한번 값이 저장되면 더 이상 변경이 안되므로  
	다른 메소드가 사용한다고 해서 값을 변경할 수는 없다.  
	따라서, 여러 메소드가 공통적으로 사용해야할 상수일 경우,  
	전역 상수를 사용하는 것이 추천된다.   
	*/
	 public class Ex02Global {  
	    public static int number;  
	    public static final int SIZE = 4;  
	  
	    public static void main(String[] args) {  
	        number = 20;  
	        System.out.println("number의 현재 값 : " + number);  
	        increase();  
	        increase();  
	        increase();  
	        discrease();  
	        System.out.println("increase() 후 number : " + number);  
	    }  
	  
	    public static void increase() {  
	        number++;  
	    }  
	  
	    public static void discrease() {  
	        number--;  
	    }  
	}
	
	
	package day0513;  
	/*  
	구조체(Struct)
	
	구조체란 여러가지의 데이터타입을 합쳐서 한가지의 데이터타입으로 묶는 
	특수한 자료형을 뜻한다.  
	단, 구조체는 C, C++에서만 사용 가능하고 자바에서는 사용이 불가능하다.  
	하지만 우리가 구조체와 유사한 것을 만들어낼 수 있다.  
	 */  
	import types.Student;  
	  
	public class Ex01Struct {  
	    public static void main(String[] args) {  
	        // Student 변수를 선언해보자  
	        Student kim = new Student();  
	  
	        // Student 변수 kim 안에 값을 저장해보자  
	        // 우리가 클래스형 변수 안에 값을 저장할 때에는  
	        // 변수이름.종류 = 값;으로 저장하게 된다.  
	        kim.id = 1;  
	        kim.name = "김철수";  
	        kim.korean = 70;  
	        kim.english = 86;  
	        kim.math = 98;  
	        // 저장된 값을 불러올떄도 마찬가지  
	        System.out.printf("번호 : %02d번 이름 : %s\n", kim.id, kim.name);  
	        Student lee = new Student();  
	        lee.id = 2;  
	        lee.name = "이영희";  
	        lee.korean = 88;  
	        lee.english = 85;  
	        lee.math = 78; 
	        System.out.printf("번호 : %02d번 이름 : %s\n", lee.id, lee.name);  
	    }  
	}
	
	
	```
	
- 객체지향 프로그래밍의 5가지 원칙
	``` java
	package day0514;  
	/*  
	객체지향 프로그래밍의 5원칙  
	객체지향 프로그래밍에서는 5가지 원칙이 있는데  
	해당 원칙을 잘 지켜야 여러분들이 프로그래밍을 만들때 
	진정한 객체지향 프로그래밍을 한다고 할 수 있다.  
	하지만 여러분들이 전부다 지키는 것은 훗날의 일이고  
	지금은 S를 잘지키는 것을 목표로 해야한다.  
	  
	S : 단일 책임 원칙(Single Responsibility Principle)  
	    클래스는 한번에 한가지만 책임을 지어야 한다.  
	    만약, 해당 클래스가 데이터를 필드화 시켜서 관리할 것이면 그것만 해야하고  
	    화면 출력을 담당할거면 화면 출력을 담당해야 한다.  
	  
	O : 개방 패쇄 원칙(Open - Closed Principle)  
	    모든 클래스는 확장에는 열려 있고, 변경에는 닫혀 있어야 한다.  
	    즉, 우리가 어떠한 기능을 추가할 때에는 쉽지만,  
	    내부의 변경이 다른 클래스에 영향을 미쳐선 안된다.  
	  
	L : 리스코프 대체 원칙(Liskov Subsititution Principle)  
	    모든 부모 클래스의 객체를 자식 클래스의 객체로 교체하더라도  
	    프로그램에는 문제가 없어야 한다.  
	  
	I : 인터페이스 분리 원칙(Interface Segregation Principle)  
	    프로그램은, 자신이 사용하지 않는 메서드를 의존해선 안된다.  
	  
	  
	D : 의존 역전 원칙(Dependency Inversion Principle)  
	    A 클래스가 B 클래스에 의존적이더라고 해도  
	    A 클래스는 B 클래스의 메소드가 어떻게 작동하는지는 알 필요가 없다.  
	 */  
	public class Ex05SOLID {  
	}
	```
	
- 접근제한자 / 캡슐화
	```java
	package day0514;  
	  
	/*  
	  
	접근제한자(Access Modifier)와 캡슐화(Capsulization)  
	
	접근 제한자  
	
	접근 제한자란, 해당 클래스의 필드 혹은 메소드를  
	외부 클래스가 접근 가능한 범위를 설정해 주는 키워드이다.  
	  
	public : 외부 패키지의 외부 클래스 누구나 접근 가능하다.  
	protected : 같은 패키지의 다른 클래스는 접근 가능하지만 
				다른 패키지일 경우, 해당 클래스의 자식 클래스 일 때에만 
				접근 가능하다.    
	defult : 우리가 아무런 접근 제한자를 적어주지 않을 때에는  
	         같은 패키지의 다른 클래스들까지만 접근이 가능하다.  
	         같은 패키지의 클래스들만 접근 가능하기 때문에 
	         패키지 접근 제한자라고도 부른다.  
	private : 자기 자신이 아닌 다른 클래스들은 모두 다 접근할 수 없다.  
	  
	캡술화  
	
	캡슐화란, 우리가 만든 클래스의 필드를  
	외부에서 직접적으로 접근하지 못하게 막고  
	메소드의 경우, 외부에서 사용하지 않을 메소드이면  
	접근을 막게 만드는 방법이다.  
	캡슐화를 하는 이유는, 우리가 객체 지향적 관점에서  
	외부가 우리 클래스의 필드 혹은 메소드를 직접적으로 값을 넣거나 호출하지 말고  
	객체 그 자체를 소화시키도록 만들기 위함이다.  
	  
	캡슐화의 기본 방법  
	1. 필드는 모두다 private   
	   단, private으로 지정된 필드의 경우 
	   우리가 직접적으로 접근할 수 없기 때문에  
	   값을 저장하는 setter 메소드와 저장된 값을 
	   불러오는 getter 메소드를 통하여  
	   간접적으로 접근하게 된다.  
	2. 외부에서 쓰는 메소드만 public, 
	   그 외는 모두다 private  
	   
	getter 메소드 만드는 방법  
	   public 필드타입 get필드이름() {  
	    return 필드이름;  
	 }  
	 
	setter 메소드 만드는 방법  
	   public void set필드이름(필드타입 필드이름) {  
	    this.필드이름 = 필드이름;  
	}  
	  
	*/
	 public class Ex02Capsule {  
	  
	}
	
	
	package day0514;  
  
	import types.Animal;  
	import types.Cat;  
	import types.Dog;  
	import types.IAnimal;  
	  
	/*  
	상속(Ineritance)  
	
	아침 드라마나 실제 상황에서 부모가 자식이 상속을 해주는 이유:  
	자식이 부모가 가진 재산을 그대로 쓰게 할려고  
	  
	프로그래밍에서 상속을 하는 이유:  
	똑같다.  
	-> 부모 클래스가 가진 필드 혹은 메소드를 자식 클래스가 그대로 쓰게 할려고  
	  
	클래스 상속을 하는 방법  
	부모 클래스를 만들고  
	자식 클래스에서 상속을 할때  
	public class 자식 클래스 이름 extents 부모 클래스 이름이라고 
	적어주면 상속이 이뤄진다.  
	  
	단, 인터페이스 상속은 부모 클래스의 코드를 그대로 쓰기 위함이 아니라  
	우리가 다형성이라는 성격을 부여하기 위한이기 때문에, 지금은 다루지 않는다.  
	  
	다형성(Polymorphism)  
	다양한 형태를 가지는 성질  
	다형성은 우리가 부모 클래스 객체가 들어갈 자리에  
	자식 클래스가 그대로 들어갈 수 있는 것을 뜻한다.  
	예를 들어서  
	equals 메소드의 경우 파라미터에 java.lang.Object가 있기 때문에  
	해당 Object 클래스를 상속 받는 모든 클래스 객체가 파라미터로 들어갈 수 있다.  
	  
	또한, 부모 클래스 객체를 자식 클래스의 생성자로 초기화하는 것도  
	이러한 폴리몰피즘 덕분에 가능한 것이다.  
	  
	*/
	public class Ex03Inherit {  
	    public static void main(String[] args) {  
	        Animal a = new Animal();  
	        a.info();  
	        a.move();  
	        a.makeSound();  
	  
	        Dog d = new Dog();  
	        d.info();  
	        d.move();  
	        d.makeSound();  
	  
	        Animal animal = new Dog();  
	        animal.makeSound();  
	  
	        System.out.println("=========================");  
	        System.out.println("인터페이스 상속");  
	        System.out.println("=========================");  
	        IAnimal randomAnimal = new Cat(); //new Cat(); or new Dog();  
	        randomAnimal.info();  
	        randomAnimal.move();  
	        randomAnimal.makeSound();  
	    }  
	}
	
	
	package day0514;  
	  
	import types.Hobby;  
	import types.Writer;  
	  
	/*  
	의존성 주입(Dependency Injection)
	
	의존성 주입이란, 우리의 클래스가 다른 클래스에 의존적인 관계일 경우,  
	해당 의존성을 약화시키기 위해 사용되는 방법이다.  
	  
	예를 들어 우리가 A라는 클래스가 있고  
	해당 클래스는 B라는 클래스가 있어야 정상적으로 동작하는 클래스라고 가정해보자  
	그래서 우리 A 클래스가 내부적으로 B 클래스 타입의 필드가 있고 모든 메소드는  
	  
	해당 클래스의 메소드를 다양하게 활용한다고 가정해보자  
	이러한 경우, A 클래스는 B 클래스에 매우 의존적인 관계가 맺어지게 된다.  
	  
	그러던 어느날, B 클래스가 대규모 패치를 하게 되어  
	모든 메소드의 내용이 바뀌었다고 가정해보자.  
	그렇다면 A 클래스의 운명은?  
	똑같이 A 클래스도 똑같이 대규모 패치를 해주어야 하는 경우가 발생하게 된다.  
	  
	이러한 의존성을 줄이기 위하여 여러 방법이 시도 되었으나  
	가장 좋은 방법은 다음과 같은 방법으로 해소를 하는 것이다.  
	  
	의존성은 2가지 방법으로 줄일 수가 있는데  
	2가지 방법 모두 B 라는 원본 클래스를 A가 직접 초기화를 하는 것이 아니라  
	외부에서 B라는 클래스 객체를 만들어서 초기화하고  
	A에 해당 객체를 전달시켜서 사용하게 하는 방법이 된다.  
	방법 1 : setter를 통한 의존성 주입  
	방법 2 : 생성자를 통한 의존성 주입  
	*/
	public class Ex04DI {  
	    public static void main(String[] args) {  
	        Writer writer = new Writer(3, "아가사 크리스티");  
	        Hobby hobby = new Hobby(writer);  
	        hobby.method1();  
	        hobby.method2();  
	        hobby.method3();  
	    }  
	}
	```
	
- static
``` java
	- 단 하나만 있는 것을 의미한다.
	- 예시
		- 영화관의 스크린
		- 학원 안에 강의실
	- @Repository, @Controller, @Service를 걸면 싱글톤이 된다.
	- 
```
	
- 
``` java
	
```
	
- 
``` java
	
```
  
##### GradeBook
- version 1 : Scanner, printf , sysout을 활용한 기초적인 입출력 
	```java
	package day0501;  
	/*
	사용자로부터 번호, 이름, 국어, 영어, 수학 점수 순으로 입력을 받아서  
	다음과 같은 형식으로 출력되는 프로그램을 작성하시오  
	출력형식 :번호 : 0#번 이름 : ###국어 : 0##점 영어 : 0##점 수학 : 0##점  
	총점 : 0##점 평균 : 0##.##점  
	4시 55분까지  
	*/
	import java.util.Scanner;  
	  
	public class Ex08Gradebook {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);    
	     // 과목의 갯수를 저장할 상수  
	        final int SUBJECT_SIZE = 3;  	
	          
		    System.out.println("번호를 입력하세요.");  
		    int number = scanner.nextInt();    
			System.out.println("이름을 입력하세요.");  
	        scanner.nextLine();  
		    String name = scanner.nextLine(); 
			System.out.println("국어 점수를 입력하세요.");  
		    int korean = scanner.nextInt();  
		    System.out.println("영어 점수를 입력하세요.");  
		    int english = scanner.nextInt();  
		    System.out.println("수학 점수를 입력하세요.");  
		    int math = scanner.nextInt();  
		    int sum = korean+english+math;  
		    double average = (double) sum / (double) SUBJECT_SIZE;  
		  
		    System.out.printf("번호 : %02d번  이름 : %s\n",number,name);  
		    System.out.printf
		    ("국어 : %03d점 영어 : %03d점 수학 : %03d점\n", 
		    korean, english, math);  
		    System.out.printf("총점 : %03d점 평균 : %06.2f점\n", 
		    sum, average);  
		    }  
	}
	```
	
- version 2 : 
	```java
	package day0509;  
	// ArrayUtil, ScannerUtil을 사용한  
	// 학생 관리 프로그램  
	  
	import java.util.Scanner;  
	import util.ScannerUtil;  
	import util.ArrayUtil;  
	  
	public class Ex02GradeBook {  
	    public static void main(String[] args) {  
	        // 입력을 처리할 Scanner 클래스 변수  
	        Scanner scanner = new Scanner(System.in);  
			  
	        // 학생 번호 배열  
	        int[] idArray = new int[0];  
			  
	        // 학생 이름 배열  
	        String[] nameArray = new String[0];  
			  
	        // 국어 점수 배열  
	        int[] koreanArray = new int[0];  
			  
	        // 영어 점수 배열  
	        int[] englishArray = new int[0];  
			  
	        // 수학 점수 배열  
	        int[] mathArray = new int[0];  
			  
	        // 입력 가능한 최소 점수  
	        final int MIN_SCORE = 0;  
			  
	        // 입력 가능한 최대 점수  
	        final int MAX_SCORE = 100;  
	  
	        while (true) {  
	            String menuMessage = "1. 입력 2. 출력 3. 종료";  
	            int userChoice = ScannerUtil.nextInt(scanner, menuMessage);  
	            if (userChoice == 1) {  
	                // 입력 코드 구현  
	                // 번호 입력  받기  
	                String message = "학생의 번호를 입력해주세요.";  
	                int id = ScannerUtil.nextInt(scanner, message);  
					  
	                // 이름 입력 받기  
	                message = "학생의 이름을 입력해주세요.";  
		            String name = ScannerUtil.nextLine(scanner, message);  
					  
	                // 국어 점수 입력 받기  
	                message = "학생의 국어 점수를 입력해주세요.";  
	                int korean = ScannerUtil.nextInt
	                (scanner, message, MIN_SCORE, MAX_SCORE);  
					  
	                // 영어 점수 입력 받기  
	                message = "학생의 영어 점수를 입력해주세요.";  
	                int english = ScannerUtil.nextInt
	                (scanner, message, MIN_SCORE, MAX_SCORE);  
					  
	                // 수학 점수 입력 받기  
	                message = "학생의 수학 점수를 입력해주세요.";  
	                int math = ScannerUtil.nextInt
	                (scanner, message, MIN_SCORE, MAX_SCORE);  
					  
	                // 입력 받은 정보들을 배열에 추가해준다.  
	                // 번호 추가  
	                idArray = ArrayUtil.add(idArray, id);  
	                // 이름 추가  
	                nameArray = ArrayUtil.add(nameArray, name);  
	                // 국어 추가  
	                koreanArray = ArrayUtil.add(koreanArray, korean);  
	                // 영어 추가  
	                englishArray = ArrayUtil.add(englishArray, english);  
	                // 수학 추가  
	                mathArray = ArrayUtil.add(mathArray, math);  
	  
	            } else if (userChoice == 2) {  
	                // 출력 코드 구현  
	                for (int i = 0; i < ArrayUtil.size(idArray); i++) {  
	                    int id = ArrayUtil.get(idArray, i);  
	                    String name = ArrayUtil.get(nameArray, i);  
	                    int korean = ArrayUtil.get(koreanArray, i);  
	                    int english = ArrayUtil.get(englishArray, i);  
	                    int math = ArrayUtil.get(mathArray, i);  
	                    int sum = korean + english + math;  
	                    double average = (double) sum / 3;  
	                    System.out.printf
	                    ("번호: %2d번 이름: %s\n", id, name);  
	                    System.out.printf
	                    ("국어: %03d점 영어: %03d점 수학: %03d점\n", 
	                    korean, english, math);  
	                    System.out.printf
	                    ("총점: %03d점 평균: %06.2f점\n", sum, average);  
	                }  
	            } else if (userChoice == 3) {  
	                System.out.println("사용해주셔서 감사합니다.");  
	                break;  
	            }  
	        }  
	    }  
	}
	```
	
- version 3 : 
	``` java
	package day0510;  
	  
	import util.ArrayUtil;  
	import z_practice.ScannerUtil;  
	import java.util.Scanner;  
	  
	/*  
	전역 변수와 상수를 사용한  
	학생 성적 관리 프로그램  
	*/
	 public class Ex03GradeBook01 {  
		  
	    // 각종 정보를 담을 배열  
	    public static int[] idArray = new int[0];  
	    public static String[] nameArray = new String[0];  
	    public static int[] koreanArray = new int[0];  
	    public static int[] englishArray = new int[0];  
	    public static int[] mathArray = new int[0];  
	    public static int nextId = 1;  
		  
	    // 전역 상수  
	    public static final Scanner SCANNER = new Scanner(System.in);  
	    public static final int SCORE_MIN = 0;  
	    public static final int SCORE_MAX = 100;  
	    public static final int SUBJECT_SIZE = 3;  
		  
	    public static void main(String[] args) {  
	        showMenu();  
	    }  
		  
	    // 메뉴를 보여주는 메소드  
	    public static void showMenu() {  
	        String message = "1.학생 입력 2.전체 출력 3.종료";  
	        while (true) {  
	            int userChoice = ScannerUtil.nextInt(SCANNER, message);  
	            if (userChoice == 1) {  
	                // 학생 입력 메소드 호출  
	                insert();  
	            } else if (userChoice == 2) {  
	                printList();  
	                // 전체 출력 메소드 호출  
	            } else if (userChoice == 3) {  
	                System.out.println("이용해주셔서 감사합니다.");  
	            }  
	        }  
	    }  
		  
	    public static void insert() {  
	        String message;  
	        idArray = ArrayUtil.add(idArray, nextId++);  
	        message = "학생 이름을 입력 : ";  
	        nameArray = ArrayUtil.add
	        (nameArray, util.ScannerUtil.nextLine(SCANNER, message));  
	        message = "국어 점수를 입력 : ";  
	        koreanArray = ArrayUtil.add
	        (koreanArray, util.ScannerUtil.nextInt(SCANNER, message));  
	        message = "영어 점수를 입력 : ";  
	        englishArray = ArrayUtil.add
	        (englishArray, util.ScannerUtil.nextInt(SCANNER, message));  
	        message = "수학 점수를 입력 : ";  
	        mathArray = ArrayUtil.add(mathArray, 
	        util.ScannerUtil.nextInt(SCANNER, message));  
	    }  
		  
	    public static void printList() {  
	        for (int i = 0; i < idArray.length; i++) {  
	            String name = ArrayUtil.get(nameArray, i);  
	            int id = ArrayUtil.get(idArray, i);  
				  
	            System.out.printf("%d. %s\n", id, name);  
	        }  
	        String message = 
	        "상세보기할 학생의 번호나 뒤로 가실려면 0을 입력해주세요";  
	        int userChoice = ScannerUtil.nextInt(SCANNER, message);  
	        while (!validate(userChoice)) {  
	            System.out.println("잘못 입력하셨습니다.");  
	            userChoice = ScannerUtil.nextInt(SCANNER, message);  
	        }  
			  
	        if (userChoice != 0) {  
	            // 학생 개별 보기 메소드 호출  
	            printOne(userChoice);  
	        }  
	    }  
	    // 목록 보기에서 사용자가 입력한 값이 유효한 값인지 체크하여  
	    // 유효하면 true, 유효하지 않으면 false가 리턴되는 메소드  
	    public static boolean validate(int value) {  
	        if (value == 0) {  
	            return true;  
	        }  
	        return ArrayUtil.contains(idArray, value);  
	    }  
		  
	    private static void printOne(int id) {  
	        int index = ArrayUtil.indexOf(idArray, id);  
	        String name = ArrayUtil.get(nameArray, index);  
	        int korean = ArrayUtil.get(koreanArray, index);  
	        int english = ArrayUtil.get(englishArray, index);  
	        int math = ArrayUtil.get(mathArray, index);  
			  
	        int sum = korean + english + math;  
	        double average = (double) sum / SUBJECT_SIZE;  
			      
		System.out.println("==============================================");  
	    System.out.printf("번호: %2d번 이름: %s\n", id, name);  
	    System.out.printf
	    ("국어: %03d점 영어: %03d점 수학: %03d점\n", korean, english, math);  
	    System.out.printf("총점: %03d점 평균: %06.2f점\n", sum, average);        
		System.out.println("==============================================");  
	    String message = "1.수정 2.삭제 3.뒤로";  
	    int userChoice = util.ScannerUtil.nextInt(SCANNER, message, 1, 3);  
	    if (userChoice == 1) {  
	        // 학생 수정 메소드 실행  
	        update(id);  
	        printOne(id);  
	        } else if (userChoice == 2) {  
	            delete(id);  
	            // 학생 삭제 메소드 실행  
	        } else if (userChoice == 3) {  
	            // 학생 리스트를 보는 것을 다시 실행시켜준다.  
	            printList();  
	        }  
	    }  
		  
	    public static void update(int id) {  
	        int index = ArrayUtil.indexOf(idArray, id);  
	        String message;  
			  
	        message = "학생의 이름을 다시 입력해주세요.";  
	        String name = ScannerUtil.nextLine(SCANNER, message);  
	        message = "학생의 국어 점수를 다시 입력해주세요.";  
	        int korean = ScannerUtil.nextInt
	        (SCANNER, message, SCORE_MIN, SCORE_MAX);  
	        message = "학생의 영어 점수를 다시 입력해주세요.";  
	        int english = ScannerUtil.nextInt
	        (SCANNER, message, SCORE_MIN, SCORE_MAX);	  
	        message = "학생의 수학 점수를 다시 입력해주세요.";  
	        int math = ScannerUtil.nextInt
	        (SCANNER, message, SCORE_MIN, SCORE_MAX);  
	    }  
	  
	    public static void delete(int id) {  
	        int index = ArrayUtil.indexOf(idArray, id);  
	        String message = "정말로 삭제하시겠습니까? Y/N";  
	        String ansewer = util.ScannerUtil.nextLine(SCANNER, message);  
	        // 스트링 값 비교를 할 때 대소문자 없이 같으면 true, 
	        // 다르면 false를 확인하고 싶다면?  
	        // equalsIgnoreCase 
	        // if (ansewer.equalsIgnoreCase("Y")) {
	        // 사용자가 동의했으므로 삭제  
	        idArray = ArrayUtil.remove(idArray, index);  
	        nameArray = ArrayUtil.remove(nameArray, index);  
	        koreanArray = ArrayUtil.remove(koreanArray, index);  
	        englishArray = ArrayUtil.remove(englishArray, index);  
	        mathArray = ArrayUtil.remove(mathArray, index);  
	        printList();  
	        } else {  
		    // 상세보기를 다시 실행시켜준다.  
	        printOne(id);  
	        }  
	    } 
	    // 클래스 마지막 줄  
	}
	```

##### Lotto
	
- version 1 : Random , for문, 배열 , printf
	```java
	package day0507;  
	  
	import java.util.Random;  
	import java.util.Scanner;  
	// 로또 번호 제작기 ver 0.1// 1~45까지 랜덤한 숫자를 배열에 저장하고 
	// 출력하는 프로그램을 작성하시오  
	// 10시 40분까지  
	public class Ex02Lotto01 {  
	    public static void main(String[] args) {  
	        Random random = new Random();  
	        int[] numbers = new int[6];    
	        //for문을 사용하여, 랜덤한 숫자 1~45를 배열에 6개 저장한다.  
	        for (int i = 0; i < numbers.length; i++) {  
	            numbers[i] = random.nextInt(45) + 1;  
	        }  
	        for (int i = 0; i < numbers.length; i++) {  
	            System.out.printf("numbers[%d]: %d\n", i, numbers[i]);  
	        }  
	    }  
	}
	```
	
- version 2 : Random, for문, 배열, printf
	```java
	package day0507;  
	// 로또 번호 제작기 ver 0.5// 중복되지 않는 랜덤한 숫자 6개를 뽑아서  
	// 배열에 저장하는 프로그램  
	  
	// 중복이란?  
	// 같은 값이 여러번 나오는 것  
	// = 어떠한 숫자가 다른 인덱스에서 나오는 경우  
	  
	import java.util.Random;  
	  
	public class Ex03Lotto02 {  
	    public static void main(String[] args) {  
	        Random random = new Random();  
	        int[] numbers = new int[6];  
	  
	        // for문의 경우, 내부의 초기화식이나, 변경식 같은 것을  
	        // 공백을 넣어줄 수도 있다.  
	        // 단 이때에는, 무한 루프가 되지 않도록 break 또는 변화식을  
	        // 반드시 포함시켜주는 것이 중요하다.  
	  
	        // i for문을 만들되, 변화식은 비어있는 i for문을 만들어주자  
	        for (int i = 0; i < numbers.length; ) {  
	            // 랜덤한 숫자를 뽑아서 int 변수 temp에 저장해주자  
	            int temp = random.nextInt(45) + 1;  
	  
	            // 중복을 찾을때만 true가 저장될 boolean 변수  
	            boolean isDuplicated = false;  
	  
	            // j for문을 만들어서, numbers의 모든 요소와  
	            // temp를 비교해보자  
	            for (int j = 0; j < numbers.length; j++) {  
	                //만약,  numbers[j]가 temp와 같으면  
	                //isDuplicated의 값을 true로 변경해주자  
	                if (numbers[j] == temp) {  
	                    isDuplicated = true;  
	                }  
	            }  
	  
	            if (!isDuplicated) {  
	                // temp의 값이 중복이 아니므로  
	                // numbers[i]에 값을 저장하고  
	                // i를 1 증가 시킨다.  
	                numbers[i++] = temp;  
	            }  
	        }  
	  
	        // 결과값 출력  
	        for (int i = 0; i < numbers.length; i++) {  
	            System.out.printf("numbers[%d]: %d\n", i, numbers[i]);  
	        }  
	    }  
	}
	```
	
- version 3 : Random, for문, 이중 for문, 배열, printf, 
	```java
	  package day0507;  
	// 로또 번호 제작기 ver 1.0// 중복되지 않는 랜덤한 숫자 6개를 정렬하여 
	// 보여주는 프로그램  
	  
	import java.util.Random;  
	  
	public class Ex04Lotto03 {  
	    public static void main(String[] args) {  
	        Random random = new Random();  
	        int[] numbers = new int[6];  
			  
	        // 중복되지 않는 숫자 6개 뽑기  
	        for (int i = 0; i < numbers.length; ) {  
	            int temp = random.nextInt(45) + 1;  
	  
	            boolean isDuplicated = false;  
	            for (int j = 0; j < numbers.length; j++) {  
	                if (numbers[j] == temp) {  
	                    isDuplicated = true;  
	                }  
	            }  
	            if (!isDuplicated) {  
	                numbers[i++] = temp;  
	            }  
	        }  
	        // 결과값 출력  
	        for (int i = 0; i < numbers.length; i++) {  
	            System.out.printf("numbers 1[%d]: %d\n", i, numbers[i]);  
	        }  
	  
	        /*  
	        numbers 정렬하기  
	        
	        우리가 i for문을 사용하여 i번째 인덱스의 값과 
	        i+1번쨰 인덱스의 값을 
	        비교할 것이므로 i for문의 반복 조건식은 
	        numbers.length - 1이 되어야  
	        4 <-> 5까지 비교하고 i for문이 종료가 된다.  
	        */        
	        for (int i = 0; i < numbers.length - 1; i++) {  
	        // numbers의 i번째와 i+1번째를 비교하여 
	        // i번째가 더 크면 실행되는 if문을 만들어준다.  
	            if (numbers[i] > numbers[i + 1]) {  
	                int temp = numbers[i];  
	                numbers[i] = numbers[i + 1];  
	                numbers[i + 1] = temp;  
	        // i for문 내부의 코드가 전부 실행되고 나서  
	        // 실행되는 코드는 for문의 ,i++이기 때문에  
	        // i를 -1로 초기화 해야 i++이 실행, i가 0으로 변화된다.  
	                i = -1;  
	            }  
	        }  
	        // 결과값 출력  
	        for (int i = 0; i < numbers.length; i++) {  
	            System.out.printf("numbers 2[%d]: %d\n", i, numbers[i]);  
	        }  
	    }  
	}
	```
	
- version 4
	```java
	package day0507;  
	  
	import java.util.Random;  
	import java.util.Scanner;  
	  
	/*  
	로또 번호 제작지 ver 1.1사용자로부터 1~45 숫자 6개를 입력받아서  
	컴퓨터의 당첨 숫자와 비교하여  
	맞춘 갯수를 출력하는 프로그램을 작성하시오  
	단, 사용자가 잘못된 숫자를 입력하면 올바른 숫자가 입력될때까지 입력을 받으세요.  
	1시 20분까지  
	*/
	public class Ex05Lotto04 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        Random random = new Random();  
	        //0.Magic Number 해소를 위한 상수  
	        final int LENGTH = 6;  
	        final int MIN_VALUE = 1;  
	        final int MAX_VALUE = 45;  
			  
	        // 1. 컴퓨터 숫자를 저장할 int[] 
	        // int[] computerNumbers = new int[LENGTH];  
	        // 2. 사용자 숫자를 저장할 int[]        
	        // int[] userNumbers = new int[LENGTH];  
	        // 3. 컴퓨터 배열에 중복되지 않는 숫자 6개 저장  
	        for (int i = 0; i < computerNumbers.length; ) {  
	            int randomNumber = random.nextInt(MAX_VALUE) + MIN_VALUE;  
	            boolean isDuplicated = false;  
				  
	            // 현재 배열에서 입력될 인덱스는 i번째 이므로,  
	            // 우리가 중복인지 아닌지를 검사할 인덱스는 i 이전까지만  
	            // 검사하면 된다.  
	            // 따라서 j for문의 조건식은 j < i로 하면 된다.  
	            for (int j = 0; j < i; j++) {  
	                // 만약 randomNumber의 현재 값이  
	                // conputerNumbers의 j번째의 현재 값과 같으면  
	                // isDuplicated의 값은 true로 변경해준다.  
	                if (randomNumber == computerNumbers[j]) {  
	                    isDuplicated = true;  
	                }  
	            }  
				  
	            // isDuplicated에 false가 저장되어있으면  
	            // 해당 randomNumber는 중복되지 않은 숫자이므로  
	            // computerNumbers배열의 i번쨰에 저장하고,  
	            // i를 1 증가시켜준다.  
	            if (!isDuplicated) {  
	                computerNumbers[i] = randomNumber;  
	                i++;  
	            }  
	        }  
			  
	        // 4. computerNumber 정렬  
	        // 정렬에서는 우리가 i번째의 값과 i + 1번 값을 비교하게 되므로  
	        // 배열의 마지막 요소까지 검사하는 것이 아니라  
	        // 0 <->1, 1<->2, 2<->3 ... 4<->5 까지만 검사 될 수 있도록  
	        // i는 마지막 인덱스 - 1까지만 반복될 수 있도록 한다.  
	        for (int i = 0; i < computerNumbers.length - 1; i++) {  
	            if (computerNumbers[i] > computerNumbers[i + 1]) {  
	                int temp = computerNumbers[i];  
	                computerNumbers[i] = computerNumbers[i + 1];  
	                computerNumbers[i + 1] = temp;  
	                i = -1;  
	            }  
	        }  
			  
	        // 5. 사용자로부터 숫자를 입력받아서 배열에 저장하는 for문  
	        for (int i = 0; i < userNumbers.length; ) {  
	            System.out.printf("%d번쨰 숫자를 입력해주세요\n", i + 1);  
	            System.out.println("> ");  
	            int userNumber = scanner.nextInt();  
	            boolean isValid = true;  
				  
	            // userNumber가 올바른 범위가 아닐 경우  
	            // false가 저장되게 한다.  
	            if (!(userNumber >= MIN_VALUE && userNumber <= MAX_VALUE)) {  
	                isValid = false;  
	            }  
	  
	            // 입력된 숫자가 중복일 경우  
	            // isValid에 false가 저장되게 한다.  
	            for (int j = 0; j < i; j++) {  
	                if (userNumber == userNumbers[j]) {  
	                    isValid = false;  
	                }  
	            }  
	  
	            if (isValid) {  
	                userNumbers[i] = userNumber;  
	                i++;  
	            } else {  
	                System.out.println("유효하지 않은 숫자입니다.");  
	            }  
	        }  
	        //6. 사용자 숫자 배열을 정렬해준다.  
	        for (int i = 0; i < userNumbers.length - 1; i++) {  
	            if (userNumbers[i] > userNumbers[i + 1]) {  
	                int temp = userNumbers[i];  
	                userNumbers[i] = userNumbers[i + 1];  
	                userNumbers[i + 1] = temp;  
	                i = -1;  
	            }  
	        }  
	        //7. 컴퓨터 숫자 배열 출력하기  
	        System.out.println("컴퓨터의 숫자 : [");  
	        for (int i = 0; i < computerNumbers.length; i++) {  
	            System.out.printf("%d", computerNumbers[i]);  
	            if (i != computerNumbers.length - 1) {  
	                System.out.println(", ");  
	            }  
	        }  
	        System.out.println("]");  
	  
	        //8. 사용자의 숫자 출력하기  
	        System.out.println("사용자의 숫자:[ ");  
	        for (int i = 0; i < userNumbers.length; i++) {  
	            System.out.printf("%d", userNumbers[i]);  
	            if (i != userNumbers.length - 1) {  
	                System.out.println(" , ");  
	            }  
	        }  
	        System.out.println("]");  
	  
	        //9. 사용자가 몇개를 맞췄는지 출력  
	        // 사용자가 맞춘 갯수를 저장할 int 변수  
	        int count = 0;  
	        for (int i = 0; i < userNumbers.length; i++) {  
	            for (int j = 0; j < computerNumbers.length; j++) {  
	                if (userNumbers[i] == computerNumbers[j]) {  
	                    count++;  
	                }  
	            }  
	        }  
	        System.out.println("총 맞은 갯수: " + count);  
	    }  
	}
	```
	
- version 5
	```java
	package day0507;  
	  
	import java.util.Scanner;  
	  
	/*  
	학생 5명의 번호, 이름, 국어, 영어, 수학 점수를 입력 받아서  
	예쁘게 출력하는 프로그램을 작성하시오  
	단, 한번에 5명의 정보를 모두다 입력하는 것이 아니라  
	메뉴를 만들어서  
	입력  메뉴를 통해 들어갔을 때  
	한명의 정보만 입력을 하되, 만약 5명의 전보를 모두다 입력했을 경우  
	더 이상 입력이 안되게 만드시고  
	출력할 때에는 현재 입력된 학생들만 출력이 되게 만드시오  
	  
	심화 : 만약 5명을 모두다 입력했을 경우, 
	새로운 입력 시 가장 먼저 입력된 정보를 없애고  
	현재 정보가 들어갈 수 있도록 코드를 작성하시오  
	*/
	public class Ex06GradeBook {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        //학생들의 정보를 저장할 배열들  
	        //번호 배열  
	        int[] idArray = new int[5];  
	        //이름 배열  
	        String[] nameArray = new String[5];  
	        //국어 점수 배열  
	        int[] korArray = new int[5];  
	        //영어 점수 배열  
	        int[] engArray = new int[5];  
	        //수학 점수 배열  
	        int[] mathArray = new int[5];  
	        // 다음 입력할 인덱스를 저장할 int 변수  
	        int idx = 0;  
	        boolean trade = true;  
	  
	        while (trade) {  
	            System.out.println("1.입력 2.출력 3.종료");  
	            System.out.println("> ");  
	            int userChoice = scanner.nextInt();  
	            switch (userChoice) {  
	                case 1:  
	                    // 입력 코드 구현  
	                    if (idx < idArray.length) {  
	                        //더 이상 학생을 입력할 수 없음.  
		                    System.out.println
		                    ("더 이상 학생을 입력할 수 없습니다.");  
	                        //아직 학생을 더 입력할 수 있음.  
	                        //번호를 받는다.  
	                        System.out.println("번호 : ");  
	                        idArray[idx] = scanner.nextInt();  
	                        System.out.println("이룸 : ");  
	                        scanner.nextLine();  
	                        nameArray[idx] = scanner.nextLine();  
	                        //번호를 받는다.  
	                        System.out.println("국어 : ");  
	                        korArray[idx] = scanner.nextInt();  
	                        //번호를 받는다.  
	                        System.out.println("영어 : ");  
	                        engArray[idx] = scanner.nextInt();  
	                        //번호를 받는다.  
	                        System.out.println("수학 : ");  
	                        mathArray[idx] = scanner.nextInt();  
	                        idx++;  
	                    } else {  
	                        //각 배열의 요소를 한칸식 땡긴다.  
	                        for (int i = 1; i < idArray.length; i++) {  
	                            idArray[i - 1] = idArray[i];  
	                            nameArray[i - 1] = nameArray[i];  
	                            korArray[i -1] = korArray[i];  
	                            engArray[i -1] = engArray[i];  
	                            mathArray[i -1] = mathArray[i];  
	                        }  
	                        //입력을 받는다.  
	                        //배열의 가장 마지막 인덱스  
	                        int lastIndex = idArray.length - 1;  
	                    }  
	                    break;  
	                case 2:  
	                    // 출력 코드 구현  
	                    if (idx == 0) {  
	                        // idx의 값이 0이다.  
	                        // -> idx++이 실행된 적이 없다.  
	                        // -> idx++은 학생 정보 입력을 해야지만 실행된다.  
	                        // -> 따라서 아직 입력된 학생이 존재하지 않는다.  
	                        System.out.println
	                        ("아직 입력된 정보가 존재하지 않습니다.");  
	                    } else {  
	                        for (int i = 0; i < idx; i++) {  
	                            //i번째 학생의 총점 계산  
	                            int sum = 
	                            korArray[i] + engArray[i] + mathArray[i];  
	                            //평균 계산  
	                            double average = (double) sum / 3;  
	                            System.out.printf
	                            ("%d번. %s\n", idArray[i], nameArray[i]);  
	                            System.out.printf
	                            ("국어 : %d 영어 : %d 수학 : %d", 
	                            korArray[i], engArray[i], mathArray[i]);  
	                            System.out.printf
	                            ("총점 : %d 평균 : %06.2f점\n", sum, average);  
	                        }  
	                    }  
	                    break;  
	                case 3:  
	                    System.out.println("사용해주셔서 감사합니다.");  
	                    trade = false;  
	                    break;  
	            }  
	        }  
	    }  
	}
	```
	
- version 6
	```java
	package day0507;  
	  
	import java.util.Scanner;  
	  
	/*  
	학생 5명의 번호, 이름, 국어, 영어, 수학 점수를 입력 받아서  
	예쁘게 출력하는 프로그램을 작성하시오  
	단, 한번에 5명의 정보를 모두다 입력하는 것이 아니라  
	메뉴를 만들어서 입력  메뉴를 통해 들어갔을 때  
	한명의 정보만 입력을 하되, 만약 5명의 전보를 모두다 입력했을 경우  
	더 이상 입력이 안되게 만드시고  
	출력할 때에는 현재 입력된 학생들만 출력이 되게 만드시오  
	  
	심화 : 만약 5명을 모두다 입력했을 경우, 
	새로운 입력 시 가장 먼저 입력된 정보를 없애고  
	현재 정보가 들어갈 수 있도록 코드를 작성하시오  
	*/
	 public class Ex06GradeBook2 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        //학생들의 정보를 저장할 배열들  
	        //번호 배열  
	        int[] idArray = new int[5];  
	        //이름 배열  
	        String[] nameArray = new String[5];  
	        //국어 점수 배열  
	        int[] korArray = new int[5];  
	        //영어 점수 배열  
	        int[] engArray = new int[5];  
	        //수학 점수 배열  
	        int[] mathArray = new int[5];  
	        // 다음 입력할 인덱스를 저장할 int 변수  
	        int idx = 0;  
	        boolean trade = true;  
	        while (trade) {  
	            System.out.println("1.입력 2.출력 3.종료");  
	            System.out.println("> ");  
	            int userChoice = scanner.nextInt();  
	            switch (userChoice) {  
	                case 1:  
	                    // 입력 코드 구현  
	                    if (idx < idArray.length) {  
	                        //더 이상 학생을 입력할 수 없음.  
	                        System.out.println
	                        ("더 이상 학생을 입력할 수 없습니다.");  
	                    }  
	                    //아직 학생을 더 입력할 수 있음.  
	                    //번호를 받는다.  
	                    System.out.println("번호 : ");  
	                    idArray[idx] = scanner.nextInt();  
	                    System.out.println("이룸 : ");  
	                    scanner.nextLine();  
	                    nameArray[idx] = scanner.nextLine();  
	                    //번호를 받는다.  
	                    System.out.println("국어 : ");  
	                    korArray[idx] = scanner.nextInt();  
	                    //번호를 받는다.  
	                    System.out.println("영어 : ");  
	                    engArray[idx] = scanner.nextInt();  
	                    //번호를 받는다.  
	                    System.out.println("수학 : ");  
	                    mathArray[idx] = scanner.nextInt();  
	                    idx++;  
	                    break;  
	                case 2:  
	                    // 출력 코드 구현  
	                    if (idx == 0) {  
	                        // idx의 값이 0이다.  
	                        // -> idx++이 실행된 적이 없다.  
	                        // -> idx++은 학생 정보 입력을 해야지만 실행된다.  
	                        // -> 따라서 아직 입력된 학생이 존재하지 않는다.  
	                        System.out.println
	                        ("아직 입력된 정보가 존재하지 않습니다.");  
	                    } else {  
	                        for (int i = 0; i < idx; i++) {  
	                            //i번째 학생의 총점 계산  
	                            int sum = 
	                            korArray[i] + engArray[i] + mathArray[i];  
	                            //평균 계산  
	                            double average = (double) sum / 3;  
	  
	                            System.out.printf
	                            ("%d번. %s\n", idArray[i], nameArray[i]);  
	                            System.out.printf
	                            ("국어 : %d 영어 : %d 수학 : %d", 
	                            korArray[i], engArray[i], mathArray[i]);  
	                            System.out.printf
	                            ("총점 : %d 평균 : %06.2f점", sum, average);  
	                        }  
	                    }  
	                    break;  
	                case 3:  
	                    System.out.println("사용해주셔서 감사합니다.");  
	                    trade = false;  
	                    break;  
	            }  
	        }  
	    }  
	}
	```
	
- version 7
	```java
	package day0508;  
	  
	// 로또 번호 제작기  
	// 사용자로부터 게임 수를 입력 받아서  
	// 한번에 여러 게임을 할 수 있는 로또 번호 제작 프로그램을 작성하시오.  
	// 몇게임 하시겠습니까?  
	// > 5  
	// 1번째 게임  
	// 1. 수동 2. 자동  
	// > 1  
	// 1번째 숫자를 입력해주세요 .....// 2번째 게임  
	// 1. 수동 2. 자동  
	// > 2  
	// 3번째 게임 ......// 컴퓨터의 숫자: [...]  
	// 사용자의 1번째 게임: [....] -> x개 맞음  
	  
	import java.util.Scanner;  
	import java.util.Random;  
	  
	public class Ex02Lotto {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        Random random = new Random();  
			  
	        // 1. 컴퓨터 숫자 정하기  
	        // 컴퓨터 숫자를 저장할 배열  
	        int[] computerNumbers = new int[6];  
	        // computerNumbers에 중복되지 않는 숫자 6개 저장  
	        for (int i = 0; i < computerNumbers.length; ) {  
	            int randomNumber = random.nextInt(45) + 1;  
	            boolean isDuplicated = false;  
	            for (int j = 0; j < i; j++) {  
	                if (randomNumber == computerNumbers[j]) {  
	                    isDuplicated = true;  
	                }  
	            }  
	  
	            if (!isDuplicated) {  
	                computerNumbers[i] = randomNumber;  
	                i++;  
	            }  
	        }  
			  
	        // computerNumbers 정렬  
	        for (int i = 0; i < computerNumbers.length - 1; i++) {  
	            if (computerNumbers[i] > computerNumbers[i + 1]) {  
	                int temp = computerNumbers[i];  
	                computerNumbers[i] = computerNumbers[i + 1];  
	                computerNumbers[i + 1] = temp;  
	                i = -1;  
	            }  
	        }  
			  
	        // 사용자로부터 입력을 받아서  
	        // 게임수, 수동/자동 처리 하기  
	        System.out.println("몇 게임하시겠습니까?");  
	        System.out.print("> ");  
	        int gameSize = scanner.nextInt();  
			  
	        // 사용자가 입력한 수를 토대로 배열 생성  
	        int[][] userNumbers = new int[gameSize][6];  
			  
	        // 각 게임에 대한 수동/자동 처리  
	        for (int i = 0; i < userNumbers.length; i++) {  
	            System.out.println("=============================");  
	            System.out.println((i + 1) + "번째 게임");  
	            System.out.println("=============================");  
	            // 자동/수동 입력받기  
	            System.out.println("1. 자동 2. 수동");  
	            System.out.print("> ");  
	            int userChoice = scanner.nextInt();  
			  
	            for (int j = 0; j < userNumbers[i].length; ) {  
	                int temp;  
	                if (userChoice == 2) {  
	                    System.out.println((j + 1) + "번째 숫자");  
	                    System.out.println("1~45 사이의 숫자를 입력해주세요.");  
	                    System.out.print("> ");  
	                    temp = scanner.nextInt();  
	                } else {  
	                    temp = random.nextInt(45) + 1;  
	                }  
					  
	                boolean isValid = true;  
					  
	                if (!(temp >= 1 && temp <= 45)) {  
	                    isValid = false;  
	                }  
					  
	                for (int k = 0; k < j; k++) {  
	                    if (temp == userNumbers[i][k]) {  
	                        isValid = false;  
	                    }  
	                }  
					  
	                if (isValid) {  
	                    userNumbers[i][j] = temp;  
	                    j++;  
	                } else if (userChoice == 2) {  
	                    System.out.println("잘못 입력하셨습니다.");  
	                }  
	            }  
	            System.out.println("-----------------------------\n");  
	        }  
			  
	        // 사용자 숫자 정렬  
	        for (int i = 0; i < userNumbers.length; i++) {  
	            // i번째 게임 정렬  
	            for (int j = 0; j < userNumbers[i].length - 1; j++) {  
	                if (userNumbers[i][j] > userNumbers[i][j + 1]) {  
	                    int temp = userNumbers[i][j];  
	                    userNumbers[i][j] = userNumbers[i][j + 1];  
	                    userNumbers[i][j + 1] = temp;  
	                    j = -1;  
	                }  
	            }  
	        }  
			  
	        // 컴퓨터 숫자 출력  
	        System.out.print("컴퓨터 숫자: [");  
	        for (int i = 0; i < computerNumbers.length; i++) {  
	            System.out.printf("%d", computerNumbers[i]);  
	            if (i != computerNumbers.length - 1) {  
	                System.out.print(", ");  
	            }  
	        }  
	        System.out.println("]");  
			  
	        // 사용자의 숫자와 결과를 출력한다.  
	        System.out.println("결과");  
	        for (int i = 0; i < userNumbers.length; i++) {  
	            System.out.println("===================");  
	            System.out.println((i + 1) + "번째 게임");  
	            System.out.println("===================");  
				  
	            // 맞은 갯수를 저장할 int 변수  
	            int count = 0;  
				  
	            System.out.print("사용자의 숫자: [");  
	            for (int j = 0; j < userNumbers[i].length; j++) {  
	                for (int k = 0; k < computerNumbers.length; k++) {  
	                    if (userNumbers[i][j] == computerNumbers[k]) {  
	                        count++;  
	                    }  
	                }  
	                System.out.printf("%d", userNumbers[i][j]);  
	                if (j != userNumbers[i].length - 1) {  
	                    System.out.print(", ");  
	                }  
	            }  
	            System.out.println("] - 맞은 갯수: " + count);  
	        }  
	    }  
	}
	```
	
- version 8
	```java
	package day0509;  
	  
	// 로또 번호 제작기  
	// ArrayUtil을 사용한 버젼  
	  
	import java.util.Random;  
	import java.util.Scanner;  
	import util.ArrayUtil;  
	import util.ScannerUtil;  
	  
	public class Ex01Lotto {  
	    public static void main(String[] args) {  
	        Random random = new Random();  
	        Scanner scanner = new Scanner(System.in);  
	  
	        // 컴퓨터의 숫자를 저장할 배열  
	        int[] computerNumbers = new int[0];  
	  
	        // 중복되지 않은 랜덤 숫자 6개를 computerNumbers에 추가한다.  
	        while (ArrayUtil.size(computerNumbers) < 6) {  
	            // 1~45까지의 랜덤한 숫자를 하나 뽑는다.  
	            int temp = random.nextInt(45) + 1;  
	            // 만약 temp가 computerNumbers에 없으면  
	            // temp를 computerNumbers에 추가한다.  
	            if (!ArrayUtil.contains(computerNumbers, temp)) {  
	                computerNumbers = ArrayUtil.add(computerNumbers, temp);  
	            }  
	        }  
	        // 정렬하기  
	        for (int i = 0; i < ArrayUtil.size(computerNumbers) - 1; i++) {  
	            if (ArrayUtil.get(computerNumbers, i) >  
	                    ArrayUtil.get(computerNumbers, i + 1)) {  
	                int temp = ArrayUtil.get(computerNumbers, i);  
	                computerNumbers[i] = ArrayUtil.get
	                (computerNumbers, i + 1);  
	                computerNumbers[i + 1] = temp;  
	                i = -1;  
	            }  
	        }  
	        for (int i = 0; i < ArrayUtil.size(computerNumbers); i++) {  
	            System.out.println(ArrayUtil.get(computerNumbers, i));  
	        }  
	    }  
	}
	```
##### 별찍기
	
- 별찍기 1
	```java
	  package day0503;  
	/*
	1부터 100까지의 소수를 구하는 프로그램  
	소수란?  
	1과 자기 자신으로 나눠지는 수  
	= 약수가 2개인 숫자  
	약수란?  
	A를 B로 나눴을 때, 나눠 떨어지면  
	B는 A의 약수이다.  
	= A를 B로 나눴을 때, 나머지가 0과 같으면  
	B는 A의 약수이다.  
	*/
	public class Ex01PrimeNumber {  
	    public static void main(String[] args) {  
	        // i for문에서 i는 소수인지 아닌지를 검사할 숫자가 된다.  
	        // 그렇다면 i의 시작값은? 1  
	        // i의 반복 조건식은? i <= 100  
	        for (int i = 1; i <= 100; i++) {  
	            // i의 약수의 갯수를 저장할 int 변수  
	            int count = 0;  
	  
	            // j for문의 j는 i의 약수인지 아닌지를 검사할 숫자가 된다.  
	            // 그렇다면 j의 시작값은? 1  
	            // j의 반복 조건식은? j <= i  
	            for (int j = 1; j <= i; j++) {  
	                // j for문이 반복되는 동안  
	                // i 나누기 j의 나머지가 0과 같으면  
	                // j 는 i의 약수이므로,  
	                // count를 1 증가시킨다.  
	                if (i % j == 0) {  
	                    count++;  
	                }  
	            }  
	            if (count == 2) {  
	                System.out.println(i + "은 소수입니다.");  
	            }  
	        }  
	    }  
	}
	
	```
	
- 별찍기 2
	```java
	package day0503;  
	  
	import java.util.Scanner;  
	  
	public class StarPrinter02 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	  
	        System.out.println("======================================");  
	        System.out.println("             별찍기 2번");  
	        System.out.println("======================================");  
	        System.out.println("\n출력할 줄 수를 입력해주세요.");  
	        System.out.print("> ");  
	        int userNumber = scanner.nextInt();  
	  
	        // 출력할 총 줄의 숫자를 저장할 int 변수  
	        int height = userNumber;  
	        for (int i = 1; i <= height; i++) {  
	            // 해당 줄의 출력 내용을 저장할 String 변수  
	            String stars = "";  
	            for (int j = i; j <= userNumber; j++) {  
	                stars += "*";  
	            }  
	            System.out.println(stars);  
	        }  
	    }  
	}
	```
	
- 별찍기 3
	```java
	package day0503;  
	  
	import java.util.Scanner;  
	  
	public class StarPrinter03 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	  
	        System.out.println("======================================");  
	        System.out.println("             별찍기 3번");  
	        System.out.println("======================================");  
	        System.out.println("\n출력할 줄 수를 입력해주세요.");  
	        System.out.print("> ");  
	        int userNumber = scanner.nextInt();  
	        int height = userNumber;  
	        for (int i = 1; i <= height; i++) {  
	            String stars = "";  
	            // 공백을 담당하는 j for 문  
	            for (int j = 1; j <= userNumber - i; j++) {  
	                stars += " ";  
	            }  
	            // 별을 담당하는 j for 문  
	            for (int j = 1; j <= i; j++) {  
	                stars += "*";  
	            }  
	            System.out.println(stars);  
	        }  
	    }  
	}
	```
	
- 별찍기 4
	```java
	package day0503;  
	  
	import java.util.Scanner;  
	  
	public class StarPrinter04 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        System.out.println("======================================");  
	        System.out.println("             별찍기 4번");  
	        System.out.println("======================================");  
	        System.out.println("\n출력할 줄 수를 입력해주세요.");  
	        System.out.print("> ");  
	        int userNumber = scanner.nextInt();  
	        int height = userNumber;  
	        for (int i = 1; i <= height; i++) {  
	            String stars = "";  
	            // 공백을 담당하는 j for문  
	            for (int j = 1; j <= i - 1; j++) {  
	                stars += " ";  
	            }  
	            // 별을 담당하는 j for문  
	            for (int j = i; j <= userNumber; j++) {  
	                stars += "*";  
	            }  
	            System.out.println(stars);  
	        }  
	    }  
	}
	```
	
- 별찍기 5
	```java
	package day0503;  
	  
	import java.util.Scanner;  
	  
	public class StarPrinter05 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);    
	        System.out.println("======================================");  
	        System.out.println("             별찍기 5번");  
	        System.out.println("======================================");  
	        System.out.println("\n출력할 줄 수를 입력해주세요.");  
	        System.out.print("> ");  
	        int userNumber = scanner.nextInt();  
	        int height = userNumber;  
	        for (int i = 1; i <= userNumber; i++) {  
	            // 해당 줄의 출력 내용을 저장할 String 변수  
	            String stars = "";  
	            // 해당 줄의 공백의 갯수를 저장할 int 변수  
	            int spaceWidth = userNumber - i;  
	            // 해당 줄의 별의 갯수를 저장할 int 변수  
	            int starWidth = 2 * i - 1;  
	            // 공백을 담당하는 j for 문  
	            for (int j = 1; j <= spaceWidth; j++) {  
	                stars += " ";  
	            }  
	            // 별을 담당하는 j for 문  
	            for (int j = 1; j <= starWidth; j++) {  
	                stars += "*";  
	            }  
	            System.out.println(stars);  
	        }  
	    }  
	}
	```
	
- 별찍기 6
	```java
	package day0503;  
	  
	import java.util.Scanner;  
	  
	public class StarPrinter06Easy {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        System.out.println("======================================");  
	        System.out.println("             별찍기 6번 쉬운 버젼");  
	        System.out.println("======================================");  
	        System.out.println("\n출력할 줄 수를 입력해주세요.");  
	        System.out.print("> ");  
	        int userNumber = scanner.nextInt();  
	        int height = userNumber;  
	        for (int i = height; i >= 1; i--) {  
	            String stars = "";  
	            int spaceWidth = userNumber - i;  
	            int starWidth = 2 * i - 1;  
	            for (int j = 1; j <= spaceWidth; j++) {  
	                stars += " ";  
	            }  
	            for (int j = 1; j <= starWidth; j++) {  
	                stars += "*";  
	            }  
	            System.out.println(stars);  
	        }  
	    }  
	}
	```
	
- 별찍기 7
	```java
	package day0503;  
	  
	import java.util.Scanner;  
	  
	public class StarPrinter07 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);    
	        System.out.println("======================================");  
	        System.out.println("             별찍기 7번");  
	        System.out.println("======================================");  
	        System.out.println("\n출력할 줄 수를 입력해주세요.");  
	        System.out.print("> ");  
	        int userNumber = scanner.nextInt();  
	    }  
	}
	```
	
- 별찍기 8
	```java
	package day0503;  
	  
	import java.util.Scanner;  
	  
	public class StarPrinter08 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);    
	        System.out.println("======================================");  
	        System.out.println("             별찍기 8번");  
	        System.out.println("======================================");  
	        System.out.println("\n출력할 줄 수를 입력해주세요.");  
	        System.out.print("> ");  
	        int userNumber = scanner.nextInt();  
	    }  
	}
	```
	
- 별찍기 9
	```java
	package day0503;  
	  
	import java.util.Scanner;  
	  
	public class StarPrinter09 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);    
	        System.out.println("======================================");  
	        System.out.println("             별찍기 9번");  
	        System.out.println("======================================");  
	        System.out.println("\n출력할 줄 수를 입력해주세요.");  
	        System.out.print("> ");  
	        int userNumber = scanner.nextInt();  
	    }  
	}
	```
	
- 별찍기 10
	```java
	package day0503;  
	  
	import java.util.Scanner;  
	  
	public class StarPrinter10 {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	        System.out.println("======================================");  
	        System.out.println("             별찍기 10번");  
	        System.out.println("======================================");  
	        System.out.println("\n출력할 줄 수를 입력해주세요.");  
	        System.out.print("> ");  
	        int userNumber = scanner.nextInt();  
	    }  
	}
	```
	

##### 예제 코드
	
- Board
	```java
	package day0514;  
	  
	import types.Board;  
	import util.ScannerUtil;  
	import java.util.ArrayList;  
	import java.util.Scanner;  
	  
	/*  
	게시판 클래스와 어레이리스트를 활용하여  
	게시판 프로그램을 작성하시오  
	11시 30분까지  
	 */
	public class Ex01Board {  
    public static ArrayList<Board> list = new ArrayList<>();  
	public static int boardId = 1;  
	public static final Scanner SCANNER = new Scanner(System.in);  
	public static final int MENU_MIN = 1;  
	public static final int MENU_MAX = 3;  
	  
	public static void main(String[] args) {  
	    showBoard();  
	}  
	  
		public static void showBoard() {  
	     while (true) {  
		        String message = "1.작성 | 2.조회 | 3.종료";  
		        int userInput = ScannerUtil.nextInt(SCANNER, message, 1, 3);  
		        if (userInput == 1) {  
	            insertPost();  
		        } else if (userInput == 2) {  
			    viewPost();  
		        } else if (userInput == 3) {  
		            System.out.println("이용해주셔서 감사합니다.");  
		        break;  
		            }  
		        }  
		    }  
		  
	    public static void insertPost() {  
	        Board b = new Board();  
	        b.setId(boardId++);  
	        String message;  
	        message = "작성자 이름 : ";  
	        String name = ScannerUtil.nextLine(SCANNER, message);  
	        b.setName(name);  
	        message = "제목 : ";  
	        String title = ScannerUtil.nextLine(SCANNER, message);  
	        b.setTitle(title);  
	        message = "글내용 : ";  
	        String content = ScannerUtil.nextLine(SCANNER, message);  
	        b.setContent(content);  
	        list.add(b);  
	    }  
	  
	    public static void viewPost() {  
	        if (list.isEmpty()) {  
	            System.out.println("게시물이 없습니다.");  
	        } else {  
	            for (int i = 0; i < list.size(); i++) {  
	                Board b = list.get(i);  
	                System.out.printf
	                ("글번호 : %s 작성자 : %s\n", b.getId(), b.getName());  
	            }  
	            for (Board b : list) {  
	                System.out.printf
	                ("글번호 : %s 작성자 : %s\n", b.getId(), b.getName());  
	            }  
	            String message = "게시물 상세보기 or 뒤로 가기 : 0번 입력";  
	            int userChoice = ScannerUtil.nextInt(SCANNER, message);  
	            while (!vaildate(userChoice)) {  
	                System.out.println("잘못 입력하셨습니다.");  
	                userChoice = ScannerUtil.nextInt(SCANNER, message);  
	            }  
	            if (userChoice != 0) {  
	                printOne(userChoice);  
	            }  
	        }  
	    }  
		  
	    private static void printOne(int id) {  
	        Board b = selectOne(id);  
	        if (b == null) {  
	            System.out.println("잘못된 번호입니다.");  
	            System.out.println("게시물 목록으로 돌아갑니다.");  
	            viewPost();  
	        } else {  
	            b.printList();  
	            String message = "1.수정 | 2.삭제 | 3.뒤로가기";  
	            int userInput = ScannerUtil.nextInt(SCANNER, message, 1, 3);  
	            if (userInput == 1) {  
	                update(id);  
	            } else if (userInput == 2) {  
	                delete(id);  
	            } else if (userInput == 3) {  
	                viewPost();  
	            }  
	        }  
	    }  
		  
	    private static void update(int id) {  
	        Board b = new Board();  
	        String message;  
	        message = "이름 : ";  
	        b.setName(ScannerUtil.nextLine(SCANNER, message));  
	        message = "제목 : ";  
	        b.setTitle(ScannerUtil.nextLine(SCANNER, message));  
	        message = "내용 : ";  
	        b.setContent(ScannerUtil.nextLine(SCANNER, message));  
	        printOne(id);  
	        list.add(b);  
	    }  
		  
	    private static void delete(int id) {  
	        Board b = selectOne(id);  
	        String message = "정말로 삭제하시겠습니까? Y / N";  
	        String answer = ScannerUtil.nextLine(SCANNER, message);  
	        if (answer.equalsIgnoreCase("Y")) {  
	            list.remove(b);  
	            viewPost();  
	        } else {  
	            printOne(id);  
	        }  
	    }  
		  
	    private static boolean vaildate(int userChoice) {  
	        if (userChoice == 0) {  
	            return true;  
	        }  
	        Board b = new Board();  
	        b.setId(userChoice);  
	        return list.contains(b);  
	    }  
		  
	    private static Board selectOne(int id) {  
	        Board b = new Board();  
	        b.setId(id);  
	        int index = list.indexOf(new Board());  
	        if (index != -1) {  
	            return list.get(index);  
	        } else {  
	            return null;  
	        }  
	    }  
	}
	```
	
- Board ver 2.0
	- 어레이리스트에서 DB로 데이터 저장 수단을 변경
	```java
	```
	
- Board ver 3.0
	- viewer를 HTML 템플릿으로 변경
	```java
	```
	
- 
	```java
	```
	
	



##### Util / Type / Interface / ETC
	
- LetterGrade
	```java
	package day0502;  
	  
	import java.util.Scanner;  
	  
	/*
	사용자로부터 점수를 입력 받아서  
	90점 이상 : A
	80대 : B
	70대 : C
	60대 : D
	50대 미만 : F가 출력되는 프로그램을 작성하시오  
	*/
	 public class Ex03LetterGrade {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	  
	        System.out.println("점수를 입력하세요.");  
	        int scours = scanner.nextInt();  
	  
	        System.out.println("-------------------");  
	        System.out.println("검증을 안할 경우");  
	        if (scours >= 90){  
	            System.out.println("A");  
	        } else if (scours >= 80){  
	            System.out.println("B");  
	        } else if (scours >= 70){  
	            System.out.println("C");  
	        } else if (scours >= 60){  
	            System.out.println("D");  
	        } else {  
	            System.out.println("F");  
	        }  
	    }  
	}
	```
	
- Validation
	```java
	package day0502;  
	  
	import java.util.Scanner;  
	/*
	사용자가 입력한 값이 언제나 우리의 의도대로 올바른 값만 들어오지 않기 때문에  
	입력된 값에 대한 검증이 필요로 한다.  
	*/
	 public class Ex04Validation {  
	    public static void main(String[] args) {  
	        Scanner scanner = new Scanner(System.in);  
	  
	        System.out.println("점수를 입력하세요.");  
	        int scours = scanner.nextInt();  
	  
	        System.out.println("-------------------");  
	        System.out.println("검증을 안할 경우");  
	        if (scours >= 90) {  
	            System.out.println("A");  
	        } else if (scours >= 80) {  
	            System.out.println("B");  
	        } else if (scours >= 70) {  
	            System.out.println("C");  
	        } else if (scours >= 60) {  
	            System.out.println("D");  
	        } else {  
	            System.out.println("F");  
	        }  
	        System.out.println("===================");  
	  
	         값 검증을 하는 첫번째 방법 조건식을 정확하게 잡아주기         
	         이 방법은 조건이 연속적이지 않을 경우 효율적이다.  
	        if (scours >= 90 && scours <= 100) {  
	            System.out.println("A");  
	        } else if (scours >= 80 && scours < 90) {  
	            System.out.println("B");  
	        } else if (scours >= 70 && scours < 80) {  
	            System.out.println("C");  
	        } else if (scours >= 60 && scours < 70) {  
	            System.out.println("D");  
	        } else if (scours >= 0 && scours < 60) {  
	            System.out.println("F");  
	        } else {  
	            System.out.println("올바르지 않는 점수입니다.");  
	        }  
	  
	        두번째 방법  
	        먼저 입력된 값이 올바른지 체크하고 올바른 값이 입력되었을 때에만 
	        코드를 진행시키는 방법.  
	        이 방법은 올바른 값의 범위가 연속적일 경우 효율적이다.  
	        
	        System.out.println("=======================");  
	        System.out.println("입력값 먼저 검증하기");  
	        System.out.println("=======================");  
	        if (scours >= 0 && scours <= 100){  
	            System.out.println("A");  
	        } else if (scours >= 80 && scours < 90) {  
	            System.out.println("B");  
	        } else if (scours >= 70 && scours < 80) {  
	            System.out.println("C");  
	        } else if (scours >= 60 && scours < 70) {  
	            System.out.println("D");  
	        } else if (scours >= 0 && scours < 60) {  
	            System.out.println("F");  
	        } else {  
	            System.out.println("올바르지 않는 점수입니다.");  
	        }  
	    }  
	}
	```
	
- DynamicAlloc
	```java
	package day0508;  
	  
	import util.ArrayUtil;  
	  
	// 배열의 동적 할당(Dynamic Allocation)  
	// 현재까지 배운 배열의 최대 단점: 크기가 고정되어있다.  
	// 이렇게 크기를 처음부터 지정하고 만드는 배열을  
	// 우리는 정적 할당(Static Allocation) 이라고 한다.  
	// 하지만 우리가 크기가 자유로운 배열을 만들 경우, 해당 배열을  
	// 동적 할당이 되는 배열이라고 한다.  
	// 하지만, 진정한 동적 할당이 되기 위해서는  
	// 우리가 직접 주소값을 컨트롤 하여 이어붙이거나 없애거나를 해야 하지만  
	// 자바에서는 주소값을 직접적으로 컨트롤 할 수 없으므로  
	// 우리는 유사 동적 할당을 하게 될 것이다.  
	public class Ex05DynamicAlloc {  
	    public static void main(String[] args) {  
	        System.out.println("1. int[]");  
	        System.out.println("A. size()");  
	        int[] array = new int[4];  
	        System.out.println
	        ("ArrayUtil.size(array): " + ArrayUtil.size(array));  
	        
	        System.out.println("B. isEmpty()");  
	        System.out.println
	        ("ArrayUtil.isEmpty(array): " + ArrayUtil.isEmpty(array));  
	        array[1] = 30;  
	        array[3] = 30;  
	        
	        System.out.println("C. get()");  
	        System.out.println
	        ("ArrayUtil.get(array, 1): " + ArrayUtil.get(array, 1));  
	        
	        System.out.println("D. indexOf()");  
	        System.out.println
	        ("ArrayUtil.indexOf(array, 30): " + ArrayUtil.indexOf(array, 30)); 
	        System.out.println
	        ("ArrayUtil.indexOf(array, 20): " + ArrayUtil.indexOf(array, 20)); 
	        
	        System.out.println("E. lastIndexOf()");  
	        System.out.println
	        ("ArrayUtil.lastIndexOf(array, 30): " + 
	        rayUtil.lastIndexOf(array, 30));  
	        System.out.println
	        ("ArrayUtil.lastIndexOf(array, 20): " + 
	        ArrayUtil.lastIndexOf(array, 20));  
	        
	        System.out.println("F. contains()");  
	        System.out.println
	        ("ArrayUtil.contains(array, 30): " + 
	        ArrayUtil.contains(array, 30));  
	        System.out.println
	        ("ArrayUtil.contains(array, 20): " + 
	        ArrayUtil.contains(array, 20));  
	        
	        System.out.println("G. add()");  
	        System.out.println
	        ("add() 전 ArrayUtil.size(array): " + 
	        ArrayUtil.size(array));  
	        array = ArrayUtil.add(array, 10);  
	        System.out.println
	        ("add() 후 ArrayUtil.size(array): " + 
	        ArrayUtil.size(array));  
	        
	        System.out.println("H. add()");  
	        System.out.println
	        ("add() 전 ArrayUtil.get(array, 2): " + 
	        ArrayUtil.get(array, 2));  
	        array = ArrayUtil.add(array, 2, 340);  
	        System.out.println
	        ("add() 후 ArrayUtil.get(array, 2): " + 
	        ArrayUtil.get(array, 2));  
	        
	        System.out.println("I. set()");  
	        System.out.println
	        ("set() 전 ArrayUtil.get(array, 2): " + ArrayUtil.get(array, 2));  
	        int origin = ArrayUtil.set(array, 2, 50);  
	        System.out.println
	        ("set() 후 ArrayUtil.get(array, 2): " + ArrayUtil.get(array, 2));  
	        System.out.println("set() 후 원래 값: " + origin);  
	        
	        System.out.println("J. remove()");  
	        System.out.println
	        ("remove() 전 ArrayUtil.size(array): " + ArrayUtil.size(array));  
	        System.out.println
	        ("remove() 전 ArrayUtil.get(array, 2): " + 
	        ArrayUtil.get(array, 2));  
	        array = ArrayUtil.remove(array, 2);  
	        System.out.println
	        ("remove() 후 ArrayUtil.size(array): " + ArrayUtil.size(array));  
	        System.out.println
	        ("remove() 후 ArrayUtil.get(array, 2): " + 
	        ArrayUtil.get(array, 2));  
	        
	        System.out.println("K. removeElement()");  
	        array[2] = 890;  
	        System.out.println
	        ("removeElement() 전 contains(890): " + 
	        ArrayUtil.contains(array, 890));  
	        array = ArrayUtil.removeElement(array, 890);  
	        System.out.println
	        ("removeElement() 후 contains(890): " + 
	        ArrayUtil.contains(array, 890));  
	    }  
	}
	```
	
- Util_ArrayUtil
	``` java
	package util;  
	  
	// 배열을 다룰 때 도움이 될 메소드들을 모아둔 클래스  
	public class ArrayUtil {  
			  
	        // 1. int[]  
	        // 1-A. 현재 배열의 길이를 리턴하는 size()        
	        // public static int size(int[] array) {  
	            return array.length;  
	        }  
			  
	        // 1-B. 현재 배열이 아무것도 없으면 true, 있으면 false가 리턴되는  
	        // isEmpty()  
	        public static boolean isEmpty(int[] array) {  
	            return size(array) == 0;  
	        }  
			  
	        // 1-C. 현재 배열의 특정 인덱스의 값을 리턴하는  
	        // get()  
	        public static int get(int[] array, int index) {  
	            return array[index];  
	        }  
			  
	        // 1-D. 현재 배열에서 특정 값의 가장 먼저 등장하는 인덱스를 찾는  
	        // indexOf()  
	        // 단, 해당 배열에 그 값이 없으면 -1이 리턴된다.  
	        public static int indexOf(int[] array, int element) {  
	            for (int i = 0; i < size(array); i++) {  
	                if (element == get(array, i)) {  
	                    return i;  
	                }  
	            }  
	            return -1;  
	        }  
			  
	        // 1-E. 현재 배열에서 특정 값의 가장 마지막에 등장하는 인덱스를 찾는  
	        // lastIndexOf()  
	        // 단, 해당 배열에 그 값이 없으면 -1이 리턴된다.  
	        public static int lastIndexOf(int[] array, int element) {  
	            for (int i = size(array) - 1; i >= 0; i--) {  
	                if (element == get(array, i)) {  
	                    return i;  
	                }  
	            }  
	            return -1;  
	        }  
			  
	        // 1-F. 현재 배열에서 특정한 값이 존재하면 true, 없으면 false가 나오는  
	        // contains()  
	        public static boolean contains(int[] array, int element) {  
	            return indexOf(array, element) != -1;  
	        }  
			  
	        // 1-G. 현재 배열에 맨 마지막에 새로운 요소를 추가하는  
	        // add()  
	        public static int[] add(int[] array, int element) {  
	            // array보다 길이가 1이 더 큰 새로운 배열을 하나 만들어준다.  
	            int[] temp = new int[size(array) + 1];  
	            // 원본 배열인 array의 값들을 temp에 복사해온다.  
	            for (int i = 0; i < size(array); i++) {  
	                temp[i] = get(array, i);  
	            }  
	            // 새로운 요소인 element를 temp의 가장 마지막 칸에 저장한다.  
	            temp[size(temp) - 1] = element;  
				  
	            // temp를 리턴한다.  
	            return temp;  
	        }  
			  
	        // 1-H. 현재 배열의 특정 인덱스에 새로운 값을 추가하는  
	        // add()  
	        public static int[] add(int[] array, int index, int element) {  
	            // 만약 index가 불가능한 index일 경우,  
	            // 원본 array를 다시 리턴을 한다.  
	            if (index < 0 || index > size(array)) {  
	                return array;  
	            }  
	            int[] temp = new int[0];  
	            for (int i = 0; i < size(array) + 1; i++) {  
	                if (i < index) {  
	                    temp = add(temp, get(array, i));  
	                } else if (i == index) {  
	                    temp = add(temp, element);  
	                } else {  
	                    temp = add(temp, get(array, i - 1));  
	                }  
	            }  
	            return temp;  
	        }  
				  
	        // 1-I. 해당 배열에서 특정 인덱스의 값을 다른 값으로 교체하고  
	        // 원래 있던 값을 리턴하는  
	        // set()  
	        public static int set(int[] array, int index, int element) {  
	            int temp = get(array, index);  
	            array[index] = element;  
				  
	            return temp;  
	        }  
			  
	        // 1-J. 해당 배열의 특정 인덱스를 삭제하는  
	        // remove()  
	        public static int[] remove(int[] array, int index) {  
	            int[] temp = new int[0];  
	            for (int i = 0; i < size(array); i++) {  
	                if (i != index) {  
	                    temp = add(temp, get(array, i));  
	                }  
	            }  
	            return temp;  
	        }  
			
	        // 1-K. 해당 배열의 특정 엘리먼트가 있는 인덱스를 삭제하는  
	        // removeElement()  
	        public static int[] removeElement(int[] array, int element) {  
	            return remove(array, indexOf(array, element));  
	        }  
			  
	        // 2. String[]  
	        // 2-A. size()        public static int size(String[] array) {  
	            return array.length;  
	        }  
			  
	        // 2-B. isEmpty()  
	        public static boolean isEmpty(String[] array) {  
	            return size(array) == 0;  
	        }  
			  
	        // 2-C. get()  
	        public static String get(String[] array, int index) {  
	            return array[index];  
	        }  
			  
	        // 2-D. indexOf()  
	        public static int indexOf(String[] array, String element) {  
	            for (int i = 0; i < size(array); i++) {  
	                if (element.equals(get(array, i))) {  
	                    return i;  
	                }  
	            }  
	            return -1;  
	        }  
			  
	        // 2-E. lastIndexOf()  
	        public static int lastIndexOf(String[] array, String element) {  
	            for (int i = size(array) - 1; i >= 0; i--) {  
	                if (element.equals(get(array, i))) {  
	                    return i;  
	                }  
	            }  
	            return -1;  
	        }  
			  
	        // 2-F. contains()  
	        public static boolean contains(String[] array, String element) {  
	            return indexOf(array, element) != -1;  
	        }  
			  
	        // 2-G. add()  
	        public static String[] add(String[] array, String element) {  
	            String[] temp = new String[size(array) + 1];  
	            for (int i = 0; i < size(array); i++) {  
	                temp[i] = get(array, i);  
	            }  
	            temp[size(temp) - 1] = element;  
	            
	            return temp;  
	        }  
			  
	        // 2-H. add()  
	        public static String[] add
	        (String[] array, int index, String element) {  
	            if (index < 0 || index >= size(array)) {  
	                return array;  
	            }  
	            String[] temp = new String[0];  
	            for (int i = 0; i < size(array) + 1; i++) {  
	                if (i < index) {  
	                    temp = add(temp, get(array, i));  
	                } else if (i == index) {  
	                    temp = add(temp, element);  
	                } else {  
	                    temp = add(temp, get(array, i - 1));  
	                }  
	            }  
	            return temp;  
	        }  
	        
	        // 2-I. set()  
	        public static String set
	        (String[] array, int index, String element) {  
	            String temp = get(array, index);  
	            array[index] = element;  
	            return temp;  
	        }  
	        
	        // 2-J. remove()  
	        public static String[] remove(String[] array, int index) {  
	            String[] temp = new String[0];  
	            for (int i = 0; i < size(array); i++) {  
	                if (i != index) {  
	                    temp = add(temp, get(array, i));  
	                }  
	            }  
				  
	            return temp;  
	        }  
			  
	        // 2-K. remove()  
	        public static String[] remove(String[] array, String element) {  
	            return remove(array, indexOf(array, element));  
	        }  
	    }  
	}
	```
	
- Util_ScannerUtil
	``` java
	package util;  
	  
	import java.util.Scanner;  
	  
	// 스캐너 클래스를 사용할 때  
	// 좀더 간편하게 사용할 수있는 메소드들을 모아둔  
	// 클래스  
	public class ScannerUtil {  
	    // 출력에 사용할 메시지를 받아서  
	    // 예쁘게 출력해줄 메소드  
	    public static void printMessage(String message) {  
	        System.out.println(message);  
	        System.out.print("> ");  
	    }  
	  
	    // 사용자로부터 입력에 사용할 스캐너와 입력에 필요한 메시지를 받아서  
	    // 정수 입력을 처리하여 리턴해주는 메소드  
	    public static int nextInt(Scanner scanner, String message) {  
	        printMessage(message);  
	        return scanner.nextInt();  
	    }  
	  
	    // 사용자가 스캐너, 메시지, 최소값, 최대값을 보내면  
	    // 해당 범위의 정수를 리턴해주는 메소드  
	    public static int nextInt
	    (Scanner scanner, String message, int min, int max) {  
	        int temp = nextInt(scanner, message);  
	        while (!(temp >= min && temp <= max)) {  
	            System.out.println("범위를 벗어난 값입니다.");  
	            temp = nextInt(scanner, message);  
	        }  
	        return temp;  
	    }  
		  
	    // Scanner 버그를 해결한 nextLine()    
	    public static String nextLine(Scanner scanner, String message) {  
	        printMessage(message);  
	        String temp = scanner.nextLine();  
	        if (temp.isEmpty()) {  
	            temp = scanner.nextLine();  
	        }  
			  
	        return temp;  
	    }  
	}
	```
	
- Type_Student
	``` java
	package day0513;  
	  
	import types.Student;  
	  
	/*  
	클래스  
	2세대 언어까지는 프로그램을 기능의 집합으로 보았다.  
	그렇기 때문에 라이브러리 같은 파일들을 만들어서 기능을 따로 관리 하고  
	그리고 struct를 만들어서 데이터를 따로 관리하였다.  
	하지만 객체지향적 관점이 시작되면서 "우리가 왜 이것들을 따로 관리해야지?"  
	라는 관점이 나오게 된다.  
	바로 클래스가 나오게 된 것이다.  
	객체지향 관점에서는 프로그램을 더 작은 프로그램의 집합으로 보았고  
	하나하나의 작은 프로그램들을 우리가 필요로 할 때 변수로 만들어서  
	사용하게 되는 것이다.  
	  
	클래스는 다음과 같은 항목으로 이루어진다.  
	해당 클래스 변수가 저장할 관리할 더 작은 데이터들의 종류(=필드)  
	해당 클래스 변수가 실행 가능한 메소드들  
	  
	static  
	static 키워드는 해당 클래스의 필드 혹은 메소드를  
	클래스 변수 선언과 초기화 없이 직접 사용을 가능하게 만들어주는 키워드이다.  
	하지만, 해당 방법은 클래스 변수 선언을 하지 않게 하므로  
	객체지향에 반하는 행위이다.  
	따라서 앞으로는, 우리가 static 키워드를 사용하는 것을 최소화하도록 한다.  
	특히 static 메소드는 메인 메소드, ScannerUtil 외에서는 사용하지 않는다.  
	  
	생성자(Constructor)  
	생성자란, 해당 클래스 변수가 초기화 될때 호출되는 메소드로써,  
	처음 해당 클래스 변수에 들어갈 외부의 값이나 아니면 초기화 되는 값  
	또는 특정한 작업을 할 때 호출되는 특수한 메소드이다.  
	만약, 우리가 아무런 생성자를 만들어주지 않는 다면  
	자바에서 기본적으로 제공되는 생성자가 호출이 되는데,  
	해당 생성자는 필드의 값울 기본형 데이터타입의 필드는 0으로  
	참조형 데이터타입의 필드는 null로 초기화해준다.  
	생성자의 경우 우리가 따로 만들어 줄 수 있는데,  
	한가지 주의할 점은 우리가 파라미터가 있는 생성자만 만들어주면  
	더 이상 파라미터가 없는 생성자는 호출할 수 없다.  
	만약 파라미터 있는 생성자와 파라미터 없는 생성자 2개가 모두다 필요하면  
	  
	 */public class Ex02Class {  
	    public static void main(String[] args) {  
	        //Student 클래스 변수 선언 및 초기화  
	        Student s1 = new Student();  
	        s1.id = 1;  
	        s1.name = "김철수";  
	        s1.korean = 100;  
	        s1.english = 88;  
	        s1.math = 98;  
	        s1.printInfo();  
			  
	        Student s2 = new Student();  
	        s2.id = 2;  
	        s2.name = "김영희";  
	        s2.korean = 89;  
	        s2.english = 88;  
	        s2.math = 99;  
	        s2.printInfo();  
			   
	        Student s3 = new Student(10, "김준수", 95, 95, 96);  
	        s3.printInfo();  
	  
	        Student s4 = new Student();  
	        s4.id = 2;  
	        s4.name = "김영희";  
	        s4.korean = 89;  
	        s4.english = 88;  
	        s4.math = 99;  
	        System.out.println("s2.equlas(s4) : " + s2.equals(s4));  
	        s4.printInfo();    
	    }  
	}
	```
	
- Type_Writer
	``` java
	package types;  
	  
	public class Writer {  
	    private int number;  
	    private String author;  
	  
	    public Writer(int number, String author) {  
	        this.number = number;  
	        this.author = author;  
	    }  
	  
	    public int getNumber() {  
	        return number;  
	    }  
	  
	    public void setNumber(int number) {  
	        this.number = number;  
	    }  
	  
	    public void write(String name) {  
	        System.out.println(name + "글을 씁니다.");  
	    }  
	  
	    public void read() {  
	        System.out.println
	        ("저는 지금까지 좋아하는 작가인" + author + 
	        "의 글을" + number + "번 읽었어요");  
	    }   
	}
	```
	
+ Interface_IAnimal
	``` java
	package types;  
	/*  
	인터페이스
	
	인터페이스는 참조형 데이터타입의 한가지 종류로써  
	클래스와 매우 유사해보이지만  
	필드가 존재할 수 없고  
	메소드는 '선언"만 한다.  
	즉 "추상"적으로 메소드가 이렇게 생겼지? 만 만들기 때문에  
	그렇게 선언된 메소드들을 우리가 추상 메소드라고도 부른다.  
	  
	실제로 어떠한 필드가 있고 메소드가 어떤 내용을 가져서  
	어떤 코드가 실행될지는 해당 인터페이스를 상속받는 클래스가 직접 구현하게 된다.  
	만약, 인터페이스를 상속 받았는데 인터페이스의 메소드를  
	오버라이드 하지 않으면 에러가 발생된다.  
	  
	즉, 클래스 상속과는 다르게 오버라이드에 대해 강제성을 띄는 상속이 된다.  
	  
	interface 상속은  
	우리가 상속받는 자식 클래스 이름 옆에  
	implements 인터페이스 이름으로 상속을 하게 된다.  
	 */
	 public interface IAnimal {  
	    public void info();  
		  
	    public void move();  
		  
	    public void makeSound();  
	}
	```
	
- Type_Hobby
	``` java
	package types;  
	  
	public class Hobby {  
	    private Writer writer;  
	  
	    public Hobby(Writer writer) {  
	        this.writer = writer;  
	    }  
	  
	    public void method1() {  
	        System.out.println("예제 메소드 1번입니다.");  
	        writer.read();  
	        writer.write("조재영");  
	  
	        System.out.println("예제 메소드 1번 끝\n");  
	    }  
	  
	    public void method2() {  
	        System.out.println("예제 메소드 2번입니다.");  
	        writer.write("조재영");  
	        writer.write("조재영");  
	        System.out.println("예제 메소드 2번 끝\n");  
	    }  
	  
	    public void method3() {  
	        System.out.println("예제 메소드 3번입니다.");  
	        writer.read();  
	        writer.read();  
	        System.out.println("예제 메소드 3번 끝\n");  
	    }  
	}
	```
	
- Type_Dog
	``` java
	package types;  
	  
	// Animal 클래스를 상속받는 자식 클래스 Dogpublic class Dog extends Animal{  
	    public Dog(){  
	        System.out.println("Dog() 호출");  
	    }  
	    // 오버라이드(Override)  
	    // 오버라이드란, 부모 클래스의 메소드를 자식 클래스가 사용하고자 했는데  
	    // 만약 자식 클래스가 재정의가 필요하다면  
	    // 부모 클래스의 메소드를 그대로 선언하고  
	    // 메소드의 내용을 바꾸어서 만들어주는 방법이다.  
	    // 예) public boolean equals(Object obj)  
	  
	    @Override  
	    public void makeSound(){  
	        System.out.println("멍멍");  
	    }  
	}
	```
	
- Type_Cow
	``` java
	package types;  
	  
	public class Cow implements IAnimal {  
	  
	    @Override  
	    public void info() {  
	        System.out.println("소는 맛있습니다.");  
	    }  
	  
	    @Override  
	    public void move() {  
	        System.out.println("소가 움직입니다.");  
	    }  
	  
	    @Override  
	    public void makeSound() {  
	        System.out.println("음메");  
	    }  
	}
	```
	
- Type_Board
	``` java
	package types;  
	  
	public class Board {  
	    private Integer id;  
	    private String name;  
	    private String title;  
	    private String content;  
		  
	    public Board(Integer id, String name, String title, String content) {  
	        this.id = id;  
	        this.name = name;  
	        this.title = title;  
	        this.content = content;  
	    }  
		  
	    public void printList() {  
	        System.out.println("글번호 : " + id);  
	        System.out.println("작성자 : " + name);  
	        System.out.println("작성자 : " + title);  
	        System.out.println("작성자 : " + content);  
	    }  
		  
	    public Board() {  
	        id = -1;  
	        name = "입력없음";  
	        title = "입력없음";  
	        content = "입력없음";  
	    }  
		  
	    @Override  
	    public boolean equals(Object o) {  
	        if (o == this) {  
	            return true;  
	        }  
	        if (o instanceof Board) {  
	            Board b = (Board) o;  
	            return id == b.id;  
	        }  
	        return false;  
	    }  
		  
	    public int getId() {  
	        return id;  
	    }  
		  
	    public void setId(int id) {  
	        this.id = id;  
	    }  
		  
	    public String getName() {  
	        return name;  
	    }  
		  
	    public void setName(String name) {  
	        this.name = name;  
	    }  
		  
	    public String getTitle() {  
	        return title;  
	    }  
		  
	    public void setTitle(String title) {  
	        this.title = title;  
	    }  
		  
	    public String getContent() {  
	        return content;  
	    }  
		
	    public void setContent(String content) {  
	        this.content = content;  
	    }  
	}
	```
	
- Type_Animal
	``` java
	package types;  
	  
	/*  
	상속에서 사용할 최상위 클래스
	*/
	public class Animal {  
	    public void move() {  
	        System.out.println("동물이 움직인다.");  
	    }  
	    
	    public void info() {  
	        System.out.println("동물과 식물의 차이는 세포에 세포벽이 없다 이다.");  
	    }  
		
	    public void makeSound() {  
	        System.out.println("동물이 소리를 낸다.");  
	    }  
		  
	    public Animal() {  
	        System.out.println("Animal() 호출 : ");  
	    }  
	}
	```


##### MVC 2
	
- BoardMain
	```java
	package day0516.java.main;  
  
	import day0516.java.controller.UserController;  
	import day0516.java.viewer.UserViewer;  
	import java.util.Scanner;  
  
	public class BoardMain {  
	    public static void main(String[] args) {  
        // 입력에 사용할 Scanner 클래스 객체  
        Scanner scanner = new Scanner(System.in);  
  
        // 각종 컨트롤러 클래스 객체  
        UserController userController = new UserController();  
  
        // 각종 뷰어 클래스 객체  
        UserViewer userViewer = new UserViewer();  
  
        // setter를 사용한 의존성 주입  
        userViewer.setScanner(scanner);  
        userViewer.setUserController(userController);  
	    }  
	}
	```
	
- StudentMain
	```java
	package day0516.java.main;  
  
	import day0516.java.controller.StudentController;  
	import day0516.java.viewer.StudentViewer;  
  
	public class StudentMain {  
	    public static void main(String[] args) {  
	        StudentController studentController = new StudentController();  
	        StudentViewer studentViewer = 
	        new StudentViewer(studentController);  
	        studentViewer.showMenu();  
	    }  
	}
	```
	
- StudentDTO
	```java
	package day0516.java.model;  
	// 모델  
	// 모델은 사용자가 입력한 값을 자바 객체의 형태로 바꾸거나  
	// 아니면 데이터 베이스로부터 받은 값을 자바 객체의 형태로 바꿀 때  
	// 사용되는 클래스의 종류이다.  
	// 모델 클래스의 경우 이름의 끝에  
	// DTO 혹은 VO 가 붙는데  
	// 각각 Data Transfer Object 혹은 Value Object의 의미를 가진다.  
	// DTO가 좀더 넓은 의미를 가지므로 DTO를 붙이면 왠만해서는 틀리지 않다.  
	  
	// 모델 클래스에는 해당 데이터를 객체화 시킬때 필요한 필드, 겟터/셋터, equals()  
	// 정도의 메소드만 들어간다.  
	  
	import lombok.Data;  
	// lombok은 게터/세터, toString() 등 모델 클래스들에게 필요한  
	// 기본 메소드를 자동으로 생성해주는 외부 라이브러리다.  
	// 필요에 따라서는 우리가 직접 @Getter, @Setter, 등 필요한 것을  
	// 골라서 쓸수도 있지만 @Data 라고 적어주면 모든 기능을 다 활성화시킨다.  
	  
	@Data  
	public class StudentDTO {  
	    private int id;  
	    private String name;  
	    private int korean;  
	    private int english;  
	    private int math;  
		  
	    @Override  
	    public boolean equals(Object o) {  
	        if (this == o) {  
	            return true;  
	        }  
	        if (o instanceof StudentDTO) {  
	            StudentDTO s = (StudentDTO) o;  
	            return id == s.id;  
	        }  
	        return false;  
	    }  
	}
	```
	
- UserDTO
	```java
	package day0516.java.model;  
  
	import lombok.Data;  
	  
	@Data  
	public class UserDTO {  
	    private int id;  
	    private String username;  
	    private String password;  
	    private String nickname;  
	  
	    @Override  
	    public boolean equals(Object o) {  
	        if (this == o) {  
	            return true;  
	        }  
	  
	        if (o instanceof UserDTO) {  
	            UserDTO u = (UserDTO) o;  
	            return id == u.id;  
	        }  
	  
	        return false;  
	    }  
	}
	```
	
- StudentController
	```java
	package day0516.java.controller;  
	// 컨트롤러  
	// 컨트롤러 클래스는 주로 사용자의 요청을 받아서 데이터를 가공하여  
	// 다시 사용자에게 보내주는 역할을 맡는다.  
	  
	// 우리에게 데이터베이스가 있으면 컨트롤러가 데이터베이스로 값을 전송하거나  
	// 전송받은 값을 가공하여 다시 보내주는 역할을 하지만  
	// 우리는 데이터베이스가 없으므로  
	// 어레이리스트를 유사 데이터베이스로 사용하게 된다.  
	  
	import model.StudentDTO;  
	import java.util.ArrayList;  
	  
	public class StudentController {  
	    // 유사 데이터베이스 역할을 할 ArrayList 필드  
	    private ArrayList<StudentDTO> list;  
	    // 다음 입력될 학생의 학생 번호를 저장할 int 필드  
	    private int nextId;  
	  
	    public StudentController() {  
	        list = new ArrayList<>();  
	        nextId = 1;  
	    }  
	  
	    // 1. 사용자로부터 StudentDTO 객체를 전달받아서  
	    //    list에 추가하는 insert()    
	    public void insert(StudentDTO s) {  
	        s.setId(nextId++);  
	        list.add(s);  
	    }  
	  
	    // 2. 현재 리스트 전체를 보내주는  
	    //    selectAll()  
	    public ArrayList<StudentDTO> selectAll() {  
	        return list;  
	    }  
	  
	    // 3. 특정 id값을 가진 StudentDTO 객체를 리턴하는  
	    //    selectOne()  
	    //    단, 해당 id값이 존재하지 않으면 null을 리턴한다.  
	    public StudentDTO selectOne(int id) {  
	        StudentDTO temp = new StudentDTO();  
	        temp.setId(id);  
	  
	        if (list.contains(temp)) {  
	            return list.get(list.indexOf(temp));  
	        }  
	  
	        return null;  
	    }  
	  
	    // 4. 사용자가 보낸 StudentDTO 객체로  
	    //    리스트의 특정 요소를 수정하는  
	    //    update()  
	    public void update(StudentDTO s) {  
	        int index = list.indexOf(s);  
	        list.set(index, s);  
	    }  
	  
	    // 5. 특정 id 값을 가진 객체를  
	    //    list에서 삭제하는  
	    //    delete()  
	    public void delete(int id) {  
	        StudentDTO temp = new StudentDTO();  
	        temp.setId(id);  
	        list.remove(temp);  
	    }  
	  
	    // 6. 파라미터로 들어온 학생 객체의 총점을 계산 하는 메소드  
	    public int calculateSum(StudentDTO s) {  
	        return s.getKorean() + s.getEnglish() + s.getMath();  
	    }  
	  
	    // 7. 파라미터로 들어온 학생 객체의 평균을 계산 하는 메소드  
	    public double calculateAverage(StudentDTO s) {  
	        return (double) calculateSum(s) / 3;  
	    }  
	}
	```
	
- UserController
	```java
	package day0516.java.controller;  
	  
	import model.UserDTO;  
	import java.util.ArrayList;  
	  
	public class UserController {  
	    // 유사 DB 역할을 할 ArrayList 필드  
	    private ArrayList<UserDTO> list;  
	    // 다음 입력될 회원의 번호를 저장할 int 필드  
	    private int nextId;  
		  
	    public UserController() {  
	        list = new ArrayList<>();  
	        nextId = 1;  
	    }  
		  
	    public void insert(UserDTO userDTO) {  
	        userDTO.setId(nextId++);  
	        list.add(userDTO);  
	    }  
	  
	    public boolean validateUsername(String username) {  
	        for (UserDTO u : list) {  
	            if (u.getUsername().equalsIgnoreCase(username)) {  
	                return false;  
	            }  
	        }  
			  
	        return true;  
	    }  
		  
	    public UserDTO selectOne(int id) {  
	        UserDTO temp = new UserDTO();  
	        temp.setId(id);  
	        if (list.contains(temp)) {  
	            return list.get(list.indexOf(temp));  
	        }  
			  
	        return null;  
	    }  
		  
	    public void update(UserDTO userDTO) {  
	        list.set(list.indexOf(userDTO), userDTO);  
	    }  
		  
	    public void delete(int id) {  
	        UserDTO temp = new UserDTO();  
	        temp.setId(id);  
			  
	        list.remove(temp);  
	    }  
		  
	    public UserDTO auth(String username, String password) {  
	        for (UserDTO u : list) {  
	            if (username.equalsIgnoreCase(u.getUsername())) {  
	                if (password.equals(u.getPassword())) {  
	                    return u;  
	                }  
	            }  
	        }  
	        return null;  
	    }  
	}
	```
	
- StudentViewer
	```java
	package day0516.java.viewer;  
	  
	// 실제 사용자가 보게될 UI를 담당할 Viewer
	// 단, 우리가 자바 콘솔에서 화면을 보기 때문에 Viewer 클래스가 있는 것이지  
	// 웹 프로그래밍에서는 웹페이지가 Viewer 가 된다.  
	  
	import day0516.java.controller.StudentController;  
	import model.StudentDTO;  
	import util.ScannerUtil;  
	  
	import java.util.ArrayList;  
	import java.util.Scanner;  
	  
	public class StudentViewer {  
	    private final Scanner SCANNER = new Scanner(System.in);  
	    private StudentController studentController;  
	  
	    public StudentViewer(StudentController studentController) {  
	        this.studentController = studentController;  
	    }  
	  
	    public void showMenu() {  
	        String message = "1. 입력 2. 출력 3. 종료";  
	        while (true) {  
	            int userChoice = ScannerUtil.nextInt(SCANNER, message);  
	            if (userChoice == 1) {  
	                insertStudent();  
	            } else if (userChoice == 2) {  
	                printList();  
	            } else if (userChoice == 3) {  
	                System.out.println("사용해주셔서 감사합니다.");  
	                break;  
	            }  
	        }  
	    }  
		  
	    private void insertStudent() {  
	        StudentDTO s = new StudentDTO();  
			  
	        String message;  
			  
	        message = "학생의 이름을 입력해주세요.";  
	        s.setName(ScannerUtil.nextLine(SCANNER, message));  
			  
	        message = "학생의 국어 점수를 입력해주세요.";  
	        s.setKorean(ScannerUtil.nextInt(SCANNER, message));  
			  
	        message = "학생의 영어 점수를 입력해주세요.";  
	        s.setEnglish(ScannerUtil.nextInt(SCANNER, message));  
			  
	        message = "학생의 수학 점수를 입력해주세요.";  
	        s.setMath(ScannerUtil.nextInt(SCANNER, message));  
			  
	        studentController.insert(s);  
	    }  
		  
	    private void printList() {  
	        ArrayList<StudentDTO> list = studentController.selectAll();  
	        if (list.isEmpty()) {  
	            System.out.println("아직 등록된 학생 정보가 없습니다.");  
	        } else {  
	            briefList(list);  
	            String message = 
	            "상세보기할 학생의 번호나 뒤로 가실려면 0을 입력해주세요.";  
	            int userChoice = ScannerUtil.nextInt(SCANNER, message);  
				  
	            while (!validateValue(userChoice)) {  
	                System.out.println("잘못 입력하셨습니다.");  
	                userChoice = ScannerUtil.nextInt(SCANNER, message);  
	            }  
				  
	            if (userChoice != 0) {  
	                printOne(userChoice);  
	            }  
	        }  
	    }  
		  
	    private void briefList(ArrayList<StudentDTO> list) {  
	        for (StudentDTO s : list) {  
	            System.out.printf("%d. %s\n", s.getId(), s.getName());  
	        }  
	    }  
		  
	    private boolean validateValue(int value) {  
	        if (value == 0) {  
	            return true;  
	        }  
	        return studentController.selectOne(value) != null;  
	    }  
	  
	    private void printOne(int id) {  
	        StudentDTO s = studentController.selectOne(id);  
	        System.out.println("==============================");  
	        System.out.println(s.getName() + " 학생의 정보");  
	        System.out.println("------------------------------");  
	        System.out.printf
	        ("번호: %02d번 이름: %s\n", s.getId(), s.getName());  
	        System.out.printf
	        ("국어: %03d점 영어: %03d점 수학: %03d점\n",  
	        s.getKorean(), s.getEnglish(), s.getMath());  
	        System.out.printf
	        ("총점: %03d점 평균: %06.2f점\n",
	        studentController.calculateSum(s), 
	        studentController.calculateAverage(s));  
	        System.out.println("===============================");  
	        String message = "1. 수정 2. 삭제 3. 뒤로가기";  
	        int userChoice = ScannerUtil.nextInt(SCANNER, message, 1, 3);  
	        if (userChoice == 1) {  
	            update(id);  
	        } else if (userChoice == 2) {  
	            delete(id);  
	        } else if (userChoice == 3) {  
	            printList();  
	        }  
	    }  
		  
	    private void update(int id) {  
	        StudentDTO s = studentController.selectOne(id);  
	        String message;  
			  
	        message = "새로운 이름을 입력해주세요.";  
	        s.setName(ScannerUtil.nextLine(SCANNER, message));  
			  
	        message = "새로운 국어 점수를 입력해주세요.";  
	        s.setKorean(ScannerUtil.nextInt(SCANNER, message));  
			  
	        message = "새로운 영어 점수를 입력해주세요.";  
	        s.setEnglish(ScannerUtil.nextInt(SCANNER, message));  
			  
	        message = "새로운 수학 점수를 입력해주세요.";  
	        s.setMath(ScannerUtil.nextInt(SCANNER, message));  
	        
	        studentController.update(s);  
	        printOne(id);  
	    }  
		
	    private void delete(int id) {  
	        String answer = ScannerUtil.nextLine
	        (SCANNER, "정말로 삭제하시겠습니까? Y/N");  
	        if (answer.equalsIgnoreCase("Y")) {  
	            studentController.delete(id);  
	            printList();  
	        } else {  
	            printOne(id);  
	        }  
	    }  
	}
	```
	
- UserViewer
	```java
	package day0516.java.viewer;  
  
	import day0516.java.controller.UserController;  
	import lombok.Getter;  
	import lombok.Setter;  
	import model.UserDTO;  
	import util.ScannerUtil;  
	  
	import java.util.Scanner;  
	  
	public class UserViewer {  
	    @Setter  
	    private UserController userController;  
	    @Setter  
	    private Scanner scanner;  
	    @Getter  
	    private UserDTO logIn;  
	  
	    public void showIndex() {  
	        String message = "1. 로그인 2. 회원가입 3. 프로그램 종료";  
	        while (true) {  
	            int userChoice = ScannerUtil.nextInt(scanner, message);  
	            if (userChoice == 1) {  
	                auth();  
	                if (logIn != null) {  
	                    // 회원 메뉴 실행  
	                }  
	            } else if (userChoice == 2) {  
	                register();  
	            } else if (userChoice == 3) {  
	                System.out.println("사용해주셔서 감사합니다.");  
	                break;  
	            }  
	        }  
	    }  
	  
	    private void auth() {  
	        String message;  
	        message = "아이디를 입력해주세요.";  
	        String username = ScannerUtil.nextLine(scanner, message);  
	  
	        message = "비밀번호를 입력해주세요.";  
	        String password = ScannerUtil.nextLine(scanner, message);  
	  
	        logIn = userController.auth(username, password);  
	  
	        if (logIn == null) {  
	            System.out.println
	            ("잘못 입력하셨습니다. 로그인 정보를 다시 확인해주세요.");  
	        }  
	    }  
	}
	```
	
- ScannerUtil
	```java
	package day0516.java.util;  
	  
	import java.util.Scanner;  
	  
	// 스캐너 클래스를 사용할 때  
	// 좀더 간편하게 사용할 수있는 메소드들을 모아둔  
	// 클래스  
	public class ScannerUtil {  
	    // 출력에 사용할 메시지를 받아서  
	    // 예쁘게 출력해줄 메소드  
	    private static void printMessage(String message) {  
	        System.out.println(message);  
	        System.out.print("> ");  
	    }  
		  
	    // 사용자로부터 입력에 사용할 스캐너와 입력에 필요한 메시지를 받아서  
	    // 정수 입력을 처리하여 리턴해주는 메소드  
	    public static int nextInt(Scanner scanner, String message) {  
	        String temp = nextLine(scanner, message);  
	        while (!temp.matches("^-?\\d+$")) {  
	            System.out.println("숫자가 아닙니다.\n 다시 입력해주세요.");  
	            temp = nextLine(scanner, message);  
	        }  
			  
	        // String을 int로 바꿀 때에는?  
	        // Integer.parseInt(String) 을 사용하면 된다.  
			  
	        return Integer.parseInt(temp);  
	    }  
		  
	    // 사용자가 스캐너, 메시지, 최소값, 최대값을 보내면  
	    // 해당 범위의 정수를 리턴해주는 메소드  
	    public static int nextInt
	    (Scanner scanner, String message, int min, int max) {  
	        int temp = nextInt(scanner, message);  
	        while (!(temp >= min && temp <= max)) {  
	            System.out.println("범위를 벗어난 값입니다.");  
	            temp = nextInt(scanner, message);  
	        }
	        return temp;  
	    }  
	    // Scanner 버그를 해결한 nextLine() 
	    public static String nextLine(Scanner scanner, String message) {  
	        printMessage(message);  
	        String temp = scanner.nextLine();  
	        if (temp.isEmpty()) {  
	            temp = scanner.nextLine();  
	        }  
	        return temp;  
	    }  
	}
	```
  
### Java란?
- 
### Java의 활용
- 
### Java의 확장
- 