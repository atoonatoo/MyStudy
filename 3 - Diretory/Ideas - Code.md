---
created:
---

---
- [[0 Home]]
---

###### 상용 정보
- 상영정보를 이렇게 활용해 볼수 있지 않을까?
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