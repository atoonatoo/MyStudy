

----
##### 연결 문서

- [[자료구조(Data Structures)]]
---

- 컬렉션 프레임워크란?
	컬렉션은 다수의 데이터, 프레임워크는 표준화된 프로그래밍 방식을 의미한다. 
	따라서 컬렉션 프레임워크란 데이터 그룹을 저장하는 클래스들을 표준화하는 설계이다.
	컬렉션 프레임우크를 활용하면 객체 지향적이고 재사용성이 높은 코드를 작성할 수 있다.
	
	
- 컬렉션 프레임워크의 상속 계층도
	- 주요 인터페이스로는 List, Set, Map이 있다.
	
	
- 각 인터페이스의 특징과 구현 클래스
	- List
		- 순서 유지, 저장, 중복 저장 O
		- ArrayList, Vector, Stack, Linkdlist 등
	- Set
		- 순서 유지, 저장, 중복 저장 X
		- HashSet, TreeSet 등
	- Map
		- 키와 값을 쌍으로 저장, 순서 유지 X, 키 중복 저장 X
		- HashMap, Hashtable, TreeMap, Properties