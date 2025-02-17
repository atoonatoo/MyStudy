

----
##### 연결 문서

- [[6 - ATNT/2 Area/Operation System]]
- [[Process]]
---

##### 제목 : Inter-Process-Communication / IPC / 프로세스 간 통신

- IPC란 

	"프로세스 들 사이에서 서로 데이터를 주고 받는 행위 또는 그에 대한 방법이나 경로"
	
	운영체제 상에서 실행 중인 프로세스 간에 정보를 주고받는 것을 프로세스간 통신이라고 한다.
	프로세스는 자신에게 할당된 메모리 내의 정보만 접근할 수 있다. 
	이는 안전성을 위해 운영체제에서 자기 프로세스의 메모리만 접근하도록 
	강제하고 있다는 것이다.
	
	 따라서 한 프로그램에서 병렬성을 키우면서 공유되는 데이터를 사용하기 위해 메모리 공간을 
	 공유하는 스레드를 이용하는 경우가 많다. 하지만 이것은 하나의 프로그램에서만 의미가 
	 있는 것이고, 서로 다른 프로그램(즉, 서로 다른 프로그램)의 데이터를 공유하려면 
	 결국 다른 프로세스의 메모리를 접근할 필요가 발생한다. 
	 따라서 이 때는 IPC라는 것을 사용하게 된다.

- IPC의 특징

- IPC의 종류
	- PIPE (Anonymous PIPE)
		파이프는 두 개의 프로세스를 연결하게 되고, 하나의 프로세스는 데이터를 쓰기만, 
		다른 하나는 데이터를 읽기만 할 수 있다. 한쪽 방향으로만 통신이 가능한 파이프의
		특징 떄문에 Half-Duplex(반이중) 통신이라고 부르기도 한다.
		파이프같은 반이중 통신의 경우 읽기나 쓰기 중 하나만 가능하므로 만약 읽기/쓰기
		둘다 사용하고 싶다면 두개의 파이프를 만들어야만 가능하다.
		
		장점 : PIPE는 매우 간단하게 사용할 수 있다. 
		만약 한쪽 프로세스가 단지 읽기만 하고 다른 쪽 프로세스는 단지 쓰기만 하는, 
		단순한 데이터 흐름을 가진다면 고민 없이 PIPE를 사용하면 된다. 
		
		단점 : 반이중 통신이라는 점으로 만약 프로세스가 읽기와 쓰기 통신을 모두 해야 한다면
		PIPE를 두개 만들어야 하는데 구현이 꽤나 복잡해질 수 있다.
		만약 전이중 통신을 고려해야될 상황이라면 PIPE는 좋은 선택이 아니라고 보여진다.
	
	- Named Pipe(FIFO)
		익명 파이프(Pipe)는 통신을 할 프로세스가 명확하게 알 수 있는 경우 사용한다.
		예를 들어 자식과 부모 프로세스 간 통신의 경우에 사용할 수 있으며, 
		Named PIPE는 전혀 모르는 상태의 프로세스들 사이의 통신의 경우 사용한다.
		익명 파이프(PIPE)의 단점으로 같은 PPID(같은 부모 프로세스)를 가지는 
		프로세스들 사이에서만 통신이 가능하지만, Named PIPE는 그 부분을 해결한, 
		PIPE의 확장이라고 할 수 있다. Nmaed PIPE는 부모 프로세스와 무관하게 
		전혀 다른 모든 프로세스들 사이에서 통신이 가능하다.
		
		이유 : 프로세스 통신을 위해 이름이 있는 파일을 사용하기 때문이다.
		Named PIPE의 생성은 mkfifo를 통해 이뤄지는데, mkfifo가 성공하면
		명명된 파일이 생성된다.
		
		단점 : 마찬가지로 읽기/쓰기가 동시에 가능하지 않으며, 
		read-only, write-only만 가능하다.
		하지만 통신선로가 파일로 존재하므로 하나를 읽기 전용으로 열고 다른
		하나를 쓰기 전용으로 영어서 이러한 read/write 문제를 해결 할 수 있다.
		호스트 영역의 서버 클라이언트 간에 전이중 통신을 위해서는 결국 
		PIPE와 같이 두개의 FIFO 파일이 필요하게 된다.
	
	- Message Queue
		  Queue(큐)는 선입선출의 자료구조를 가지는 통신 설비로 커널에서 관리한다.
		  입출력 방식으로 보자면 Named PIPE와 동일하다고 볼 수 있다.
		  Name PIPE와 다른 점이라면 Name PIPE가 데이터의 흐름이라면 메세지 큐는 
		  "메모리 공간"이라는 점이다. 파이프가 아닌, 어디에서나 물건을 꺼낼 수 있는
		  컨테이 벨트라고 보면 될 것이다.
	
	- Shared Memory(공유 메모)
	  
	- Memory Map
	  
	- Socket
	  
	- Semaphore



