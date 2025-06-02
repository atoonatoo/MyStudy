
---
- [[CS]]
---

![](https://velog.velcdn.com/images/atoonatoo/post/554a6a54-d5ec-4b1a-8a69-45c1d0e2eb66/image.png)


### 1. Java SE(Standard Edition) API

Java SE API는 Java 애플리케이션에서 필요한 기본적인 기능을 제공하는 표준 라이브러리이다. 

Java 프로그래밍 언어로 작성된 애플리케이션에서 다양한 기능을 구현할 수 있도록 도와주는 클래스를 포함하고 있다.

---

### 2. 역할
- 기본 기능 제공
	다양한 기본 기능을 제공하여 애플리케이션 개발을 쉽게 만들 수 있다. 예를 들어, 데이터 구조, 입출력, 네트워킹, 보안 등을 다룸.

- 플랫폼 독립성 보장
Java 애플리케이션이 운영 체제에 종속되지 않도록 해줌. JVM을 통해 다양한 운영 체제에서 실행될 수 있음.

- 재사용성 및 확장성 제공
	코드의 재사용을 촉진하고, 기존 클래스를 활용해 쉽게 확장 가능함.
    
- 모듈화된 설계
	다양한 모듈로 나뉘어 있어 필요한 기능만 선택적으로 사용 가능함.

---

### 3. 패키지 내의 기능 종류

Java SE API는 여러 패키지로 나누어져 있으며, 각 패키지는 다양한 기능을 제공함. 주요 패키지와 그 기능은 다음과 같다.

- java.lang: 기본적인 클래스들을 제공함.
	예: String, Math, Object, Thread, System

- java.util: 데이터 구조 및 유틸리티 클래스를 제공함.
	예: ArrayList, HashMap, Date, Collections, Iterator

- java.io: 파일 입출력 및 데이터 스트림 처리 관련 기능을 제공함.
	예: File, InputStream, OutputStream, BufferedReader, PrintWriter
    
- java.nio: 고성능의 비동기 I/O 기능을 제공함.
	예: Buffer, Channel, Path, Files

- java.net: 네트워크 관련 기능을 제공함.
	예: Socket, URL, URLConnection, HttpURLConnection

- java.math: 수학적 계산을 위한 기능을 제공함.
	예: BigDecimal, BigInteger

- java.time: 날짜와 시간 관련 기능을 제공함.
	예: LocalDate, LocalTime, ZonedDateTime, Duration

- java.sql: 데이터베이스 연결 및 SQL 처리를 위한 기능을 제공함.
	예: Connection, Statement, ResultSet, PreparedStatement

- javax.swing: GUI 애플리케이션을 위한 컴포넌트를 제공함.
	예: JFrame, JButton, JLabel, JPanel

- java.security: 보안 관련 기능을 제공함.
	예: MessageDigest, KeyPair, SecurityManager

- java.util.concurrent: 멀티스레딩 및 동시성 관련 기능을 제공함.
	예: ExecutorService, CountDownLatch, Semaphore, AtomicInteger



