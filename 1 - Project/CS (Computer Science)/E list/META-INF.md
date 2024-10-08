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

- META-INF란 Java 아카이브 ([[Jar (Java ARchive)]], [[War (Web Arichive)]], [[Ear]] 등) 파일의 [[Root Directory]]에 위치한 특별한 디렉토리로, 
  어플리케이션이나 라이브러리에 대한 [[META-DATA]]를 저장하는데에 사용된다. 

##### 주요 역할

- **MANIFEST.MF 파일**
    - JAR 파일의 메타데이터를 담고 있으며, 메인 클래스 지정이나 클래스패스 설정 등 애플리케이션의 동작을 정의한다.
      
-  **보안 및 서명 파일
	- `.SF`, `.DSA`, `.RSA` 등의 파일을 통해 JAR 파일의 무결성과 출처를 검증하여 보안을 강화한다.
	  
-  **서비스 로더 구성 파일**
    - `META-INF/services/` 디렉토리에 위치하며, 특정 인터페이스의 구현체를 런타임에 동적으로 로드하기 위한 설정을 제공한다.
      
-  **프레임워크 설정 파일**
    - Spring 등의 프레임워크에서 추가 설정이나 확장 기능을 지원하기 위해 사용된다.
      
-  **라이선스 및 법적 정보**:
    - `LICENSE`, `NOTICE` 등의 파일로 라이브러리나 애플리케이션의 라이선스와 법적 정보를 제공한다.

##### 요약
- META-INF 디렉토리는 Java 애플리케이션의 실행, 보안, 확장성 등에 필요한 중요한 메타데이터를 포함하여 
  애플리케이션의 원활한 배포와 실행을 지원한다.