
### 1. JDK란 무엇인가?
JDK는 Java Development Kit의 약자로, 자바 애플리케이션을 개발하고 실행하기 위한 소프트웨어 개발 도구이다. 

자바 컴파일러, 디버거, JVM(Java Virtual Machine) 등을 포함하여 개발자가 자바 프로그램을 작성하고 실행할 수 있도록 지원하며,

JDK는 JRE(Java Runtime Environment)와 JVM을 포함한 자바 개발의 핵심 도구로 간주된다.

---

### 2. JDK의 특징

- 플랫폼 독립성 - JDK로 개발한 자바 애플리케이션은 다양한 운영체제에서 실행 가능함.

- 다양한 개발 도구 - 컴파일러, 디버거, 패키지 관리 도구 등을 제공함.

- 표준 라이브러리 포함 - 풍부한 자바 API 라이브러리를 포함하여 다양한 개발 작업을 지원함.

- 정기적 업데이트 - 성능 향상과 보안 강화를 위해 주기적으로 업데이트됨.

---

### 3. JDK의 구성 요소

- 자바 컴파일러 (javac)
자바 소스 코드를 바이트코드(.class 파일)로 변환.

- 자바 가상 머신 (JVM)
바이트코드를 실제 기계어로 변환하여 실행함.

- 자바 런타임 환경 (JRE)
	- JRE는 자바 애플리케이션을 실행하기 위한 환경이다.
	- JVM, 표준 라이브러리, 구성 파일 등을 포함하여 자바 애플리케이션이 원활히 동작하도록 한다.

- JDK와 JRE의 관계:
JDK는 개발 및 실행 환경을 포함하며, JRE는 실행 환경에 초점이 맞춰짐.
JDK 안에 JRE가 포함되어 있음.

- JRE의 주요 구성 요소:
JVM: 바이트코드를 실행하는 가상 머신.
클래스 라이브러리: 자바 애플리케이션 실행에 필요한 표준 라이브러리.
런타임 파일: JVM의 실행에 필요한 구성 파일과 리소스.


- 표준 라이브러리
자바 프로그래밍에 필요한 기본 클래스와 API 모음을 포함함.

   - 도구
	- jdb: 디버깅 도구
	- jar: 자바 아카이브 관리 도구
	- javadoc: 문서 생성 도구 등 다양한 유틸리티 제공.

---

### 4. JDK 버전 업데이트 내용

- JDK 8 (2014)
람다 표현식, 스트림 API, 새로운 날짜/시간 API 등이 추가됨. 함수형 프로그래밍 스타일을 도입함.

- JDK 9 (2017)
모듈 시스템(JPMS) 도입. 대규모 애플리케이션을 모듈 단위로 관리할 수 있게 함. JShell(대화형 자바 쉘) 추가됨.

- JDK 10 (2018)
지역 변수 타입 추론(var) 추가로 코드가 간결해짐.

- JDK 11 (2018)
장기 지원(LTS) 버전으로, 새로운 HTTP 클라이언트 API와 람다 표현식에서 var 사용 가능해짐.

- JDK 12 - 17 (2019 - 2021)
패턴 매칭, 레코드, 스위치 표현식 개선, 텍스트 블록 등 추가됨. 코드 가독성과 생산성이 높아짐.

- JDK 18 (2022)
패턴 매칭과 벡터 API에 대한 개선이 이루어짐.

---

### 5. JDK 종류

- Java SE (Standard Edition)
표준 자바 플랫폼으로, 일반 애플리케이션 개발을 지원함.

- Java EE (Enterprise Edition)
기업 환경에 적합한 플랫폼으로, 웹 애플리케이션 서버 기능을 포함함.

- Java ME (Micro Edition)
자원이 제한된 모바일 장치와 임베디드 시스템을 위한 플랫폼임.

- OpenJDK
오픈소스 기반의 JDK로, 무료로 사용 가능함.

---

### 6. JDK 개발 생명주기

![](https://velog.velcdn.com/images/atoonatoo/post/dcfddc32-f0eb-4a0d-9880-968e50b3dfe2/image.png)

1. JDK

- 소스 코드 작성 → 컴파일(javac) → 바이트코드 생성(.class 파일).

2. JRE

- 컴파일된 프로그램(.class 파일)을 실행하기 위해 필요한 런타임 환경(JRE)을 통해 실행.

3. JVM

- JVM은 JRE 안에 포함되어 실행 엔진 역할을 수행하며, 바이트코드를 OS가 이해할 수 있는 기계어로 변환하여 프로그램 실행.