---
created:
---
---
# **README**

- Stringbulid의 주요 기능은 글자를 계속 더하거나 바꿀 수 있는 도구
- StringBuilder는 **자바 표준 라이브러리**에 포함된 클래스이다.
- 자바 기본 패키지에 추가 되어 있기 떄문에 별도로 추가 설피가 필요없다.
  
- 예제 코드
```java
// String 사용
String str = "Hello";
str = str + " World"; // 새로운 문자열을 만들고 str에 할당
System.out.println(str); // "Hello World"

// StringBuilder 사용
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World"); // 같은 객체에 " World"를 추가
System.out.println(sb.toString()); // "Hello World"

// `String`은 매번 새로운 문장을 만들면 새 객체가 생성됩니다.
// `StringBuilder`는 처음 만든 객체에 계속 추가할 수 있어 더 빠르고 효율적입니다.
// 이처럼 `StringBuilder`는 글자를 자주 추가하거나 바꿀 때 유용하게 쓰입니다.
```
### 주요 기능

- **append()** - 문자열 추가
```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb.toString()); // "Hello World"
```

- insert() - 특정 위치에 문자열 삽입
```java
StringBuilder sb = new StringBuilder("Hello World");
sb.insert(5, " Java");
System.out.println(sb.toString()); // "Hello Java World"
```

- replace() - 문자열의 일부를 변경
```java
StringBuilder sb = new StringBuilder("Hello World");
sb.replace(6, 11, "Java");
System.out.println(sb.toString()); // "Hello Java"
```

- **delete()** - 문자열의 일부 삭제
```java
StringBuilder sb = new StringBuilder("Hello World");
sb.delete(5, 11);
System.out.println(sb.toString()); // "Hello"
```

- **reverse()** - 문자열 뒤집기
```java
StringBuilder sb = new StringBuilder("Hello");
sb.reverse();
System.out.println(sb.toString()); // "olleH"
```

- **length()** - 문자열 길이 반환
```java
StringBuilder sb = new StringBuilder("Hello");
System.out.println(sb.length()); // 5
```

- **charAt()** - 특정 위치의 문자 반환
```java
StringBuilder sb = new StringBuilder("Hello");
System.out.println(sb.charAt(1)); // 'e'
```

- **setCharAt()** - 특정 위치의 문자 변경
```java
StringBuilder sb = new StringBuilder("Hello");
sb.setCharAt(1, 'a');
System.out.println(sb.toString()); // "Hallo"
```
  
  
  
