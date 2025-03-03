---
created: 2024-01-04
updated: 2024-09-14
---


----
##### 연결 문서


- [[6 - ATNT/2 Area/Operation System]]
- [[System Call]]
---

##### 제목 : Interrupt / 인터럽트


- Interrupt란
	시스템에서 발생한 다양한 종류의 이벤트 혹은 그런 이벤트를 알리는 메커니즘

- Interrupt의 종류 - 예시
	- 전원(Power)에 문제가 생겼을 때
	- I/O 작업이 완료되었을 때
	- 시간이 다 되었을 때 (timer 관련)
	- 0으로 나눴을 때 (trap이라고도 부른다.)
	- 잘못된 메모리 공간에 접근을 시도할 때 (trap이라고도 부른다.)

- Interrupt의 종류
	- 하드웨어 이벤트 처리
	- 시스템 호출 및 서비스 요청
	- 예외 처리
	- 시스템 스케줄링 및 관리 
	- 입출력 처리

- Interrupt Handler / Interrupt Service Routine, ISR)

	- "실제 인터럽트를 처리하기 위한 루틴"
	
	인터럽트가 발생하면 이를 핸들링하기 위해 함수가 호출되는데 이를 이벤트 핸들러라고 한다.
	예를 들어, 키보드 자판을 눌러서 인터럽트가 발생하면 키보드 인터럽트를 처리하는
	키보드 인터럽트 이벤트 핸들러가 호출된다. 
	마찬가지로 스마트폰에서 화면을 손으로 만지면 터치 인터럽트가 발생하고, 
	터치 인터럽트를 처리하는 터치 인터럽트 핸들러가 호출된다.
	
	![[디바이스 별로 실행되는 인터럽트 핸들러.png]]

	인터럽트 핸들러는 함수 형태로 존재하며, 커널 내의 인터럽트 함수에서 호출한다.
	이처럼 인터럽트가 발생해 지정한 인터럽트 핸들러가 동작하려면 request_irq() 함수를 
	적절한 인자와 함께 호출해서 미리 인터럽트 핸들러를 등록해 주어야 한다.
	
	
	
	- 마우스를 움직였을 때 마우스 인터럽트 핸들러를 호출하는 과정
	![[마우스를 움직였을 때 마우스 인터럽트 핸들러를 호출하는 과정.png]]
	
