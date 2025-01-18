---
created:
---

---

### 1. 유용한 정보

##### GPT 질문 예시

- **`stream()`**: "모든 사람의 이름을 차례로 가져와!"
- **`map()`**: "이 사람 이름을 다른 형태로 바꿔줘!"
- **`collect()`**: "바꾼 결과들을 다시 리스트로 만들어서 나한테 줘!"

이렇게 `stream()`을 사용하면 **데이터를 쉽게 변환**하고 **리스트로 모을 수** 있어서 코드가 더 짧고 간결해집니다.

---
### 2. 유용한 코드

- 더미데이터 메서드
		//    대량 insert 더미 데이터 메서드  
	//    @GetMapping("test")  
	//    public String test(HttpSession session) {  
	//        UserDTO logIn = (UserDTO) session.getAttribute("logIn");  
	//        if (logIn == null) {  
	//            return "redirect:/";  
	//        }  
	//        for (int i = 1; i <= 300; i++) {  
	//            ItemDTO itemDTO = new ItemDTO();  
	//            itemDTO.setName("테스트 상품이름 " + i);//            itemDTO.setDescription("테스트" + i + "번 상품 설명입니다.");  
	//            itemDTO.setPrice(1000);  
	//            itemDTO.setQuantity(100);  
	//            itemDTO.setUserId(logIn.getId());  
	//            itemService.insert(itemDTO);  
	//        }  
	//  
	//        return "redirect:/item/showAll";  
	//    }

---
### 3. 아이디어 
###### 상용 정보
- 상영정보를 이렇게 활용해 볼수 있지 않을까?!
``` java
@RestController
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{userId}")
    public ResponseEntity<User> getUserById(@PathVariable Long userId) {
        // userId를 사용하여 특정 사용자 정보 조회
        User user = userService.getUserById(userId);
        if (user != null) {
            return ResponseEntity.ok(user);
        } else {
            return ResponseEntity.notFound().build();
        }
    }
	
    @GetMapping("/{userId}/posts/{postId}")
    public ResponseEntity<Post> getPostById(@PathVariable Long userId, @PathVariable Long postId) {
        // userId와 postId를 사용하여 특정 사용자의 특정 포스트 조회
        Post post = postService.getPostById(userId, postId);
        if (post != null) {
            return ResponseEntity.ok(post);
        } else {
            return ResponseEntity.notFound().build();
        }
    }
    // 추가적인 API 메서드들...
}
```



---



