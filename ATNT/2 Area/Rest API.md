

----
##### 연결 문서

- 
- 
- 
---

### [ REST API ]

- **** [ REST API란? ]
	
	- **** < REST란? >
		- Representational State Transfer)의 약자
		- 자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 모든 것을 의미
		- HTTP URI를 통해 자원(Resource)을 명시하고, 
		  HTTP Method (POST, GET, PUT, DELETE, PATCH 등)을 통해 
		  해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미 
		  
		  
	- **** < CRUD Operation이란?>
		- CRUD는 대부분의 컴퓨터소프트웨어가 가지는 기본적인 데이터 처리 기능인
		  Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말로 
		  REST에서 CURD Operation의 동작 예시는 다음과 같다. 
			- Create : 데이터 생성 (POST)
			- Read : 데이터 읽기 (GET)
			- Update : 데이터 수정 (PUT, PATCH)
			- Delete : 데이터 삭제 (DELETE)
			  
			  
	- **** < REST의 구성 요소 >
		1. 자원 : HTTP URI
		2. 자원에 대한 행위 : HTTP Method
		3. 자원에 대한 행위의 내용 : HTTP Message Pay Load
		   
		   
	- **** < REST의 특징 > 
		1. Server-Client (서버-클라이언트 구조)
		2. Stateless (무상태)
		3. Cacheable (캐시 처리 가능)
		4. Layered System (계층화)
		5. Uniform Interface (인터페이스 일관성)
		   
		   
	- **** < REST의 장단점 >
		- 장점
			1. HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API를 사용하기 위한 
			   별도의 인프라 구축을 할 필요가 없다.
			2. HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 함께
			   가져갈 수 있게 해준다.
			3. HTTP 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.
			4. Hypermedia API의 기본을 충실히 지키면서 범용성을 보장한다.
			5. REST API 메세지가 의도하는 바를 명확하게 나타내므로
			   의도하는 바를 쉽게 파악할 수 있다. 
			6. 여러 가지의 서비스 디자인에서 생길 수 있는 문제를 최소화한다.
			7. 서버와 클라이언트의 역할을 명확하게 분리한다. 
			   
		- 단점
			1. 표준이 자체가 존재하지 않아 정의가 필요하다.
			2. HTTP Method의 형태가 제한적이다.
			3. 브라우저를 통해 테스트할 일이 많은 서비스라면 쉽게 고칠 수 있는 URL보다 Header정보의 값을 처리해야 하므로 전문성이 요구된다. 
			4. 구형 브라우저에서 호환되지 않아 지원해주지 못하는 동작이 많다.(익스플로러)
			   
			   
	- ****< REST API를 만들 때는 정말 잘 만들어야 하는 이유 >
		1. REST API = 법
		2. 한번 설계하면 다시 수정하거나 변경하기가 너무 힘들다.
		3. 그렇기에 완벽하게 설계를 맞춰야한다.
		   
		   
	- **** < REST API란? >
		- REST의 원리를 따르는 API를 의미
		- REST API를 올바르게 설계하기 위해서는 지켜야 하는 몇가지 규칙이 있다. 
		  
		  
	- **** < REST API 설계 예시 >
		1. URI는 동사보다도 명사를, 대문자보다는 소문자를 사용해야 한다. 
		2. 마지막에 슬래시( / )를 포함하지 않는다.
		3. 언더바 대신 하이폰을 사용한다.
		4. 파일 확장자는 URI를 포함하지 않는다.
		5. 행위를 포함하지 않는다.
		   
		   
	- **** < RESTFul 이란?>
		- REST의 원리를 따르는 시스템을 의미
		- 하지만 REST를 사용했다고 모두가 RESTFul한 것은 아니다.
		- REST API의 설계 규칙을 올바르게 지킨 시스템을 RESTFul하다고 말할 수 있다.
	
	
- **** [ REST API 명강의 : 그런 REST API로 괜찮은가? ]
    
	1. **REST의 탄생 배경
		- 어떻게 인터넷에서 정보를 공유할 것인가?
	      
	      
    2. **정보를 하이퍼텍스트로 연결한다 
	    - 표현형: HTML
	    - 식별자 : URL 
	    - 전송 방법 : HTTP
	    
	    
    3. **Roy Fielding ( 대학원생 )
	    - 어떻게 하면 웹을 망가뜨리지않고 Wep을 진보시킬수 있을까?
	      
	      
    4. **해결책
	    - HTTP Object Model ( 4년후 REST라는 이름으로 발표 )
	      
	      
	5. **XML-RPC
		- 원격으로 다른 시스템의 메소드를 호출할수있는 프로토콜 -> SOAP
	      
	      
    6. **Salesforce API (2000.2)
		- 최초의 API 공개
	     
		 
	7. **SOAP의 단점
		- 복잡
		- 규칙 많음
		- 어렵다
	      
	      
	8. **REST의 장점
		- 단순
		- 규칙 적음
		- 쉽다
	      
	      
    9. **결과
		- SOAP 인기추락
		- REST 인기상승
		
	      
	10. **CMIS (2009) 발표
		- CMS 표준
		- EMC, IBM, MS 등 함꼐 작업
		- REST 바인딩 지원
    	- 로이 필딩 曰 : "NO REST in CMIS" ( CMIS에 레스트는 없다. )
	      
	      
	11. **MS API Guidelines (2016)
		- API 버저닝은 Major.minor로 하고 url에 버전 정보를 포함시킨다 등등..
		- 로이 필딩 曰 : "s/REST API/HTTP API/" 
		  ( 이것도 레스트가 아니다 이건 HTTP API라고 해야한다.)
	    
		  
    12. **로이 필딩 : "REST APIs must be hypertext-driven"
        ( REST API는 반드시 하이퍼텍스트 드라이븐이어야한다. )
		( REST API를 위한 최고의 버저닝 전략을 버저닝을 안 하는 것 )
	     
		 
    13. **뭐가 문제인가?
	    
		
    14. **REST API란 무엇인가?
	    -  REST 아키텍쳐 스타일을 따르는 API
	      
	      
    15. **그럼 REST란 무엇인가?
	    - 분산 하이퍼미디어 시스템( ex : Wep )을 위한 아키텍쳐 스타일
	      
	      
    16. **아키텍쳐 스타일은 무엇인가?
	    - 제약조건의 집합 
        - 그러므로 제약조건을 모두 지켜야 REST를 따른다고 가능하다.
	     
		 
    17. **REST를 구성하는 스타일
        - client-server
        - stateless
        - cache
        - **< uniform interface >** 
        - layered system
        - code-on-demand(optional)
          
        - 대체적으로 충족하고있지만 uniform interface은 대부분 충족을 못함
	    
		  
	18. **uniform interface의 제약 조건
        - identification of resources
        - manipulation of resources through representations
        - < self-descriptive messages >
        - < hypermedia as thwe engine of application state (HATEOAS) >
	      
	      
	19. **self-descriptive messages
		1. 메시지는 스스로를 설명해야한다.
        2. 메시지를 봤을 때 메시지 내용으로 온전히 해석이 다 가능해야한다. 
        
        - 하지만 오늘날 REST API가 이것을 상당히 만족하지 못하고있다.
	    
	    
	20. **HATEOAS
		- 애플리케이션의 상태는 Hyperlink를 이용해 전이되어야한다.
	    
   
    21. **그렇다면 왜 uniform interface를 지켜야하는가?
        - 서버와 클라이언트가 각각 독립적으로 진화한다.
        - 서버의 기능이 변경되어도 클라이언트를 업데이트할 필요가 없다.
          
    	- 근본적인 REST API가 만들어진 이유
    		내가 HTTP를 고치면 웹이 깨질 것 같은데 어떻게하면 이 문제를 해결할수 있을까?
	    
	    
	22. **REST가 잘 지켜지고있다는 대표적인 사례 -> WEP
        - 웹 페이지를 변경했다고 웹 브라우저를 업데이트할 필요는 없다.
        - 웹 브라우저를 업데이트했다고 웹 페이지를 변경할 필요도 없다.
        - HTTP 명세가 변경되어도 웹은 잘 동작한다.
        - HTML 명세가 변경되어도 웹은 잘 동작한다.
		    
		    
    23. **WEP은 어떻게 가능한걸까?
        - 피나는 노력 
        - W3C , IETF , 웹 브라우저 개발자들, 웹 서버 개발자들
        - HTML 첫 초안에서 권고안 나오는데까지 6년
        - HTML/1.1명세개정판 작업하는데 7년
          
        - 이렇게 오랜 걸린 이유 : 하위호환성을 절대 깨드리면 안됨 
        - 상호운용성에 대한 집착  
	        - Referer 오타지만 안고침
	         * charset 잘못 지은 이름이지만 안 고침
		    	- 왜? : 이름을 고치면 상호운용성이 깨지기 때문에 ( 웹이 깨지기 때문에 )
        
        
    24. **REST가 웹의 독립적 진화에 도움을 주었나?
        - HTTP에 실제로 지속적으로 영향을 줌
        - Host 헤더 추가
	    	- 길이 제한을 다루는 방법이 명시
	    	- URI에서 리소스의 정의가 추상적으로 변경됨 : 식별하고자 하는 무언가
	    	-  기타 HTTP와 URI에 많은 영향을 줌
        - HTTP/1.1 명세 최신판에서 REST에 대한 언급이 들어감
        - 로이 필딩이 HTTP와 URI 명세의 저자 중 한명이다.
	      
	      
    25. **그럼 REST는 성공했는가?
	    - Yes : 성공 !
    	- REST는 Wep의 독립적 진화를 위해 만들어졌다.
	    - Wep은 독립적으로 진화하고 있다.
	      
	26. **그런데 REST API는?
    	  - REST API는 REST 아키텍쳐 스타일을 따라야한다.
    	  - 오늘날 스스로 REST API라고 하는 대부분이 
    	    REST 아키텍쳐 스타일을 따르지 않는다.
	     
		 
	27. **REST API도 저 제약조건들은 다 지켜야 하는건가? 
	    -  로이 필딩 曰 : 지켜야한다.
    	- 하이퍼텍스트를 포함한 self-descriptive한 
    	  메시지의 uniform interface를 통해 리소스에 접근하는 API
		
		    
	28. **이런 줄 알았는데 - 오해였나봅니다.
		- SOAP : 복잡 / 규칙 많음 / 어렵다
        - REST : 단순 / 규칙 적음 / ~~쉽다~~ -> 어렵다.
	     
		 
    29. **원격 API가 꼭 REST API여야 하는건가?
		- 아니라고 한다.
    	- 시스템 전체를 통제 할 수 있다고 생각하거나, 진화에 관심이 없다면, 
    	  REST에 대해 따지느라 시간을 낭비하지 마라.
	    
		  
    30. **그럼 이제 어떻게 할까?
    	1. REST API를 구현하고 REST API라고 부른다.
    	2. RESTAPI 구현을 포기하고 HTTP API라고 부른다.
		3. REST API가 아니지만 REST API라고 부른다. ( 현재 상태 )
	    	 - 로이 필딩 : "제발 제약조건 따르던지 아니면 다른 단어를 써라. "
	      
	      
	31. **일단 왜 API는 REST가 잘 안되나 일반적인 웹과 비교해보자
    	  - Protocol
	    	  - (WEP) HTTP
	    	  - (HTTP API) HTTP
    	  - 커뮤니케이션
	    	  - (WEP) 사람-기계
	    	  - (HTTP API) 기계-기계
    	  - Media Type
	    	  - (WEP) HTML
	    	  - (HTTP API) JSON 
		- Hyperlink
			- (HTML) 된다. (a 태그 등)
			- (JSON) 정의 되어있지 않음
    	  - Self-descriptive
	    	  - (HTML) 된다. (HTML 명세)
	    	  - (JSON) 불완전
	      
	      
    32. **그런데 이 두 가지가 독립적 진화에 어떻게 도움이 되는가?
    	- elf-descriptiv 
	    	- 확장 가능한 커뮤니케이션 / 서버가 변하거나 클라이언트가 변하든 
	    	  메시지는 언제나 해석이 가능하다. 
	    	  ( 서버가 얼마나 바뀌든 메시지만 보고도 해석이 가능 )
	    	  
    	  - HATEOAS
	    	- 어플리케이션 상태 전이의 late binding 
	    		- 쉽게 말해 링크를 언제든지 바꿀수있다.
	    		- 서버가 링크를 바꾼다 해도 클라이언트에 동작에는 전혀 문제가 없다.
		     
			 
	33. **REST로 고치는 올바른 방법
	    - Self-descriptive 
	    	- Media type : 
    		- Profile : 
    	* HATEOAS : data, 헤더 모두 활용 하면 좋다.
	    	- data : 
	    	- HTTP 헤더 : 
    		
    		
    34. **하이퍼링크는 반드시 URI여야 하는건 아닌가?
    	- <http://toss.im/users/engjun>
    	- /user/eungjun
    	- eungjun
    	- /users/{username}
		- 하이퍼링크라는것만 표현된다면 다 상관없다.
	    
	    
	35. **Media type 등록은 필수인가?
		- NO
    	
    	
    36. **정리
    	1. 오늘날 대부분의 "REST API"는 사실 REST를 따르지 않고 있다.
    	   
    	2. REST의 제약조건 중에서 특히 Self-descriptive / HATEOAS를 잘 만족하지 못한다.
    	   
	    3. REST는 긴 시간에 걸쳐(수십년) 진화하는 웹 어플리케이션을 위한 것이다.
	       
    	4. REST를 따를 것인지는 API를 설계하는 이들이 스스로 판단하여 결정해야한다.
    	   
	    5. REST를 따르겠다면, Self-descriptive/HATEOA 만족시켜야한다.
	       
    	6. Self-descriptive는 custom media type이나 profile link relation 등으로 만족 가능
    	   
    	7. HATEOA는 HTTP 헤더나 본문에 링크를 담아 만족시킬 수 있다.
    	   
    	8. REST를 따르지 않겠다면, "REST를 만족하지 않는 REST API"를 
    	   뭐라고 부를지 결정해야 할 것이다.
	    	- HTTTP API라고 부를 수도 있고
	    	- 그냥 이대로 REST API라고 부를 수도 있다. ~~(roy가 싫어합니다)~~
	
	

