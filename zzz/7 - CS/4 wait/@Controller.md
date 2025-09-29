생성일 | {{2024-00-00}}
작성자 | 김동욱


---

### @Controller

-  일반적인 컨트롤러를 정의할 때 사용된다. 
	- ```
	  ```java
@Controller
public class ExampleController {
    
    @GetMapping("/home")
    public String home(Model model) {
        model.addAttribute("message", "Hello World!");
        return "home";
    }
}
```
	- 
	![[Controller.png]]
	
	1. Client는 URL 형식으로 웹 서비스에 요청을 보낸다.
	2. DispatcherServlet이 요청을 처리할 대상을 찾는다.
	3. HandlerAdapter을 통해 요청을 Controller로 위임한다. 
	4. Controller는 요청을 처리한 후에 ViewName을 반환한다.
	5. DispatcherServlet은 ViewResolver를 통해 ViewName에 해당하는 View를 찾아 사용자에게 반환한다.
	   
  
### @ResponseBody

- ResponseBody를 메서드에 적용하면 메서드의 반환 값이 HTTP 응답의 본문으로 처리되어 데이터 형식(JSON, XML)으로 클라이언트에 전달된다. 이를 통해 RestFul API를 구현할 때 데이터를 직접 반환하고, 뷰를 사용하지 않는 방식으로 동작하게 된다. 
```java
@Controller
public class ExampleController {
    @ResponseBody
    @GetMapping("/api/data")
    public ResponseEntity<Data> getData() {
        Data data = dataService.getData();
        return ResponseEntity.ok(data);
    }
}
```
- ResponseBody를 사용하여 반환 값이 함께 상태 코드 및 헤더를 지정할 수도 있다.
- Spring은 @Controller와 @ResponseBody와 같이 두 번의 어노테이션을 사용하는 수고를 덜어주기 위해 @RestController를 지원한다.
  
  
### @RestController
- RESTFul 웹 서비스를 제공하는 컨트롤러를 정의할 때 사용되며, 메서드 반환 값이 JSON , XML 등과 같은 데이터로 처리된다.
- @Controller와 @ResponseBody 어노테이션을 합친 형태라고 생각할 수 있다.
	- 따라서 사용자는 @ResponseBody를 추가할 필요가 없다.
```java
@RestController
public class ExampleRestController {
    
    @GetMapping("/hello")
    public String hello() {
        return "Hello, World!";
    }
```

---