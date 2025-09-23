---
created:
---
---
- [[Home]]
---

##### 2. 유용한 코드

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