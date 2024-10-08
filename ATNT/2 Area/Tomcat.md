

----
##### 연결 문서

- 
- 
- 
---

##### 제목 : 
    - Tomcat
        
        ```java
        - 아파치(apache)란? : 
        	세계에서 가장 많이 쓰는 웹 서버중 하나이며, 
        	아파치 소프트웨어 재단에서 관리하는 HTTP 웹 서버이다.
        	Apache는 Apache재단에서 만든 HTTP서버로 워낙 다양한 추가기능에, 
        	구축이 쉽다는 이유 때문에 많이 쓰고 있다. 
        	대부분의 중소기업들은 무료이기 때문에 많이 쓰인다.
        
        - 톰캣이란(Tomcat)? : 
        	톰캣은 아파치 소프트웨어 재단의 웹 어플리케이션 서버(와스)로서, 
        	자바 서블릿을 실행키고 JSP코드가 포함되어 있는 웹 페이지를 만들어준다. 
        	자바 서블랫과 JSP 규격의 '참조용 구현'으로 평가되고 있는 톰캣은, 
        	개발자들의 개방적 협력 작업의 산물로 바이너리 버전과 
        	소스코드 버전 둘 모두를 아파치 웹 사이트에서 얻을 수 있다. 
        	즉, 톰캣은 웹 서버에서 넘어온 동적인 페이지를 읽어들여 프로그램을 실행하고 
        	그 결과를 다시 html로 재구성하여 아파치에게 되돌려 준다. 
        	톰캣은 자체적으로 보유하고 있는 
        	내부 웹 서버와 함께 독립적으로 사용될 수도 있지만 
        	아파치나 넷스케이프 엔터프라이즈 서버, IIS등 다른 웹서버와 함께 사용될 수도 있다.
        	톰캣을 실행시키기 위해서는 JRE 1.1이상에 부합되는 자바 런타임 환경이 필요하다.
        
        - 아파치(웹서버)와 톰캣(와스)의 차이점 : 
        	* Apache 아파치 =  Web Server 웹서버 먼저 아파치는 SW단체 이름이고 
        	우리가 흔히 알고있는 아파치 서버라는 것은 이곳에서 후원 지원하는 
        	http Web Server를 지칭하는 말이다.
        	즉 "아파치는 Web Server 중 하나인 것!" 
        	하도 유명해서 아파치=웹서버 처럼 익히 알고있는 것일뿐 .. 
        	(ex. DB=oracle, mysql.. 처럼.)
        		
        		& Web server: http 요청을 처리하는 웹서버.
        
        	* Tomcat 톰캣 = WAS 와스 톰캣은 흔히 와스 WAS(Web application Server)라고 한다.
        		와스는 웹 서버와 서블릿 컨테이너의 결합으로 다양한 역할 수행하는 서버다. 
        		같은 아파치(sw단체)에서 만들었기 때문에 아파치 톰캣이다.  
        		클라이언트 요청을 받아 요청을 처리하고 
        		다시 클라이언트에게 응답해주는 역할하는것이 서블릿 컨테이너이다. 
        		아파치와 웹 서버와의 차이의 핵심은 
        		이 컨테이너 기능(웹서버 + 서블릿 )이 가능한가 / 불가능한가이다. 
        
        - 정리 : 
        	웹서버 Web Server : 정적인 데이터 처리하는 서버.
        	단순 이미지나 html파일과 같은 리소스만을 제공하는 서버는 
        	웹서버만 사용하여 빠르고 안정적이게 활용.
        	
        	와스 WAS : 동적인 데이터 처리하는 서버.
        	DB로 연결되어 데이터를 주고받거나 자바등을 통해 
        	데이터 조작이 필요한 경우에는 WAS를 활용.
        	server start 시 가장 먼저 읽어들이는 내용: Web.xml web.xml을 기반으로 
        	서버가 돌아가기 위해 필요한 내용 읽어들인다.
        
        - 왜 아파치와 톰캣을 연동하는 것인가? : 
        	와스에도 웹서버기능이 있는데 왜??  Web Server와 WAS를 같이 사용하는 것인가?
        	
        	"다음에 알아보자.."
        ```
        
        ![WAS.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/11b23e09-5eeb-440a-86c3-5fb272d32444/674aa5b9-7d57-4409-a8e0-5e36743dd4e9/WAS.png)