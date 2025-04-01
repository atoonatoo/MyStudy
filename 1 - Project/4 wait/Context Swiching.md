---
created: 2024-01-04
updated: 2024-09-14
---


----
##### 연결 문서

- [[6 - ATNT/2 Area/Operation System]]
- [[PCB]]
- [[Process]]
- [[Thread]]
- [[System Call]]
- [[Interrupt]]
---

##### 제목 : Context Swiching / 문맥 교환

- Context Swiching이란?
	프로세스나 스레드 간

- Context Swiching이 필요한 이유 
	- CPU는 한 번에 하나의 프로세스만 수행할 수 있다. 
	
	- 하지만, 실생활에서 우리는 여러 개의 프로세스를 동시에 수행하려고 한다.
		- ( ex : 유튜브를 보며 인터넷 하기)
	
	- 따라서 CPU는 동시에 수행하는 것처럼 보이게 하기 위해서 여러 개의 프로세스를 번갈아가며 수행한다. 
		- (아주 빠른 속도로 번갈아가며 수행하는 기에 동시에 실행 되는 것처럼 보인다.)
	- 이렇게 CPU가 프로세스를 바꿔가며 실행하기 위해서 Context Swiching이 필요한 것이다.

- Context Swiching 과정

	1. Process P1이 실행되는 도중 인터럽트나 시스템 콜이 발생한다.
	2. PCB1에 P1의 정보를 저장하고, PCB2의 상태를 불러온다.
	3. Process의 P2를 실행한다. 
	4. P2가 실행되는 도중 인터럽트나 시스템 콜이 발생한다.
	5. PCB2에 P2의 정보를 저장하고 PCB1의 상태를 불러온다. 
	6. Process P1을 실행한다.

- Context Swiching Overhead란?
	프로세스가 바뀌는 과정을 Context Swiching이라고 하는데 이 과정에서 프로세스가
	실행되기 전까지의 기다리는 시간, 메모리를 오버헤드라고 한다. 

	간단하게 이야기하자면 저장하고 불러오는 과정이다.
