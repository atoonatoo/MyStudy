---
created:
---
---
- [[0 Home]]
- [[learning]]
---
##### Jmeter 로그인 대용량 트래픽 테스트을 위한 필수 세팅

- CSV Data Set Config 설정
    - Filename: users.csv (email,password 포함된 파일)
    - Variable Names: email,password
    - Ignore first line: True
    - 예시:
        - `email,password test1@naver.com,123456789`
    
- Thread Group 설정
    - Number of Threads: 테스트할 사용자 수 (예: 30)
    - Loop Count: 반복 횟수 (1로 설정하면 사용자당 1회 로그인)
    
- HTTP Request 설정
    - Method: POST
    - Path: /login
    - Body Data: 아래 JSON 형식 입력
    - Use multipart: 체크하지 않음
    - Body 예시:
        - `{   "email": "${email}",   "password": "${password}" }`
    - 필수 Header:
        - Content-Type: application/json
        - Accept: application/json
    
- 서버 쪽 사전 조건
    - 로그인 API는 email, password 필드명을 JSON으로 받아야 함
    - csrf().disable() 설정 필요 (CSRF 토큰 없이도 POST 가능)
    - /login 경로가 permitAll()로 허용되어야 함
    - DB의 비밀번호는 반드시 BCrypt 해시로 저장되어야 함
    - `BCryptPasswordEncoder.matches("123456789", dbHash)`가 true가 되어야 로그인 성공
    
- View Results Tree 확인
    - 전송된 JSON에 `${email}`이 실제 사용자 이메일로 치환됐는지 확인
    - 응답 상태 코드가 200 OK인지, 아니라면 401 메시지 내용 확인
    
- 로그인 성공 시 토큰 추출 (선택 사항)
    - JSONPath Extractor로 token 값 추출 가능
    - 이후 API 요청에 Authorization: Bearer ${token} 헤더 추가 가능

---

- 요약 순서
    
    - CSV 설정 (email/password)
        
    - Thread Group 사용자 수 설정
        
    - HTTP Request → POST + JSON + Header
        
    - 서버 로그인 API 구조와의 정합성 확인
        
    - View Results Tree로 응답 및 치환 여부 확인


