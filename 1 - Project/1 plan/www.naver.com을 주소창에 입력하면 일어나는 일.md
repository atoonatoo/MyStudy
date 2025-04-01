
---
- [[CS]]
---


컴퓨터를 이용하는 사용자들은 대부분 웹 브라우저를 이용할 것이다. 
우리에게 익숙하고 당연한 이 웹브라우저를 이용하면서 이런 의문을 가져본다.
**웹 브라우저에 URL을 입력하면 어떤 일이 생기는걸까?**
그 뒷단에서 일어나는 과정에 대해서 알아보도록 하자.

---

![](https://velog.velcdn.com/images/atoonatoo/post/f62fa305-2fa9-4560-9a26-2e38c84bb3e9/image.png)


# 1. PC 브라우저에서 URL 입력  
- 사용자가 PC 브라우저(Chrome, Edge, Firefox, Safari 등)의 주소창에 www.naver.com을 입력함.  
---

# 2. Local DNS에 질의  
- PC는 미리 설정되어 있는 DNS(Local DNS)에게 "www.naver.com"이라는 hostname에 대한 IP주소를 요청함.  
---

# 3. 캐싱 정보 부재 확인  
- Local DNS에 "www.naver.com"에 대한 캐싱 정보가 없다고 가정함.  
---

# 4. 다른 DNS 서버와의 통신 시작  
- Local DNS는 "www.naver.com"의 IP주소를 찾기 위해 DNS 메시지를 통해 다른 DNS 서버들과 통신을 시작함.  
- 우선 Root DNS 서버에게 질의함.  
---

# 5. Root DNS 서버 정보의 사전 설정  
- 각 Local DNS 서버에는 Root DNS 서버의 IP 주소 정보가 미리 설정되어 있어야 함.  
---

# 6. Root DNS 서버의 응답  
- Root DNS 서버는 "www.naver.com"에 대한 정보를 가지고 있지 않음.  
- naver.com이 .com 도메인이므로, Local DNS에게 com 도메인을 관리하는(TLD) DNS 서버의 정보를 포함하여 응답함.  
---

# 7. com 도메인 DNS 서버 질의  
- Local DNS는 com 도메인을 관리하는 DNS 서버에게 "www.naver.com"의 IP주소를 알고 있는지 질의함.  
---

# 8. com 도메인 DNS 서버의 응답  
- 해당 DNS 서버 역시 "www.naver.com"의 정보를 가지고 있지 않음.  
- 대신, Local DNS에게 naver.com 도메인을 관리하는 DNS 서버의 정보를 포함하여 응답함.  
---

# 9. naver.com 도메인 DNS 서버 질의  
- Local DNS는 naver.com 도메인을 관리하는 DNS 서버에게 "www.naver.com"의 IP주소를 질의함.  
---

# 10. 최종 IP주소 반환  
- naver.com 도메인을 직접 매니징하는 DNS 서버는 "www.naver.com"에 대한 IP주소를 반환함.  
---

# 11. IP주소 캐싱 및 전달  
- Local DNS는 반환받은 IP주소를 캐싱하고 단말(PC)에 전달함.  
---

> **Recursive Query:**  
> Local DNS 서버가 Root DNS → com DNS → naver.com DNS 순서로 여러 DNS 서버에 질의하는 방식으로, 이 과정을 Recursive Query라고 부름.  
---


---

# 참고 문헌

1. https://aws.amazon.com/ko/blogs/korea/what-happens-when-you-type-a-url-into-your-browser/
2. https://sangbeomkim.tistory.com/173
3. https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Network/%EC%A3%BC%EC%86%8C%EC%B0%BD%EC%97%90%20naver.com%EC%9D%84%20%EC%B9%98%EB%A9%B4%20%EC%9D%BC%EC%96%B4%EB%82%98%EB%8A%94%20%EC%9D%BC.md
