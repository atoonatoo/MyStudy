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

반면에 `throws`를 

---
# 2. 연결된 예외 (Chained Exception)

## 2.1 예외를 다른 예외로 감싸 던지기

## 2.2 Checked 예외를 Unchecked 예외로 변환


---
# 99. 참고 문헌
- [참고 문헌](https://bvc12.tistory.com/196)
- [참고 문헌](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%98%88%EC%99%B8-%EB%8D%98%EC%A7%80%EA%B8%B0throw-%EC%98%88%EC%99%B8-%EC%97%B0%EA%B2%B0Chained-Exception)
