### 1. 프로그램 구조

#### 클래스와 메인 메서드

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```
- class -  클래스 정의.
- main -  프로그램의 시작점.

---

### 2. 데이터 타입

#### 기본 데이터 타입

| 데이터 타입 | 크기    | 예시                          |
|-------------|---------|-------------------------------|
| byte        | 1 byte  | byte a = 10;                  |
| short       | 2 bytes | short b = 20;                 |
| int         | 4 bytes | int c = 30;                   |
| long        | 8 bytes | long d = 40L;                 |
| float       | 4 bytes | float e = 3.14F;              |
| double      | 8 bytes | double f = 3.14;              |
| char        | 2 bytes | char g = 'A';                 |
| boolean     | 1 bit   | boolean h = true;             |

- 참조 데이터 타입
	- 클래스, 배열, 인터페이스 등.
    
---

### 3. 변수와 상수

- 변수 선언
```java
int age = 25;
String name = "John";
```
- 상수 선언
```java
final double PI = 3.14;
```
---

### 4. 연산자

#### 산술 연산자
| 연산자 | 설명   | 예시     |
|--------|--------|----------|
| +      | 더하기 | a + b    |
| -      | 빼기   | a - b    |
| *      | 곱하기 | a * b    |
| /      | 나누기 | a / b    |
| %      | 나머지 연산 | a % b  |

#### 비교 연산자
| 연산자 | 설명   | 예시     |
|--------|--------|----------|
| ==     | 값이 같은가? | a == b  |
| !=     | 값이 다른가? | a != b  |
| >      | 크다   | a > b    |
| <      | 작다   | a < b    |

#### 논리 연산자
| 연산자 | 설명   | 예시     |
|--------|--------|----------|
| &&     | 논리 AND | a > 10 && b < 20 |
| `      |         | `        |
| !      | 논리 NOT | !true    |

---

### 5. 조건문

- if-else

```java
if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}
```

- switch

```java
int day = 2;
switch(day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Other day");
}
```

---

### 6. 반복문

- for
```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

- while
```java
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}
```

- do-while
```java
int i = 0;
do {
    System.out.println(i);
    i++;
} while (i < 5);
```

---

### 7. 배열

- 1차원 배열
```java
int[] numbers = {1, 2, 3, 4, 5};
System.out.println(numbers[0]); // 1
```

- 2차원 배열
```java
int[][] matrix = {{1, 2}, {3, 4}};
System.out.println(matrix[1][1]); // 4
```

---

### 8. 메서드

- 메서드 정의와 호출

```java
public static int add(int a, int b) {
    return a + b;
}

public static void main(String[] args) {
    int result = add(5, 3);
    System.out.println(result); // 8
}

```

---

### 9. 객체와 클래스

```java
class Person {
    String name;
    int age;

    void introduce() {
        System.out.println("Hi, I'm " + name);
    }
}
```
- 객체 생성
```java
Person person = new Person();
person.name = "John";
person.age = 25;
person.introduce();
```
---
### 10. 상속
- 상속 기본
```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
```
- 사용
```java
Dog dog = new Dog();
dog.sound(); // Dog barks
```

---
### 11. 예외처리
- try-catch
```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

- finally
```java
finally {
    System.out.println("Always executed");
}
```
---
### 12. 접근제어자

| 제어자     | 같은 클래스 | 같은 패키지 | 자식 클래스 | 모든 클래스 |
|------------|-------------|-------------|-------------|-------------|
| public     | O           | O           | O           | O           |
| protected  | O           | O           | O           | X           |
| default    | O           | O           | X           | X           |
| private    | O           | X           | X           | X           |

---
### 13. 기본 클래스 라이브러리

- 문자열
```java
String text = "Hello";
System.out.println(text.length());
System.out.println(text.toUpperCase());
```

- ArrayList
```java
import java.util.ArrayList;

ArrayList<String> list = new ArrayList<>();
list.add("Apple");
list.add("Banana");
System.out.println(list.get(0));
```
