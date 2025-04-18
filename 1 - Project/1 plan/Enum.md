
---
- [[CS]]
---
### 1. 정의
enum은 열거형이다. 
자바에서 상수의 집합을 정의할 때 사용하는 특별한 데이터 타입이다. enum을 사용하면 변수에 가질 수 있는 값들을 미리 정의할 수 있다.

---

### 2. 어떤 상황에 사용하면 좋은가?

- 고정된 집합의 값을 다룰 때 사용
예를 들어, 요일, 월, 방향, 상태 코드 등과 같이 변하지 않는 값들을 처리할 때 유용하다.

- 조건 분기를 단순화하고 싶을 때 사용
switch문과 함께 사용하면 코드가 간결해지고 가독성이 좋아진다.

- 상수 값을 그룹화하고 싶을 때 사용한다. 
관련된 상수들을 하나의 enum 안에 묶어서 관리할 수 있다.

---

### 3. 특징

- 상수 집합을 다룬다. 

- enum은 미리 정의된 값들만 가질 수 있다.
- 객체지향적 특성을 갖는다. 
- enum은 클래스처럼 메서드, 필드, 생성자를 가질 수 있다.
- 타입 안전성을 제공한다. 
- 잘못된 값이 할당되지 않도록 제한한다.

---

### 4. 사용 방법

- enum은 enum 키워드를 사용하여 정의한다. 
예시로 요일을 나타내는 enum을 정의할 수 있다.

``` java
public enum Day {
    MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
}
```

enum을 사용할 때는 Day.MONDAY, Day.FRIDAY와 같이 상수 값을 사용한다.

---

### 5. 추가적인 정보

- enum은 내부적으로 java.lang.Enum 클래스를 확장한다. 
따라서 ordinal(), name() 등의 메서드를 기본적으로 사용할 수 있다.

- enum 값들은 싱글턴 패턴으로 관리된다. 
즉, 각 enum 상수는 하나의 인스턴스만 존재한다.

- enum은 비교 시 == 연산자를 사용한다. 이는 정수형 상수 비교와는 다르게 값 자체를 비교한다.

---

### 6. 장점

- 타입 안전성을 제공한다. 
- 잘못된 값이 할당될 위험을 줄여준다.
- 가독성이 향상된다. 
- 상수값을 직관적인 이름으로 사용할 수 있어 코드가 더 이해하기 쉬워진다.
- 코드 유지보수가 용이하다. 
- 관련된 상수들을 한 곳에 묶어 관리할 수 있어 코드 수정이 쉬워진다.
확장이 용이하다. 
- enum은 메서드와 필드를 가질 수 있어 기능을 추가할 수 있다.

---

### 7. 단점

- 초기화 시 고정된 값만 사용할 수 있다. 
- enum에 값을 동적으로 추가할 수 없어서 변경이 필요할 때 불편할 수 있다.
- 복잡한 비즈니스 로직에는 부적합할 수 있다. 
- enum은 상수 값에 해당하는 것만 다루므로 기능이 복잡한 로직에는 다른 방식이 더 적합할 수 있다.
- 상속이 불가능하다. 
- enum은 java.lang.Enum을 상속하기 때문에 다른 클래스를 상속할 수 없다.

---

### 8. 주의사항

- 상수 이름을 변경하면 안 된다. 
코드에서 사용하는 값에 영향을 미치므로 이름을 변경하는 것은 위험하다.

- 외부 값과 비교 시 주의해야 한다. 
enum 값은 == 연산자로 비교하는 것이 안전하다. equals()를 사용할 경우 의도치 않은 비교가 발생할 수 있다.

- 메모리 사용에 주의해야 한다. 
enum은 각 값에 대해 인스턴스를 하나씩 생성하므로, 너무 많은 값을 정의하면 메모리 사용량이 증가할 수 있다.