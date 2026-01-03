---
title: InputStreamReader
type: computer science
director: programing
date: 2025-10-14
tags:
  - programing
  - cs
  - cs_java
---
#  1. InputStreamReader은 왜 필요한가?

- InputStream / OutputStream 은 자바에서 가장 기본이 되는 입 / 출력 스트림이다.
- Stream이란 출발지와 도착지를 이어주는 다리이다.

그렇다면 어떠한 용도로 사용되는지 알아보자.

컴퓨터는 모든 걸 숫자(0, 1)로 즉 바이트로 다룬다.  사람이 키보드로 입력을 해도 컴퓨터는 아래와 같이 이해한다.

```
a -> 97
b -> 98
c -> 99
```

이게 ASCII 코드 값이다.

그래서 `InputStream`으로 읽으면 컴퓨터는 숫자만 보여준다.

```java
InputStream in = System.in;
int data = in.read();
System.out.println(data);
```

키보드에 `a`를 입력하면 `97`이라는 숫자로 출력이 된다. 
즉, 우리가 입력한 문자를 그대로 볼 수가 없다는 문제가 생긴다.

이 문제를 해결해주는 것이 바로 `InputStreamReader`이다.

이 클래스는 이름 그대로 InputStream을 읽어서(Reader)
`바이트` -> `문자(char)`로 변환 해주는 역할을 한다. 

정리하자면

`컴퓨터가 이해하는 숫자 데이터를 사람이 읽는 문자 데이터로 통역해주는 역할`이다.

## 1.1 InputStreamReader을 이용해 입력을 받는 코드

```java
import java.io.InputStream; 
import java.io.InputStreamReader; 
public class StreamTest { public static void main(String[] args) throws Exception { 
InputStream in = System.in; 
InputStreamReader reader = new InputStreamReader(in); // (1)
char[] a = new char[3]; // 배열의 크기가 3인 배열 a 선언 
reader.read(a); // (2)

System.out.println(a); } }
```

- (1) 주어진 입력 바이트 스트림 in에 대해 기본 인코딩을 사용하는 객체를 생성한다.
    - InputStreamReader reader = new InputStreamReader(in);

- (2) byte 배열대신에 char 배열로 데이터를 받을 수 있다.
    - Char[] a = new char[3];
    - reader.read(a);

이 방법은 InputStream에서 많이 개선되었지만, 여전히 고정된 길이로만 읽어야 한다는 불편한 점이 있다.

그렇다면 사용자가 엔터키를 입력할 때까지 사용자의 입력을 전부 받아들일 수 있는 방법은 없는 걸까?

이전 포스팅에서 다룬 `BufferReader` 클래스로 해결할 수 있다.

자세한 내용은 아래의 링크를 참고 바란다.

- [BufferedReader & BufferedWriter & StringBuilder](https://velog.io/@atoonatoo/BufferedReader-BufferedWriter-StringBuilder)

---

# 2.  OutputStreamWriter

마찬가지로 OutputStreamWriter의 용도를 알아보자.

컴퓨터는 데이터를 `byte`로 처리하지만, 우리는 출력할 때 `문자(String)`를 다룬다. 

예를 들어 "안녕"이라는 문장은 사용자가 보기엔 글자지만, 컴퓨터 내부적으로는 아래와 같이 저장된다.
```
안 -> EAB0 00xx
녕 -> EAB0 00yy (UTF-8 인코딩)
```

즉, 글자를 출력하려면 문자 -> 바이트 변환이 필요하다.

이 변환을 해주는 것이 `OutputStreamWriter`이다.

우리가 사용해봤던 `System.out` 같은 바이트 기반 스트림에 문자 데이터를 쓸 수 있게 해주는 클래스이다.

- 예시 코드
```java
import java.io.*;

public class Main {
    public static void main(String[] args) throws IOException {
        OutputStreamWriter writer = new OutputStreamWriter(System.out);
        writer.write("Hello World!\n");  // 문자 데이터를 바이트로 변환해 출력
        writer.flush(); // 버퍼 비워서 실제로 출력되게 함
    }
}

```

- 출력 결과
```
Hello World!
```

---

# 99.  참고 문헌

- [참고 문헌](https://silverji.tistory.com/36)
- [참고 문헌](https://sy99.tistory.com/20)





