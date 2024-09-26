---
created: 2024-01-04
updated: 2024-09-14
---
----
##### 연결 문서

- 
- 
- 
---

# **README**

- MAINFAST.MF이란 Java 어플리케이션의 [[Jar (Java ARchive)]] 파일 안에 포함된 [[META-DATA]] 파일로, 
  JAR 파일의 동작과 특성을 정의하는데 사용된다.
- 이 파일은 JAR [[Root Directory]] 내 [[META-INF]] 폴더에 위치하여 JAR 파일의 배포 및 실행에 다양한 정보를 담고 있다. 

##### 주요 역할 및 내용

- 메인 클래스 지정
	- 실행 가능한 JAR 파일에서 프로그램의 시작점을 지정한다.
	- 예: `Main-Class: com.example.Main`
	  
- CLASS PATH 설정
	- 어프리케이션이 의존하는 외부 라이브러리나 JAR 파일의 경로를 지정한다.
	- 예: `Class-Path: lib/library1.jar lib/library2.jar`
	  
- 버전 및 작성자 정보
	- 어플리케이션 버전, 작성자, 라이센스 등의 메타데이터를 포함할 수 있다.
	- Implementation-Title: MyApplication
	- Implementation-Version: 1.0.0
	- Implementation-Vendor: MyCompany
	
- 보안 서명 및 인증
	- JAR 파일의 무결성과 출처를 검증하기 위한 디지털 서명 정보가 포함될 수 있다.
	
- 확장 및 패키지 정보
	- 확장 기능이나 패키지의 의존성 정보를 명시하여 런타임 시 필요한 구성 요소를 확인한다.
	  
##### MANIFEST.MF 사용 방법
	
- JAR 생성 시 포함
	- jar 명령어의 `-m` 옵션을 사용하여 사용자 정의 MANIFEST.MF를 포함할 수 있습니다.
	- jar cfm MyApp.jar MANIFEST.MF -C bin/ .
    
- 자동 생성 및 수정
	- 빌드 도구(Maven, Gradle 등)를 사용하면 MANIFEST.MF를 자동으로 생성하거나 수정할 수 있습니다.
	
- 주의 사항
	
	- 파일 인코딩
	    - MANIFEST.MF는 UTF-8 인코딩을 사용해야 한다.
	- 공백 및 줄바꿈
	    - 속성명과 콜론 사이에 공백이 없어야 하며, 콜론과 값 사이에는 반드시 한 칸의 공백이 있어야 한다.
	    - 줄바꿈은 반드시 CRLF(Carriage Return + Line Feed)로 해야 한다.
	- 속성명 대소문자
	    - 속성명은 대소문자를 구분하지 않는다.

##### 결론

- MANIFEST.MF는 Java 애플리케이션의 배포 및 실행을 위한 중요한 메타데이터를 담고 있는 파일로, 
  특히 실행 가능한 JAR 파일을 만들 때 필수적인 요소이다. 
  이 파일을 적절히 구성하면 애플리케이션의 배포와 실행이 보다 원활해진다.
