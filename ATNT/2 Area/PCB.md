---
created: 2024-01-04
updated: 2024-09-14
---


----
##### 연결 문서

- [[Operation System]]
- [[Context Swiching]]
- [[ATNT/ATNT/2 Area/Meta Data]]
- [[Process]]
- [[ATNT/2 Area/Kernel]]
---

##### 제목 : PCB | Process Control Back 


- PCB란? 

	- 운영체제가 프로세스를 제어하기 위해 정보를 저장하는 공간으로 프로세스의 상태를 정보를 저장한다. PCB는 프로세스의 상태 관리와 Context Swiching에 있어서 필수이다.
	
	- 이러한 PCB는 프로세스 생성 시 만들어지며 메모리에 저장된다. 
	
	- 프로세스가 생성될 때마다 고유의 PCB가 생성되며, 프로세스가 완료되면 PCB는 제거된다.

- PCB의 구조

	1. Process ID : 프로세스를 구분하는 ID
	2. Procesee State : 각 State들의 상태를 저장
	3. Program Counter : 다음 Instruction의 주소를 저장하는 카운터. CPU는 이 값을 통 Process의 Instruction을 수행
	4. Register : Accumulater, CPU Register, General Register 등을 포함.
	5. CPU Scheduling Information : 우선 순위, 최종 실행시간, CPU 점유율 등이 포함
	6. Memory Information : 해당 프로세스 주소공간 (lower bound ~ upper bound) 정보를 저장
	7. Process Information : (페이지 테이블, 스케줄링, 큐 포인터, 소유자, 부모 등)
	8. Device I/O Status (프로세스에 할당된 입출력 장치 목록, 열린 파일 목록 )
	9. Pointer : 부모/자식 프로세스에 대한 포인터, 자원에 대한 포인터 등
	10. Open File List : 프로세스를 위해 열려있는 파일의 리스트

	![[PCB의 구조.png]]

