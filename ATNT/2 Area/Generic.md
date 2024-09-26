---
created: 2024-04-12
updated: 2024-09-14
---


----
##### 연결 문서

- [[ATNT/ATNT/2 Area/Java|Java]]
- 
- 
---

##### Generic
- Generic이란?
- 컴파일 타임에 타입을 체크함으로써 코드의 안정성을 높여주는 기능

- 제네릭을 사용하는 이유
	1. 컴파일 타임에 강력한 타입 검사
	- 제네릭 미사용
	```java 
	List stringList = new ArraayList<>();
	stringList.add("woowacourse");
	stringList.add(1);
	String result = (String) stringList.get(0) + (String) stringList.get(1);

	```
	- 제네릭 사용
	```java
	List<String> stringList = new ArrayList<>();
	stringList.add("woowacourse");
	stringList.add(1);
	```

	2. 캐스팅(형 변환) 제거
	- 제네릭 미사용
	```java
	List stringList = new ArrayList<>();
	stringList.add("woowacourse");
	String result = (String) stringList.get(0);
	```
	- 제네릭 사용
		```java
	List<String> stringList = new ArrayList<>();
	stringList.add("woowacourse");
	String result = stringList.get(0);
	```

- 배열 vs 제네릭 타입
	- 공변 : 배열은 Integer가 Obeject의 하이타입 O
	- 무공변 : 제네릭에서는 Integer가 Obeject 하이타입 X
	  
- 변성
	- 무공변(Invariance) - 
	- 공변(Covariance) - 
	- 반공변(Contravariance) - 
	  
- 제네릭 타입(Generic Types)
	```java
	Class<T>, interface<T>
	```
	
- 제네릭 메서드(Generic Methods)
    
- 제네릭 타입 제한의 필요성

- 제한된 제네릭 타입
	```java
	class NoodleCategory <T extends Noodle> {
	}
	```
	
- 와일드카드
	```java
	1) <?> : 모든 타입이 가능
	2) <? extends Nodle> Upper Bounded Wildcards 상한 경계 : 
	   Noodle과 Noodle의 하위 타입만
	3) <? super Noodle> Lower Bounded Wildcards 하한 경계
	   Noodle과 Noodle의 상위 타입만
	```
	
- 와일드 카드 - 제한
	  
- 와일드 카드를 언제 무엇을 써야하는가?
	- PECS
		- producer - extends : 생성을 하는 곳은 extends
		  consumer - super : 소비를 하는 곳은 super
	
- 제네릭 타입 소거
	
	
- 출처 : https://www.youtube.com/watch?v=w5AKXDBW1gQ