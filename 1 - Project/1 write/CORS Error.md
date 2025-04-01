
---
- [[CS]]
---

# 1. CORS 에러란?

웹 개발을 하다보면 반드시 마주치는 머리 아픈 에러가 바로 CORS 이다. 웹 개발의 신고식이라고 할 정도로, CORS는 누구나 한 번 정도는 지긋지긋하게 고생시켰을법한 에러이다.

![](https://velog.velcdn.com/images/atoonatoo/post/ccab0dcf-047a-463c-8303-b8e4e124bfa8/image.png)

FE 입장에선 요청 코드를 이상하게 적은 것도 아니고, BE 입장에선 서버 코드나 세팅이 이상한 것도 아니다. 모든게 멀쩡한데 왜 요청한 자료에 대한 응답이 에러로 뜨니까 어디가 문제인지 모르고 감이 도저히 안잡혔었다.

![](https://velog.velcdn.com/images/atoonatoo/post/0b54f6ca-f203-4ea9-ad3d-a4fc11c36717/image.png)

이러한 현상이 일어나는 이유는, 웹 브라우저는 HTTP 요청에 대해서 어떤 요청을 하느냐에 따라 **각기 다른 특징**을 가지고 있기 때문이다.

---

## 1.1 요청 방식에 따라 다른 CROS 발생 여부

### 1.1.1 `<img>, <video>, <script>, <link> 태그 등`

- `기본적으로 Corss-Origin 정책을 지원한다.`

- `<link>` : 태그의 href 에서 다른 사이트의 .css 리소스에 접근하는 것이 가능

- `<img>` : 태그의 src에서 다른 사이트의 .png, ,jpg 등의 리소스에 접근하는 것이 가능

- `<script>` : 태그의 src 에서 다른 사이트의 .js 리소스에 접근하는 것이 가능 (`type="module" 속성은 제외)

```html

<link rel="stylesheet" href="…" />
<script src="…"></script>
<img src="…" />

```

---

### 1.1.2 XMLHttpRequest, Fetch API 스크립트

- `기본적으로 Same-Origin 정책을 따른다.`

- 다른 도메인의 소스에 대해 자바스크립트 ajax 요청 API 호출시
- 웹 폰트 CSS 파일 내 @font-face에서 다른 도메인의 폰트 사용 시

자바스크립트에서의 요청은 기본적으로 `서로 다른 도메인에 대한 요청을 보안상 제한`한다.

브라우저는 기본으로 하나의 서버 연결만 허용돠도록 설정되어 있기 때문이다. (주로 자신의 서버)

처음보는 용어가 나온다. **Same Origin 정책**과 **Cross Origin 정책** 

이 정책의 정보 부족으로 인해 **나도 모르게 정책을 위반하는 행동**을 하게 되어 CORS 에러가 나타나는 것이다.

요청 방식에 따라 다른 CORS 발생 여부를 좀 더 이해하기 쉽게 아래 html 코드를 직접 작성하고 테스트하였다.

상황 : 똑같은 서버 도메인으로 부터 check.svg 이미지를 가져오는데, 각각 `<img>` 태그의 src 속성으로 가져오는 방식과 자바스크립트에서 ajax 요청으로 가져오는 방식이다.
- 코드
```html
<body>
    <img src="https://third-party-test.glitch.me/check.svg" alt="이미지">

    <script>
        fetch('https://third-party-test.glitch.me/check.svg')
            .then(response => response.blob())
            .then(imgBlob => {
                const imageObjectURL = URL.createObjectURL(imgBlob); // 응답 받은 이미지를 blob 객체로 변환
                const img = document.createElement('img'); // 이미지 태그를 생성하고
                img.src = imageObjectURL; // 이미지 경로를 설정한뒤
                document.body.append(img); // html에 추가
            })
    </script>
</body>
```

- 결과
![](https://velog.velcdn.com/images/atoonatoo/post/d2172b39-b332-4897-a184-531566c80953/image.png)
페이지 결과를 보면 이미지가 하나만 나타나는 걸 볼 수 있다.

브라우저 개발자 도구의 Network 창을 보면 check.svg 이미지에 대해서 두번 요청은 했지만 자바스크립트 fetch Type으로 요청한 것이 Status가 CORS error임을 볼 수 있다.

![](https://velog.velcdn.com/images/atoonatoo/post/6c6010ce-94f2-4fa5-8b4f-903b07586e43/image.png)

이 골치아픈 CORS 에러를 해결해보도록 하겠다.

---

# 2. CORS Error 이해하기

CORS는 함축 단어이며 이를 풀면 **Cross-Origin Resource Sharing** 이다.
직역하면 `교차 출처 리소스 공유 정책` 이라고 해석할 수 있다.

여기서 `교차 출처` 는 `(엇갈린) 다른 출처` 를 의미한다.

![](https://velog.velcdn.com/images/atoonatoo/post/3b25d8c6-63e6-4c29-8232-5c1a577b3ed5/image.png)

이어서 CORS 에러 메세지를 해석 해보도록 하자.

![](https://velog.velcdn.com/images/atoonatoo/post/cea2ee60-7b89-4825-addd-f9c1c7b8a39a/image.png)

아무래도 배경지식이 부족하다보니 어떻게 해결해야 할지 감이 안잡힌다.

우선 CORS의 다른 출처 리소스 공유 정책(Cross Origin Resource Sharing)이 어떠한 정책인지 알아볼 필요성을 느꼇다. 

우선 출처(Origin)가 무엇인지 살펴보자.

---

## 2.1 출처(Origin)란?

우리가 어떤 사이트를 접속할 때 인터넷 주소창에 우리는 URL이라는 문자열을 통해 접근하게 된다.

이처럼 URL은 `https://domain.com:3000/user?query=name&page=1` 과 같이 하나의 문자열 같지만, 사실은 다음과 같이 여러개의 **구성 요소** 로 이루어져 있다.

![](https://velog.velcdn.com/images/atoonatoo/post/b6f5d1a5-8578-4363-a6c0-7bf2b332c19a/image.png)

- Protocol(Scheme) : http, https
- Host : 사이트 도메인
- Port : 포트 번호
- Path : 사이트 내부 경로
- Query string : 요청의 key와 value 값
- Fragment : 해시 태그

CROS를 이해하는데 있어서 저것들 모두를 알아야 하는 것은 아니고, 딱 3가지만 기억하면 된다.

- Origin : Protocol + Host + Port

즉, **출처(Origin) 라는 것은 Protocol 과 Host 그리고 Port 까지 모두 합친 URL*** 을 의미한다. 

간단하게 현재 사이트의 Origin을 알아낼 수도 있다.

```javascript
console.log(location.origin); // "https://www.naver.com" (포트 번호 80번은 생략됨)
```

---

## 2.2 동일 출처 정책 (Same-Origin Policy)

출처(Origin)에 대해서 알아봤으니 이제 본격적으로 Same Origin 정책과 Cross Origin 정책에 대해 알아보자.

먼저 SOP (Same Origin Policy) 정책은 단어 그대로 **동일한 출처에 대한 정책** 을 말한다.
그리고 이 SOP 정책은 `동일한 출처에서만 리소스를 공유할 수 있다.` 라는 법률을 가지고 있다.

즉, 동일 출처(Same-Origin) 서버에 있는 리소스는 자유로이 가져올수 있지만, 다른 출처(Corss-Origin) 서버에 있는 이미지나 유튜브 영상 같은 리소스는 상호작용이 불가능하다는 말이다.

![](https://velog.velcdn.com/images/atoonatoo/post/89edd7a2-fee8-495e-9a9d-578347624dfc/image.png)

### 2.2.1 동일 출처 정책이 필요한 이유

그렇다면 동일 출처가 아닌 경우 접근을 차단하는 이유는 무엇인가?

사실 출처가 다른 두 어플리케이션이 자유로이 소통할 수 있는 환경은 꽤 위험한 환경이다.
만일 제약이 없다면, 해커가 CSRF(Cross-Site Request Forgery)나 XSS(Crooss-Site Scripting) 등의 방법을 이용해서 우리가 만든 어플리케이션에서 해커가 심어놓은 코드가 실행하여 개인 정보를 가로 챌 수 있다.

**다음은 SOP 정책이 없는 상황에서 악의적인 홈페이지에 접속하는 상황을 가정 한 것이다.**

![](https://velog.velcdn.com/images/atoonatoo/post/893ffb4f-3c08-43ca-a983-d4155f966487/image.png)

1. 사용자가 악성 사이트에 접속한다.
2. 이떄 해커가 몰래 심어놓은 악의적인 자바스크립트가 실행되어, 사용자가 모르는 사이에 어느 포털 사이트에 요청을 보낸다.
3. 그럼 포털 사이트에서는 해당 브라우저의 쿠키를 이용하여 로그인을 하거나 등 상호작용에 따른 개인 정보를 응답 값을 받은 뒤, 사이트에서 해커 서버(hacker.example.com)로 재차 보낸다.
4. 이외에도 사용자가 접속중인 내부망의 아이피와 포트를 가져오거나, 해커가 사용자 브라우저를 프록시처럼 악용할 수 있다.
  
따라서 이러한 악의적인 경우를 방지하기 위해, SOP 정책으로 동일하지 않는 다른 출처의 스크립트가 실행되지 않도록 브라우저에서 사전에 방지하는 것이다.

---

### 2.2.2 같은 출처와 다른 출처 구분 기준

`그렇다면 두개의 출처의 다름 유무를 판단하는 기준이 무엇일까?`

출처(Origin)의 동일함은 두 URL의 구성 요소 중 **Protocol(Scheme), Host, Port 이 3가지만 동일** 하다면 동일 출처로 판단한다.

![](https://velog.velcdn.com/images/atoonatoo/post/33d88a73-cb46-48d2-8e69-c51721d79fbd/image.png)

 다음은 https://www.domain.com:3000 출처에 대한 여러 URL에 따른 동일 출처 비교 표 이다.

![](https://velog.velcdn.com/images/atoonatoo/post/bf07e47c-7fd8-4ee7-8140-a45ba82f1780/image.png)

정리하자면 같은 프로토콜, 호스트, 포트를 사용한다면, 그 뒤의 다른 요소는 다르더라도 같은 출처로 인정된다.

반대로 프로토콜, 호스트, 포트 중 하나라도 자신의 출처와 다를 경우 브라우저는 정책상 차단하게 된다.

	- tip
    웹의 흑역사인 Internet Explorer 브라우저는 우습게도 출처 비교시 Port 부분은 무시한다.
    이는 곧 보안 취약으로 이어지며 왜 그렇게 욕을 얻어먹는지에 대한 이유 중 하나이기도 하다.
    


---

### 2.2.3 출처 비교와 차단은 브라우저가 한다.

새내기 개발자들이 착각하는 부분이라고 하는데.. 
위의 출처 구분을 서버가 하는 것으로 오해하는 것이라고 한다.
아무래도 서버에 요청을 했는데 무언가 에러가 뜨면 서버가 문제라고 생각이 들 수 밖에 없기 때문이다.
그러나 출처를 비교하는 로직은 서버에 구현된 스펙이 아닌 **브라우저에 구현된** 스펙이다.

![](https://velog.velcdn.com/images/atoonatoo/post/e7a01ae1-0f57-42ba-84ab-e28161b369c7/image.png)

사실 서버는 리소스 요청에 의한 응답은 말끔히 해주었다. 즉, 잘못이 없는 것이다.
하지만 **브라우저가 이 응답을 분석해서 동일 출처가 아니면, 빨간 에러를 띄우는 것이다.**
(사실 서버가 헤더 정보를 덜 줘서 그런 것인데.. 이는 뒤에서 다룰 것이다.)

그래서 브라우저에는 에러가 뜨지만, 정작 서버 쪽에는 정상적으로 응답을 했다고 하기 때문에 난항을 겪은 것이다. 
즉, 응답 데이터는 멀쩡하지만 브라우저 단에서 받을 수 없도록 차단을 한 것이다.

	- tip
    	- 그래서 CORS 에러를 해결하는 방안 중 하나로 
    	크롬 브라우저 설정에 SOP 정책을 비활성화 하는 방법이 있긴 한데 
    	보안상 이유로 권장하지 않는다.
    
    	- 브라우저가 정책으로 차단을 한다는 말은, 브라우저를 통하지 않고 서버 간에 통신을
        할때는 정책이 적용 되지 않는다는 말과 같다.
        즉, 클라이언트 단 코드에서 API 요청을 하는게 아니라, 서버 단 코드에서 다른 출처의
        서버로 API 요청을 하면 CORS 에러로부터 자유로워 진다.
        그래서 이를 이용한 프록시(Proxy) 서버라는 것이 있다.

---

### 2.2.4 그럼 죄다 차단하면 인터넷이 되는가? 

하지만 인터넷은 여러 사람들에게 오픈된 환경이고, 이런 환경에서 웹페이지에서 다른 출처에 있는 리소스를 가져와 사용하는 일은 매우 흔한 일이라 무턱대고 막을 수 없는 일이다.

![](https://velog.velcdn.com/images/atoonatoo/post/7c25d5fa-83fa-4f66-b217-45c66e409f78/image.png)

그래서 몇 가지 **예외 조항** 을 두고 다른 출처의 리소스 요청이라도 이 조항에 해당할 경우에는 허용하기로 했는데, 그 중 하나로 바로 **CORS 정책을 지킨 리소스 요청** 이다.

---

## 2.3 교차 출처 리소스 공유 (Cross-Origin Resource Sharing)

이처럼 교차 출처 리소스 공유(Corss-Origin Resource Sharing, CORS)는 단어 그대로 **다른 출처의 리소스 공유에 대한 허용/비허용 정책**이다.

아무리 보안이 중요하지만, 개발을 하다 보면 기능상 어쩔 수 엊ㅅ이 다른 출처 간의 상호작용을 해야 하는 케이스도 있으며, 또한 실무적으로 다른회사의 서버 API를 이용해야 하는 상황도 존재한다. 따라서 이와 같은 예외 사항을 두기 위해 CORS 정책을 허용하는 리소스에 한해 다른 출처라도 받아들인다는 것이다.

---

### 2.3.1 CORS는 사실 해결책이다.

결국 웹개발자를 과롭히던 이 에러 메세지는 사실 브라우저의 SOP 정책에 따라 다른 출처의 리소스를 차단하면서 발생된 에러이며, CORS는 다른 출처의 리소스를 얻기 위한 해결 방안이었던 것이다. 
요약하자면 ** SOP 정책을 위반해도 CORS 정책에 따르면 다른 출처의 리소스라도 허용** 한다는 뜻이다. 

그럼 어떻게 CORS 정책을 따르게 하여 SOP 정책을 회피할 수 있는가?
이를 알기 위해선 브라우저의 CORS 동작 과정을 살펴 보아야 한다.

---

### 2.3.2 브라우저 CORS 기본 동작 살펴보기

1. 클라이언트에서 HTTP 요청의 Header에 Origin을 담아 전달한다.

	1. 기본적으로 웹은 HTTP 프로토콜을 이용하여 서버에 요청을 보내게 되는데,
    2. 이때 브라우저는 요청 Header에 Origin 이라는 필드에 출처를 함꼐 담아 보내게 된다.

![](https://velog.velcdn.com/images/atoonatoo/post/1645f947-f8d1-42dc-9ac7-ede1803fda26/image.png)

2. 서버는 응답 Header에 Access-Control-Allow-Origin을 담아 클라이언트로 전달한다.

	1. 이후 서버가 이 요청에 대한 응답을 할 때 응답 헤더에 `Access-Control-Allow-Origin`이라는 필드를 추가하고 값으로 `이 리소스를 접근하는 것이 허용된 출처 url`을 내려보낸다.
    
![](https://velog.velcdn.com/images/atoonatoo/post/328b7aaa-07f3-40de-948e-bcc71cc8f104/image.png)

3. 클라이언트에서 Origin과 서버가 보내준 Access-Control-Allow-Origin을 비교한다.

	1. 이후 응답을 받은 브라우저는 자신이 보냈던 요청의 Origin과 서버가 보내준 응답의 Access-Control-Allow-Origin을 비교해본 후 차단할지 말지를 결정한다.
    2. 만약 유효하지 않다면 그 응답을 사용하지 않고 버린다. (CORS Error)
    3. 위의 경우에는 둘다 http://localhost:3000이기 때문에 유효하니 다른 출처의 리소스를 문제없이 가져오게 된다.

---

### 2.3.3 결국 CORS 해결책은 서버의 허용이 필요

위의 브라우저의 CORS 동작 과정을 살펴보니, 결론은 **서버에서 Access-Control-Allow-Origin 헤더에 허용할 출처를 기재해서 클라이언트에 응답**하면 되는 것이었다.
즉, 백엔드 개발자가 고쳐야될 부분인 것이다.

	- tip
    그렇다면 클라이언트에서 미리 자바스크립트로 origin 헤더 값을 위조하면 되지 않을까 싶지만, 브라우저에서 이를 감지하여 차단하기 때문에 결론은 불가능하다.
    
![](https://velog.velcdn.com/images/atoonatoo/post/4184adda-fcb4-49a7-8d99-e6f40839b92d/image.png)

---

# 3. CORS 작동 방식 3가지 시나리오

위의 내용은 쉽게 이해하기 위한 기본 작동 흐름이고, 
실제로 CROS가 동작하는 방식은 한 가지가 아니라 **세 가지의 시나리오** 에 따라 변경된다. 

다만 이부분은 CORS를 해결하기 위한 필수 지식이 아니다.
단순 요청을 떠나 쿠키나 토큰과 같은 인증 데이터를 다른 출처의 서버에 요청을 해야한다면 이 섹션의 지식은 필수이다. 

또한 우리가 인터넷을 배울때 TCP/UDP의 내부 통신 과정을 배웠듯이,
브라우저의 세부적인 CORS 통신 동작 과정을 살펴봐야 나중에 최적화 작업을 할 수 있다.

---

## 3.1 예비 요청(Preflight Request)

사실 브라우저는 요청을 보낼때 한번에 바로 보내지 않고, 먼저 **예비 요청**을 보내 서버와 잘 통신되는지 확인한 후 **본 요청**을 보낸다.

즉, 예비 요청의 역할은 본 요청을 보내기 전에 브라우저 스스로 안전한 요청인지 미리 확인하는 것이다.

이때 브라우저가 예비요청을 보내는 것을 **Preflight** 라고 부르며, 이 예비 요청의 HTTP 메소드를 GET이나 POST가 아닌 OPTIONS라는 요청이 사용된다는 것이 특징이다.

예를들어 자바스크립트로 다음 API 요청을 보낸다고 가정해보자.

![](https://velog.velcdn.com/images/atoonatoo/post/eb39b799-7531-431a-bd31-0249a4982aa7/image.png)

---

## 3.2 단순 요청(Simple Request)

단순 요청은 말그대로 **예비 요청(Prefilght)을 생략하고 바로 서버에 직행으로 본 요청** 을 보낸 후, 서버가 이에 대한 응답의 헤더에 Access-Control-Allow-Origin 헤더를 보내주면 브라우저가 CORS 정책 위반 여부를 검사하는 방식이다.

![](https://velog.velcdn.com/images/atoonatoo/post/7db440a6-db8c-4623-b065-4aa544e7df83/image.png)

다만, 심플한 만큼 특정 조건을 만족하는 경우에만 예비 요청을 생략할 수 있다.

대표적으로 아래의 **3가지 경우를 만족** 할 때만 가능하다.

1. 요청의 메서드는 `GET`, `HEAD`, `POST` 중 하나여야 한다.
2. `Accept`, `Accept-Language`, `Content-Language`, `Content-Type`, `DPR`, `Downlink`, `Save-Data`, `Viewport-Width`, `Width` 헤더일 경우에만 적용된다.
3. Content-Type 헤더가 `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain` 중 하나여야한다. 아닐 경우 예비 요청으로 동작된다.

이처럼 다소 **까다로운 조건**들이 많기 떄문에, 위 조건을 모두 만족되어 단순 요청이 일어나는 상황은 드물다고 보면된다.

왜냐하면 대부분 HTTP API 요청은 `text/xml` 이나 `application/json` 으로 통신하기 때문에 3번째 Context-Type이 위반되기 때문이다.

**따라서 대부분의 API 요청은 그냥 예비 요청(preflight)으로 이루어진다 라고 이해하면 된다.**

---

## 3.3 인증된 요청 (Credentialed Request)

인증된 요청은 클라이언트에서 서버에게 **자격 인증 정보(Credential)** 를 실어 요청할 때 사용되는 요청이다.

여기서 말하는 **자격 인증 정보**란 세션 ID가 저장되어있는 `쿠키(Cookie)` 혹은 `Authorization 헤더`에 설정하는 `토큰` 값 등을 일컫는다.

즉, 클라이언트에서 일반적인 JSON 데이터 외에도 쿠키 같은 인증 정보를 포함해서 다른 출처의 서버로 전달할 때 CORS의 세가지 요청 중 하나의 인증된 요청으로 동작된다는 말이며, 이는 기존의 단순 요청이나 예비 요청과는 살짝 다른 인증 형태로 통신하게 된다.

---

### 3.3.1 클라이언트에서 인증 정보를 보내도록 설정하기

기본적으로 브라우저가 제공하는 요청 API 들은 별도의 옵션 없이 브라우저의 쿠키와 같은 인증과 관련된 데이터를 함부로 요청 데이터에 담지 않도록 되어있다.
이때 요청에 인증과 관련된 정보를 담을 수 있게 해주는 옵션이 바로 credentials 옵션이다. 이 옵션에는 3가지의 값을 사용할 수 있으며, 각 값들이 가지는 의미는 아래와 같다.

- 옵션값
	1. same-origin(default)
    	같은 출처 간 요청에만 인증 정보를 담을 수 있다.
	2. include
    	모든 요청에 인증 정보를 담을 수 있다.
    3. omit
    	모든 요청에 인증 정보를 담지 않는다.

이런 별도의 설정을 해주지 않으면 쿠키 등의 인증 정보는 절대로 자동으로 서버에게 전송되지 않는다.

서버에 인증된 요청을 보내는 방법으로는 fetch 메서드를 사용하거나 axios, jQuery 라이브러리 등 다양한다. 어떤 메서드를 사용하느냐에 따라 약간 `creden tials` 옵션을 지정하는 문법이 다르다.

```javascript
// fetch 메서드
fetch("https://example.com:1234/users/login", {
	method: "POST",
	credentials: "include", // 클라이언트와 서버가 통신할때 쿠키와 같은 인증 정보 값을 공유하겠다는 설정
    body: JSON.stringify({
        userId: 1,
    }),
})


// axios 라이브러리
axios.post('https://example.com:1234/users/login', { 
    profile: { username: username, password: password } 
}, { 
	withCredentials: true // 클라이언트와 서버가 통신할때 쿠키와 같은 인증 정보 값을 공유하겠다는 설정
})


// jQuery 라이브러리
$.ajax({
	url: "https://example.com:1234/users/login",
	type: "POST",
	contentType: "application/json; charset=utf-8",
	dataType: "json",		
	xhrFields: { 
    	withCredentials: true // 클라이언트와 서버가 통신할때 쿠키와 같은 인증 정보 값을 공유하겠다는 설정
    },
	success: function (retval, textStatus) {
		console.log( JSON.stringify(retval));
	}
});
```

---

### 3.3.2 서버에 인증된 요청에 대한 헤더 설정하기

서버도 마찬가지로 이러한 인증된 요청에 대해 **일반적인 CORS 요청과는 다르게 대응** 해줘야 한다.

1. 응답 헤더의 `Access-Control-Allow-Credentials` 항목을 true로 설정해야 한다.
2. 응답 헤더의 `Access-Control-Allow-Origin` 의 값에 와일드카드 문자(`*`)는 사용할 수 없다.
3. 응답 헤더의 `Access-Control-Allow-Methods` 의 값에 와일드카드 문자(`*`)는 사용할 수 없다.
4. 응답 헤더의 `Access-Control-Allow-Headers` 의 값에 와일드카드 문자(`*`)는 사용할 수 없다.

즉, 응답의 Access-Control-Allow-Origin 헤더가 와일드카드(`*`)가 아닌 분명항 Origin으로 설정되어야 하고, Access-Control-Allow-Credentials 헤더는 true로 설정되어야 한다는 뜻이다. 그렇지 않으면 브라우저의 CORS 정책에 의해 응답이 거부된다. (인증 정보는 민감한 정보이기 때문에 출처를 정확하게 설정해주어야 한다.)

만일 이를 어길 경우 아래와 같은 또다른 종류의 CORS 에러 메세지가 발생한다.

- Access-Control-Allow-Credentials 설정을 안했을 경우
![](https://velog.velcdn.com/images/atoonatoo/post/85e89bda-2b28-4f7e-b5e5-1cc7b1fff9eb/image.png)

- Access-Control-Allow-Origin이 와일드카드(`*`)로 설정되어 있을 경우
![](https://velog.velcdn.com/images/atoonatoo/post/37678e6b-71e6-4ebf-80fd-2b71061faf9e/image.png)

- 위의 과정을 나타낸 그림

![](https://velog.velcdn.com/images/atoonatoo/post/7fc366c4-ae8f-4724-9b0e-88bb7b5de5b2/image.png)

참고로 인증된 요청 역시 예비 요청처럼 preflight가 먼저 일어난다.
위의 그림은 단순 GEET 요청이기 때문에 예비 요청은 생략 되었다.

---

## 3.4 CORS 3가지 시나리오 작동 체험 사이트

위의 3가지 CORS 시나리오를 코드로 미리 체험할 수 있는 사이트이다.

서버에서 설정 형태와 클라이언트에서의 요청 형태에 따라 CORS 에러가 나기도 하고 통과되기 하는 예제를 볼 수 있다.

https://chuckchoiboi.github.io/cors-tutorial/

![](https://velog.velcdn.com/images/atoonatoo/post/cf80cf7f-93f9-491e-b307-e760a0784f22/image.png)

메뉴 상단에 3가지 시나리오를 고를 수 있다.

![](https://velog.velcdn.com/images/atoonatoo/post/101bf97d-212b-436f-859e-94954ff9934d/image.png)

![](https://velog.velcdn.com/images/atoonatoo/post/dab05259-7060-4e46-91dc-476e8ac4eb56/image.png)

---

# 4. CORS 해결 방법

## 4.1 Chrome 확장 프로그램 이용

Chrome에서는 CORS 문제를 해결하기 위한 확장 프로그램을 제공한다.

아래의 링크에서 `Allow CORS: Access-Control-Allow-Origin` 크롬 확장 프로그램을 설치한다.

https://chromewebstore.google.com/detail/allow-cors-access-control/lhobafahddgcelffkeicbaginigeejlf?pli=1

설치가 완료되면 브라우저 오른쪽 상단에서 확장 프로그램을 활성화 시킬 수 있다.
해당 프로그램을 활성화시키게 되면, **로컬(localhost) 환경에서 API를 테스트 시, CORS 문제를 해결**할 수 있다.

서버 테스트 환경에서 고민하지 않고 빠르게 CORS를 해결하는 좋은 선택지일 것이다.

![](https://velog.velcdn.com/images/atoonatoo/post/6e20c984-8b85-417f-a823-123201edb3df/image.png)

---

## 4.2 프록시 사이트 이용하기

프록시(Proxy)란 클라이언트와 서버 사이의 중계 대리점이라고 보면 된다.

즉, 프론트에서 직접 서버에 리소스를 요청을 했더니 서버에서 따로 설정을 안해줘서 CORS 에러가 뜬다면, **모든 출처를 허용한 서버 대리점**을 통해 요청을 하면 되는 것이다.

![](https://velog.velcdn.com/images/atoonatoo/post/dfa2ca10-f1b9-40e0-b74a-1d5a9ff925a4/image.png)

다만 현재 무료 프록시 서버 대여 서비스들은 모두 악용 사례 때문에 **API 요청 횟수 제한을 두어 실전에서는 사용하기 무리**이다. 따라서 테스트용이나 맛보기용으로 사용하되, 실전에서는 직접 프록시 서버를 구축하여 사용하여야 한다.

---

### 4.2.1 heroku 프록시 서버

- https://cors-anywhere.herokuapp.com/corsdemo
- 위의 사이트로 가면 버튼을 누르고 데모 서버를 활성화 시킨다.
- 다만 시간 제한이 있기 때문에 일시적인 해결 방편이다.

![](https://velog.velcdn.com/images/atoonatoo/post/63c400e6-ead2-44e7-9774-e83c0664d1f6/image.png)

```javascript
const url = 'https://google.com' // 이 부분을 이용하는 서버 URL로 변경

fetch(`https://cors-anywhere.herokuapp.com/${url}`)
    .then((response) => response.text())
    .then((data) => console.log(data));
```

---

### 4.2.2 cors proxy app 프록시 서버

- https://github.com/raravel/cors-proxy

- axios 라이브러리 설치가 필요하다.

```html
<script src='https://cdnjs.cloudflare.com/ajax/libs/axios/1.1.3/axios.min.js'></script>
<script>
    axios({
        url: 'https://cors-proxy.org/api/',
        method: 'get',
        headers: {
            'cors-proxy-url' : 'https://google.com/' // 이 부분을 이용하는 서버 URL로 변경
        },
    }).then((res) => {
        console.log(res.data);
    })
</script>
```

---

### 4.2.3 cors.sh 프록시 서버

- https://cors.sh/
- 실전에서 이용하려면 유료 결제가 필요한 것 같다. (free도 가능하다.)

```javascript
const url = 'https://google.com' // 이 부분을 이용하는 서버 URL로 변경

fetch(`https://proxy.cors.sh/${url}`)
    .then((response) => response.text())
    .then((data) => console.log(data));
```

---

## 4.3 서버에서 Access-Control-Allow-Origin 헤더 세팅하기

직접 서버에서 HTTP 헤더 설정을 통해 출처를 허용하게 설정하는 가장 정석적인 해결책이다.
서버의 종류도 노드 서버, 스프링 서버, 아파치 서버 등 여러가지가 있다.

각 서버의 문법에 맞게 위의 HTTP 헤더를 추가해 주면 된다.

참고로 CORS에 연관된 HTTP 헤더 값으로는 다음 종류가 있다. (이들을 모두 설정할 필요는 없다.)

```html
# 헤더에 작성된 출처만 브라우저가 리소스를 접근할 수 있도록 허용함.
# * 이면 모든 곳에 공개되어 있음을 의미한다. 
Access-Control-Allow-Origin : https://naver.com

# 리소스 접근을 허용하는 HTTP 메서드를 지정해 주는 헤더
Access-Control-Request-Methods : GET, POST, PUT, DELETE

# 요청을 허용하는 해더.
Access-Control-Allow-Headers : Origin,Accept,X-Requested-With,Content-Type,Access-Control-Request-Method,Access-Control-Request-Headers,Authorization

# 클라이언트에서 preflight 의 요청 결과를 저장할 기간을 지정
# 60초 동안 preflight 요청을 캐시하는 설정으로, 첫 요청 이후 60초 동안은 OPTIONS 메소드를 사용하는 예비 요청을 보내지 않는다.
Access-Control-Max-Age : 60

# 클라이언트 요청이 쿠키를 통해서 자격 증명을 해야 하는 경우에 true. 
# 자바스크립트 요청에서 credentials가 include일 때 요청에 대한 응답을 할 수 있는지를 나타낸다.
Access-Control-Allow-Credentials : true

# 기본적으로 브라우저에게 노출이 되지 않지만, 브라우저 측에서 접근할 수 있게 허용해주는 헤더를 지정
Access-Control-Expose-Headers : Content-Length
```
---

### 4.3.1 Node.js 세팅

서버에 response Header 값으로 Access-Control 설정을 해준다.

```javascript
var http = require('http');

const PORT = process.env.PORT || 3000;

var httpServer = http.createServer(function (request, response) {
    // Setting up Headers
    response.setHeader('Access-Control-Allow-origin', '*'); // 모든 출처(orogin)을 허용
    response.setHeader('Access-Control-Allow-Methods', 'GET, POST, OPTIONS, PUT, PATCH, DELETE'); // 모든 HTTP 메서드 허용
    response.setHeader('Access-Control-Allow-Credentials', 'true'); // 클라이언트와 서버 간에 쿠키 주고받기 허용

    // ...

    response.writeHead(200, { 'Content-Type': 'text/plain' });
    response.end('ok');
});

httpServer.listen(PORT, () => {
    console.log('Server is running at port 3000...');
});
```

이때 `Access--Control-Allow-Origin` 헤더 값으로 `*`을 사용하면 모든 Origin에서 오는 요청을 허용한다는 의미이므로 당장은 편할 수 있겠지만, 바꿔서 생각하면 정체도 모르는 이상한 출처에서 오는 요청까지 모두 허용하기 때문에 보안상 위험하다.
그러니 가급적이면 번거롭더라도 다음과 같이 출처를 직접 명시해주어야 한다.

```javascript
response.setHeader('Access-Control-Allow-origin','https://github.com/atoonatoo');
```

---
### 4.3.2 Express.js 세팅

```shell
> npm i cors
```
```javascript
const express = require('express')
const cors = require("cors"); // cors 설정을 편안하게 하는 패키지
const app = express();

// ...

app.use(cors({
    origin: "https://naver.com", // 접근 권한을 부여하는 도메인
    credentials: true, // 응답 헤더에 Access-Control-Allow-Credentials 추가
    optionsSuccessStatus: 200, // 응답 상태 200으로 설정
}));

// ...
```
https://inpa.tistory.com/entry/NODE-%F0%9F%93%9A-CORS-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0-cors-%EB%AA%A8%EB%93%88

---
### 4.3.3 JSP / Servlet 세팅

```java
import javax.servlet.*;

public class CORSInterceptor implements Filter {

    private static final String[] allowedOrigins = {
            "http://localhost:3000", "http://localhost:5500", "http://localhost:5501",
            "http://127.0.0.1:3000", "http://127.0.0.1:5500", "http://127.0.0.1:5501"
    };

    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        HttpServletRequest request = (HttpServletRequest) servletRequest;

        String requestOrigin = request.getHeader("Origin");
        if(isAllowedOrigin(requestOrigin)) {
            // Authorize the origin, all headers, and all methods
            ((HttpServletResponse) servletResponse).addHeader("Access-Control-Allow-Origin", requestOrigin);
            ((HttpServletResponse) servletResponse).addHeader("Access-Control-Allow-Headers", "*");
            ((HttpServletResponse) servletResponse).addHeader("Access-Control-Allow-Methods",
                    "GET, OPTIONS, HEAD, PUT, POST, DELETE");

            HttpServletResponse resp = (HttpServletResponse) servletResponse;

            // CORS handshake (pre-flight request)
            if (request.getMethod().equals("OPTIONS")) {
                resp.setStatus(HttpServletResponse.SC_ACCEPTED);
                return;
            }
        }
        // pass the request along the filter chain
        filterChain.doFilter(request, servletResponse);
    }

    private boolean isAllowedOrigin(String origin){
        for (String allowedOrigin : allowedOrigins) {
            if(origin.equals(allowedOrigin)) return true;
        }
        return false;
    }
}
```

---
### 4.3.4 Spring 세팅

```java
// 스프링 서버 전역적으로 CORS 설정
@Configuration
public class WebConfig implements WebMvcConfigurer {
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
        	.allowedOrigins("http://localhost:8080", "http://localhost:8081") // 허용할 출처
            .allowedMethods("GET", "POST") // 허용할 HTTP method
            .allowCredentials(true) // 쿠키 인증 요청 허용
            .maxAge(3000) // 원하는 시간만큼 pre-flight 리퀘스트를 캐싱
    }
}
```

```java
// 특정 컨트롤러에만 CORS 적용하고 싶을때.
@Controller
@CrossOrigin(origins = "*", methods = RequestMethod.GET) 
public class customController {

	// 특정 메소드에만 CORS 적용 가능
    @GetMapping("/url")  
    @CrossOrigin(origins = "*", methods = RequestMethod.GET) 
    @ResponseBody
    public List<Object> findAll(){
        return service.getAll();
    }
}
```

---
### 4.3.5 Apache 세팅

httpd.conf에서 `<Ifmodule mod_headers.c>` 태그 안에 헤더 설정을 넣어준다. 또는 VirualHost 부분에 넣어도 된다.

```xml
<IfModule mod_headers.c>
	Header set Access-Control-Allow-Origin "*"
</IfModule>
```

---
### 4.3.6 Tomcat 세팅

톰캣 폴더 경로의 conf/web.xml 혹은 webapps 내의 프로젝트 폴더 내 WEB-INF/web.xml 파일에 아래 헤더 설정을 추가한다.

```xml
<filter>
    <filter-name>CorsFilter</filter-name>
    <filter-class>org.apache.catalina.filters.CorsFilter</filter-class>
    <init-param>
        <param-name>cors.allowed.origins</param-name>
        <param-value>*</param-value>
    </init-param>
    <init-param>
        <param-name>cors.allowed.methods</param-name>
        <param-value>GET,POST,HEAD,OPTIONS,PUT,DELETE</param-value>
    </init-param>
    <init-param>
        <param-name>cors.allowed.headers</param-name>
        <param-value>Content-Type,X-Requested-With,accept,Origin,Access-Control-Request-Method,Access-Control-Request-Headers</param-value>
    </init-param>
    <init-param>
        <param-name>cors.exposed.headers</param-name>
        <param-value>Access-Control-Allow-Origin,Access-Control-Allow-Credentials</param-value>
    </init-param>
    <init-param>
    	<!-- 쿠키 통신을 안하는데 이걸 true로 하면 4XX 서버 에러가 뜬다 -->
        <param-name>cors.support.credentials</param-name>
        <param-value>false</param-value> 
    </init-param>
    <init-param>
        <param-name>cors.preflight.maxage</param-name>
        <param-value>10</param-value>
    </init-param>
</filter>
<filter-mapping>
    <filter-name>CorsFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
```
---

### 4.3.7 Nginx
nginx.conf 파일 안에 `location /` 부분에 add_header 값으로 헤더 설정을 추가
```json
location / {
    root html;
    add_header 'Access-Control-Allow-Origin' '*';
    index  index.html index.htm;
}
```
---

### 4.3.8 AWS (S3 호스팅)

1. S3 콘솔 메뉴에 들어가 버킷을 선택한다.
2. 권한(Permissions) 탭을 선택한다.
3. 교차 출처 리소스 공유 창에서 `편집` 선택한다.
4. 텍스트 상자에 아래 JSON CORS 규칙을 입력한다.

![](https://velog.velcdn.com/images/atoonatoo/post/a6638cc1-6404-4f55-87b5-8cf7a2e2750c/image.png)

```JSON
[
  {
    "AllowedHeaders": [
      "Authorization"
    ],
    "AllowedMethods": [
      "GET",
      "HEAD"
    ],
    "AllowedOrigins": [
      "http://www.example.com"
    ],
    "ExposeHeaders": [
      "Access-Control-Allow-Origin"
    ]
  }
]
```

---
# 5. CORS 해결 방법 내부 동작

---

# 6. 추가적으로 알아야 하는 CORS 사례

## 6.1 CORS의 보안 취약점 가이드

원래 SOP 정책으로 막혔어야할 외부 리소스들이 CORS 정책으로 억지로 뚫어줬으니 공격에 그대로 노출되는건 당연한 수순일지도 모른다. 

예시로 CORS 정책에 대해 서버에서 너무 유연하게 리소스 허용 설정을 하게 될 경우, 해당 웹어플리케이션의 흐름을 악용하여 타인의 개인 정보를 해킹할 위험성이 있게 된다.

대표적으로 허용할 도메인들은 설정하기 귀찮다고 와일드카드(`*`)로 퉁치는걸 들 수 있다.
즉, 서버 개발자가 CORS 정책을 잘못 구성할 경우 심각한 보안 위협이 될 수 있다.

이에 대한 보안 문제점 예방 가이드는 다음 포스팅에서 공부하고 다뤄보도록 하겠다.

---

## 6.2 Chorme PNA CORS 문제

만일 위에서 본 일반적인 CORS 에러 메세지가 아닌 아래와 같은 또 다른 CORS 에러 메세지가 나왔다면, 별도의 사설망 접근(private network access)에 대한 지식이 필요하다.

![](https://velog.velcdn.com/images/atoonatoo/post/41d75cc4-24cb-4a56-94b9-e0b1ba000c23/image.png)

쉽게 말하면 **공인 네트워크의 웹사이트에사ㅓ 사설 네트워크의 리소스를 호출**할 때 사설망 접근 관련 CORS 에러가 뜨게되는데, 자세한 내용은 마찬가지로 다음 포스팅에 다뤄볼 것이다.

---

## 6.3 브라우저 Cache에 의한 CORS 문제

브라우저는 기본적으로 이미지와 같은 고용량 리소스에 대해서 한번 요청해서 응답받으면 자동으로 cache하여 저장해놓는다. 그러면 나중에 똑같은 리소스를 재요청해도 캐시 저장소에서 끝어다 쓰면 네트워크 통신없이 빠르게 가져올 수 있어 성능 상 굉장한 이점을 얻기 때문이다.

그러나 이 캐시 기능 떄문에 최신 리소스 불일치 현상 및 여러가지 자잘한 문제점이 존재한다는 단점이 존재한다. 즉, CORS 역시 이러한 캐시 문제 때문에 발생할 수도 있다.

---

# 참고 문헌

1. https://enjoydev.life/blog/frontend/10-cors
2. https://yses9296.tistory.com/97
3. https://xiubindev.tistory.com/115
4. https://innovation123.tistory.com/242
5. https://www.youtube.com/watch?v=BQykNALA2WA&pp=ygULY29ycyDsl5Drn6w%3D
6. https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-CORS-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95-%F0%9F%91%8F
7. https://inpa.tistory.com/entry/NODE-%F0%9F%93%9A-CORS-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0-cors-%EB%AA%A8%EB%93%88

---
