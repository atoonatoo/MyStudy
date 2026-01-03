---
title: throws
type: computer science
director: programing
date: 2025-10-14
tags:
  - programing
  - cs
  - cs_java
---
# 1. 예외 던지기

## 1.1 예외 발생시키기 (throw)

만일 프로그램적으로 에러가 아니라도 로직상 개발자가 일부러 에러를 내서 로그를 기록하고 싶은 상황이 있을 수 있다.

자바에서는 `throw 키워드`를 사용하여 강제로 예외를 발생시킬 수 있다.

원래는 프로그램이 알아서 에러를 탐지하고 처리 하였지만, 이번에는 사용자가 일부러 에러를 throw하여 에러를 catch 한다는 개념으로 이해하면 된다.

이때 `new`라는 생성자로 예외 클래스를 초기화하여 던졌는데, 이 클래스 생성자에 입력 값을 주게되면, catch문의 `grtMessage()` 메서드에서 출력할 메세지를 지정하게 된다.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        try {
            Scanner s = new Scanner(System.in);
            System.out.print("음수를 제외한 숫자만 입력하세요 : ");
            int num = s.nextInt(); // 사용자로부터 정수를 입력 받음
            if (num < 0) {
                // 만일 사용자가 말을 안듣고 음수를 입력하면 강제로 에러를 발생시킨다.
                throw new ArithmeticException("음수가 아닌 양수를 입력하세요 !"); // ArithmeticException 예외 클래스 객체를 생성해 catch문으로 넘겨버린다고 생각하며 된다
            }
            System.out.println("음수를 입력하지 않으셨군요. 감사합니다");
        } catch (ArithmeticException e) {
            System.out.println(e.getMessage());
        } finally {
            System.out.println("프로그램을 종료합니다");
        }
    }
}
```

## 1.2 예외 떠넘기기 (throws)

예외가 발생할 수 있는 코드를 작성할 때 `try-catch` 블록으로 처리하는 것이 기본이지만, 경우에 따라서는 다른 곳에서 예외를 처리하도록 호출한 곳으로 예외를 떠넘길 수도 있다.

이때 사용하는 키워드가 `throws`이다. `throws`는 `메서드 선언부 끝에 작성`되어 메서드에서 예외를 직접 처리(catct)하지 않은 예외를 호출한 곳으로 떠넘기는 역할을 한다.

- 예외를 발생시키는 키워드는 `throw`이며 예외를 메서드에 선언하는 키워드는 `throws`이다.

예시로 다음과 같이 메서드 3개가 있고 각 메서드 마다 예외 처리를 위해 try-catch 블록으로 일일히 감싸주었다.

```java
public class Main {
    public static void main(String[] args) {
        method1();
        method2();
        method3();
    }

    public static void method1() {
        try {
            throw new ClassNotFoundException("에러입니다.");
        } catch (ClassNotFoundException e) {
            System.out.println(e.getMessage());
        }
    }

    public static void method2() {
        try {
            throw new ArithmeticException("에러입니다");
        } catch (ArithmeticException e) {
            System.out.println(e.getMessage());
        }
    }

    public static void method3() {
        try {
            throw new NullPointerException("에러입니다");
        } catch (NullPointerException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

하지만 괜히 코드가 길어지며 가독성도 좋아 보이지 않는 것 같다.

다음과 같이 메서드 선언 코드 오른쪽에 `throws 예외 클래스명`을 기재해주면, 만일 해당 메서드 안에서 예외가 발생할 경우 try-catch 문이 없으면 해당 메서드를 호출한 상위 스택 메서드로 가서 예외 처리를 하게 된다.

```java
void method() throws Exception, Exception2, ... {	
    에러발생코드; // 예외가 발생하면 현 메소드를 호출한 쪽으로 올라간다.
}
```

```java
public class Main {
    public static void main(String[] args) {
        try {
            method1();
            method2();
            method3();
        } catch (ClassNotFoundException | ArithmeticException | NullPointerException e) {
            System.out.println(e.getMessage());
        }
    }

    public static void method1() throws ClassNotFoundException {
        throw new ClassNotFoundException("에러 발생");
    }

    public static void method2() throws ArithmeticException {
        throw new ArithmeticException("에러 발생");
    }

    public static void method3() throws NullPointerException {
        throw new NullPointerException("에러 발생");
    }
}
```

![[Pasted image 20251031150231.png]]

즉, 예외 클래스를 메서드의 `throws`에 명시하는 것은 이곳에서 예외를 처리하는 것이 아니라 자신을 호출한 메서드에게 예외를 전달하여 **예외 처리를 떠맡기는 것**이다. 또한 예외를 전달받은 메서드가 또 다시 자신을 호출할 메서드에게 전달할 수 있다. 이런 식으로 계속 호출 스택에 있는 메서드들을 따라 전달되다가, 제일 마지막에 있는 main 메서드에서 `throws`를 사용하면 가상머신에서 처리된다.

## 1.3 예외 발생과 코드의 트랜잭션

트랜잭션(Transaction)은 하나의 작업 단위를 뜻한다.

작, 자바 코드에서 메서드 블럭 내의 코드들이 **예외가 발생해도 모두 실행**되는냐 아니면 **예외가 발생하면 그 상태로 중지** 하느냐의 작업 단위를 개발자가 어떠한 형태의 예외 처리 방법을 사용하느냐에 따라 달라지게 된다.

예시로 각 메서드에서 일일히 try-catch를 한다면, 메인 메서드에 있는 메서드 실행 코드 부분이 3개 모두 실행 자체는 된다. 왜냐하면 예외처리를 각 메서드에서 하기 때문에 상위의 메인 메서드의 코드들은 모두 실행되게 된다.

![[Pasted image 20251031150724.png]]

반면에 `throws`를 상위 메서드에서 모아 처리를 한다면, 코드 어느 한 곳에서 예외가 발생하면 바로 catch로 점프하기 때문에 그 뒤의 나머지 코드들은 당연히 실행되지 않게 된다.

![[Pasted image 20251031152736.png]]

이처럼 try-catch 문은 어디에 사용하냐 어디서 throws 하느냐에 따라 자바 코드의 작업 단위(트랜잭션)가 완전히 달라질 수 있게 되는 것이다. 따라서 자신의 프로젝트에 따라 적절한 예외 처리 로직을 짜 주어야 하는 방향으로 나아가야 한다. 

---
# 2. 연결된 예외 (Chained Exception)

## 2.1 예외를 다른 예외로 감싸 던지기

연결된 예외(chained exceptio)는 한 예외가 다른 예외를 발생시킬 수 있는 기능이다. 우리가 클래스를 상속하여 다형성을 이용하여 부모 클래스 타입으로 다뤄온 것 처럼, 예외도 마치 부모 예외로 감싸서 보내 마치 `예외의 다형성 처럼 다룰 수`있다. 

예시로 예외 A가 발생했다면 이를 예외 B로 감싸서 throw하는 식으로, 마치 예외를 다른 예외로 감싸숴 던진다고 보면된다. 그래서 예외 A가 예외 B를 발생시켰다면, A를 B의 `원인 예외(cause exception)`라고 한다.

Exception 클래스가 상속하고 있는 Throwable 클래스에는 `getMessage()`, `printStackTrace()` 이외에도 chained exception을 가능하게 해주는 다음 메서드를 지원한다. 

- `Throwable initCause (Throwable cause)` : 지정한 예외를 원인 예외로 등록
- `Throwable getCauseO()` : 원인 예외를 반환

이 메서드를 이용해서 예외를 다른 예외로 포장해 던질 수 있게 된다.

당연히 Exception 클래스의 부모인 Throwable 클래스에 정의되어있기 때문에 모든 예외에서 사용 가능하다.

```java
class InstallException extends Exception { ... }
class SpaceException extends Exception { ... }
class MemoryException extends Exception { ... }

public class Main {
    public static void main(String[] args) {
        try {
            install();
        } catch (InstallException e) {
            System.out.println("원인 예외 : " + e.getCause()); // 원인 예외 출력
            e.printStackTrace();
        }
    }

    public static void install() throws InstallException {
        try {
            throw new SpaceException("설치할 공간이 부족합니다."); // SpaceException 발생

        } catch (SpaceException e) {
            InstallException ie = new InstallException("설치중 예외발생"); // 예외 생성
            ie.initCause(e); // InstallException의 원인 예외를 SpaceException으로 지정
            throw ie; // InstallException을 발생시켜 상위 메서드로 throws 된다.
        } catch (MemoryException e) {
            // ...
        }
    }
}
```

1. startInstall() 메서드에서 SpaceException 이라는 예외가 발생
2. catch 문에서 InstallException 예외 클래스를 새로 생성
3. 그리고 InstallException 객체의 메서드 `initCause()`를 이용해 SpaceException 타입의 객체를 넣어 실행
4. 그러면 SpaceException 예외는 InstallException 예외에 포함되게 된다. (원인 예외)
5. InstallException 예외 객체를 밖으로 throws한다.
6. 메인 메서드에서 InstallException 예외를 catch하고 `getCause()` 메서드를 통해 원인 예외 로그를 출력한다.

![[Pasted image 20251031153827.png]]

발생한 예외를 그대로 처리하면 되는 걸, 왜 굳이 원인 예외로 포장해서 다른 예외로 던지는 이유는, 여러가지 예외를 하나의 큰 분류의 예외로 묶어서 다루기 위해서다. 위에서 언급했던 것 처럼 `다형성 예외 버전`이라고 이해해도 좋다.

그리고 처음 부터 명확한 에러 정보를 주는 것보다는 단계별로 어떠한 원인의 에러에 의해서 에러가 났다는 정보를 주는 것이 더 좋기 때문이다. 예를 들어 위의 코드 처럼, 단순히 `설치 공간이 부족합니다.`라는 에러만 띄우면 어떠한 원인 동작으로 인해 갑자기 공간이 부족하는지 추적을 못하기 때문에, 예뢰를 감싸서 `설치 중에 -> 설치할 공간이 부족해 예외 발생` 이런 식으로 추적이 용이하기 때문이다. 

## 2.2 Checked 예외를 Unchecked 예외로 변환

연결된 예외(chained exceptio)를 사용하는 또 다른 이유는 checked 예외를 unchecked 예외로 바꿀 수 있도록 하기 위함이다.

예시로 checked exception의 종류의 예외를 포함한 코드를 작성하면 컴파일러가 예외처리(try-catch)를 강제한다.

가장 대표적인 예로 FileWriter 클래스를 이용해 파일을 불러오는 코드를 작성하면 반드시 try-catch로 감싸주어야 컴파일이 된다.

![[Pasted image 20251031154304.png]]

이런 식으로 설계한 이유는, 처음 자바 언어를 개발 했을 때 프로그래밍 경험이 적은 사람도 보다 견고한 프로그램을 작성할 수 있도록 유도하기 위해서 인데, 실제로 별것 아닌 예외도 checked exception으로 등록한 것이 꽤 많다.

자바 프로그래밍 언어가 처음 개발되던 1990년대와 지금의 컴퓨터 환경은 많이 달라졌기 때문에, 실제로 런타임 예외로 처리해도 될 것들이 아직도 check exception으로 등록되어 강제적으로 try-catch 문을 사용해야 하는 불편함이 있고, 또한 로직상 Runtime Exception으로 할 수 밖에 없는 경우가 있기 때문에, 추가된 기법이라고 생각하면 된다.

따라서 연결된 예외(chained exception)을 이용해, checked 예외를 unchecked 예외로 바꾸면 예외처리가 선택적이 되므로 억지로 거추장스러운 예외 처리를 하지 않아도 된다.

```java
class MyCheckedException extends Exception { ... } // checked excpetion

public class Main {
    public static void main(String[] args) {
            install();
    }

    public static void install() {
        throw new RuntimeException(new IOException("설치할 공간이 부족합니다."));
        // Checked 예외인 IOException을 Unchecked 예외인 RuntimeException으로 감싸 Unchecked 예외로 변신 시킨다
    }
}

```

---
# 99. 참고 문헌
- [참고 문헌](https://bvc12.tistory.com/19)
- [참고 문헌](https://www.youtube.com/watch?v=I4XrVgCzKM4)
- [참고 문헌](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%98%88%EC%99%B8-%EB%8D%98%EC%A7%80%EA%B8%B0throw-%EC%98%88%EC%99%B8-%EC%97%B0%EA%B2%B0Chained-Exception)
