---
created: 2024-01-04
updated: 2024-09-19
---
----
##### 연결 문서

- 
- 
- 
---

# **README**

- 정적 팩토리 메서드는 [[ATNT/1 - Project/CS (Computer Science)/E list/Design Pattern|Design Pattern]]의 생성패턴이다.
- 객체 생성의 역할을 하는 클래스 메서드이다.

##### 정적 팩토리 메서드 문법

```java
public class MyClass {
    private String name;

    // private 생성자: 외부에서 직접 생성자 호출을 막음
    private MyClass(String name) {
        this.name = name;
    }

    // 정적 팩토리 메서드
    public static MyClass createInstance(String name) {
        return new MyClass(name);
    }
}
```

##### 생성자와 정적 팩토리 메서드의 차이

- 정적 팩토리 메서드는 이름을 가질 수 있다.
	- 객체는 생성 목적과 과정에 따라 생성자를 구별해 사용할 필요성이 있다.
	- new 라는 키워드를 통해 객체를 생성하는 생성자는 내부 구조를 잘 알고 있기 때문에 목적에 맞게 객체를 생성할 수 있다.
	- 하지만 정적 팩토리 메서드를 사용하면 메서드 이름에 객체의 생성 목적을 담아 낼 수 있다. 

- 예제 코드
```java
public class LottoFactory() {
  private static final int LOTTO_SIZE = 6;

  private static List<LottoNumber> allLottoNumbers = ...; // 1~45까지의 로또 넘버

  public static Lotto createAutoLotto() {
    Collections.shuffle(allLottoNumbers);
    return new Lotto(allLottoNumbers.stream()
            .limit(LOTTO_SIZE)
            .collect(Collectors.toList()));
  }

  public static Lotto createManualLotto(List<LottoNumber> lottoNumbers) {
    return new Lotto(lottoNumbers);
  }
  ...
}
```

- 설명 
	두 메서드 모두 로또 객체를 생성하고 반환하는 정적 팩토리 메서드이다.
	메서드의 이름만 보아도 수동과 자동으로 생성하는지 단번에 이해할 수있다.
	이처럼 정적 팩토리 메서드를 사용하면 해당 생성의 목적을 이름을 통해 표현할 수 있어 가독성이 좋아진다.

##### 호출할 때마다 새로운 객체를 생성할 필요가 없다.

- enum과 같이 자주 사용되는 요소의 개수가 정해져있다면, 해당 개수만큼
미리 생성해놓고 조회(캐싱)할 수 있는 구조로 만들 수 있다.
- 정적 팩토리 메서드와 캐싱 구조를 함께 사용하면 매번 새로운 객체를 생성할 필요가 없어진다.

```java
public class LottoNumber {
  private static final int MIN_LOTTO_NUMBER = 1;
  private static final int MAX_LOTTO_NUMBER = 45;

	  private static Map<Integer, LottoNumber> lottoNumberCache = new HashMap<>();

  static {
    IntStream.range(MIN_LOTTO_NUMBER, MAX_LOTTO_NUMBER)
                .forEach(i -> lottoNumberCache.put(i, new LottoNumber(i)));
  }

  private int number;

  private LottoNumber(int number) {
    this.number = number;
  }

  public LottoNumber of(int number) {  // LottoNumber를 반환하는 정적 팩토리 메서드
    return lottoNumberCache.get(number);
  }

  ...
}
```

##### 하위 자료형 객체를 반환할 수 있다.

- 하위자료형 객체를 반환하는 정적 팩토리 메서드의 특징은 상속을 사용할 때 확인할 수 있다.
- 이는 생성자의 역할을 하는 정적 팩토리 메서드가 반환 값을 가지고 있기 때문에 가능한 특징이다.
- Basic, Intermediate, Advanced 클래스가 level 라는 상위 타입을 상속받고 있는 구조를 생각해보자, 시험 점수에 따라 결정되는 하위 등급 타입을 반환하는 정적 팩토리 메서드를 만들면, 다음과 같이 분기처리를 통해 하위 타입의 객체를 반환할 수 있다.

```java
public class Level {
  ...
  public static Level of(int score) {
    if (score < 50) {
      return new Basic();
    } else if (score < 80) {
      return new Intermediate();
    } else {
      return new Advanced();
    }
  }
  ...
}
```

##### 객체 생성을 캡슐화할 수 있다.

- 정적 팩토리 메서드는 객체 생성을 캡슐화하는 방법이기도 하다.

- 웹 어플리케이션을 개발하다보면 계층 간에 데이터를 전송하기 위한 객체로 DTO를 정의해서 사용한다.
- DTO와 Entity간에는 자유롭게 형 변환이 가능해야 하는데. 정적 팩토리 메서드를 사용하면 내부 구현을 모르더라도 쉽게 변환할 수 있다.

```java
public class CarDto {
  private String name;
  private int position;

  pulbic static CarDto from(Car car) {
    return new CarDto(car.getName(), car.getPosition());
  }
}

// Car -> CatDto 로 변환
CarDto carDto = CarDto.from(car);
```

- 만약 정잭 팩토리 메서드를 쓰지 않고 DTO로 변환한다면 외부에서 생성자의 내구현을 모두 드러낸 채 해야할 것이다.

```java
Car carDto = CarDto.from(car); // 정적 팩토리 메서드를 쓴 경우
CarDto carDto = new CarDto(car.getName(), car.getPosition); // 생성자를 쓴 경우
```

##### 정적 팩토리 메서드 네이밍 컨벤션

- `from` : 하나의 매개 변수를 받아서 객체를 생성
- `of` : 여러개의 매개 변수를 받아서 객체를 생성
- `getInstance` | `instance` : 인스턴스를 생성. 이전에 반환했던 것과 같을 수 있음.
- `newInstance` | `create` : 새로운 인스턴스를 생성
- `get[OtherType]` : 다른 타입의 인스턴스를 생성. 이전에 반환했던 것과 같을 수 있음.
- `new[OtherType]` : 다른 타입의 새로운 인스턴스를 생성.