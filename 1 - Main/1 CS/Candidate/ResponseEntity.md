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
 
### ResponseEntity를 사용하는 이유

#### HTTP의 응답을 제어하기 위해

- 일반적인 Controller를 사용하는 MVC 방식은 HTTP 상태 코드를 제어 할 수 없다.
- 비록 실제로 리소스가 없거나 에러가 발생했음에도 특별한 처리를 하지 않으면 200 OK로 응답될 수 있다. 
  이로 인해 실제 서버 상태를 정확하게 전달하지 못하는 한계가 발생한다.

-  **ResponseEntity 사용 이전 예제 코드

```java
@GetMapping("/user/{id}")
public User getUser(@PathVariable Long id) {
    User user = userService.findById(id);
    return user; // 리소스를 찾지 못해도 200 OK 상태 코드 반환
}
```

-  **ResponseEntity 사용 코드 이전 예제 코드

```java 
@GetMapping("/user/{id}")
public ResponseEntity<User> getUser(@PathVariable Long id) {
    User user = userService.findById(id);
    if (user == null) {
        return new ResponseEntity<>(HttpStatus.NOT_FOUND); // 404 Not Found 반환
    }
    return new ResponseEntity<>(user, HttpStatus.OK); // 리소스가 있으면 200 OK 반환
}
```

##### ResponseEntity를 잘 사용하는 방법

###### **Return은 생성자보다는 빌더 패턴 사용

```java
// 생성자
return new ResponseEntity(body, headers, HttpStatus.valueOf(200));

// 빌더 패턴
return ResponseEntity.ok() 
.headers(headers) 
.body(body);
```

-  **이유
	- 주된 이유는 코드의 **가독성**과 **유연성**
	- ResponseEntity.ok()는 [[Static Factory Method]]이다.


- **가독성과 유지보수성
	- 생성자는 인자를 받지만 이 인자가 어떤 목적으로 사용되는지 명확하지 않을 수 있다.
	- 특히 응답 헤더, 본문, 상태 코드 등을 함께 처리하는 경우 생성자 방식은 코드 가독성을 헤친다.

```java
// 생성자 방식 (가독성이 떨어질 수 있음)
return new ResponseEntity<>(user, HttpStatus.OK);

// 빌더 패턴 (가독성이 향상됨) 
return ResponseEntity.ok() .body(user);
```

- **유연성
	- 빌더 패턴을 사용하면 응답을 좀 더 쉽게 구성할 수 있다.
	- 특히 응답 헤더나 추가적인 설명이 필요한 경우, 빌더 패턴을 사용하면 각 요소를 유연하게 조합할 수 있다.

```java
// 생성자 방식 (가독성이 떨어지고 유연성이 낮음)
HttpHeaders headers = new HttpHeaders();
headers.set("Custom-Header", "value");
return new ResponseEntity<>(user, headers, HttpStatus.OK);

// 빌더 패턴 (더 유연하고 가독성 높음)
return ResponseEntity.ok()
        .header("Custom-Header", "value")
        .body(user);
```

- **확장성
	- 빌더 패턴은 여러 메서드를 체인 방식으로 호출하여 코드 확장성에 용이하다.
	- 필요에 따라 쉽게 새로운 요소를 추가하거나 응답 형식을 변경할 수 있다.

###### ResponseEntity의 Body 타입을 명시하라

```java
public ResposneEntity getUser() { }
// 위와 같이 메서드를 작성하면 ResponseEntity의 타입을 작성하지 않은 것이라 Object(모든 자바의 부모 클래스)를 Return으로 받는다.

// 위의 코드는 아래의 코드와 기능적으로 의미가 같다.
public ResposneEntity<Object> getUser() { }
```

- ResposneEntity의 타입은 명시하지 않으면 Object 타입을 Return 해준다.
- 다만 대부분 상황에서는 유지보수를 위해 타입을 명시해 주는 것이 직관적이므로 좋다.

##### 타입을 여러 개 받고 싶다면 Return 타입은 Object 대신  [[와일드카드]] 사용

- 반환 타입이 명확하지 않아도 Return 된다.

```java
public ResponseEntity<Object> getUsers() {
    List<User> users = userService.getUsers();
    return ResponseEntity.ok(users);

public ResponseEntity<?> getUsers() {
    List<User> users = userService.getUsers();
    return ResponseEntity.ok(users);
}
}
```

- 보통 타입을 여러개 받고 싶은 경우 아래와 같이 Object나 와일드카드를 사용할 수 있다.

- 둘 모두 사용 가능하지만 Return 할 때 타입이 명확하지 않을 때는 Object 보다 와일드 카드를 사용하는 것이 좋다.

- 그래서 와일드카드가 아닌 타입 파라미터를 사용한다면 컴파일 타임에 자동 형변환이 되므로 개발자는 따로 형변환을 해줄 필요가 없습니다.

```java
@GetMapping("/")
public ResponseEntity<T> getUser() {
    T user = userService.getUser();
    return ResponseEntity.ok(user);
}
```

- 하지만 API 설계 측면에서는 타입 파라미터를 이용하는 것보다 명시적으로 사용자 객체를 지정해 주는 것이 더 좋습니다.

```java
@GetMapping("/users")
public ResponseEntity<User> getUser() {
    User user = userService.getUsers();
    return ResponseEntity.ok(user);
}
```


