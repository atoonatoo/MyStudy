---
created:
---
---
- [[5 - 분류/7 - CS/4 wait/Data Structure]]
- [[]]
- 
---
##### **힙 (Heap)**  

- **완전이진트리를 기본으로 한 자료 구조이다.**
	  
- **A가 B의 부모노드(parent node) 이면, A의 Key값과 B의 키 값 사이에는 대소관계가 성립한다.**
	
- Heap의 종류
	- 최대 힙
		- 부모 노드의 키값이 자식노드의 키 값보다 항상 큰 힙
	- 최소 힙
		- 부모 노드의 키 값이 자식 노드의 키 값보다 항상 작은 힙
	
- **힙은 가장 높은 또는 가장 낮은 키 값이 뿌리노드(root 노드)에 오게되는 특징이 있다.**
	
- 이러한 구조를 통해 [[Priority Queue]]같은 추상적 자료형을 구현이 가능하다.
	
- Tree
	- 다수의 노드가 연결된 비선형 자료 구조
	- 부모 - 자식 의 계층 구조를 가지고 있다.
	  
- bianry tree (이진트리)
	- Heap은 이진트리를 사용한다.
	  
- 우선 순위 큐(priority queue)
	- ADT - 추상형 자료 큐
	- 가장 높은 우선 순위를 가진 데이터를 접근하거나 삭제할 때 굉장히 빠르게 접근 가능
	- 효율적인 삽입
	- O(1)의 우선 순위 요소 접근
	
- 부모 - 자식 노드의 대소 관계
	- min heap
	- max heap
	  
- heap은 배열로 표현이 가능하다.
	- root 노드가 인덱스 0에 위치할 경우
		- left - i * 2 + 1
		- right - i * 2 + 2
		- parent - (i - 1) / 2
	
- heap의 삽입 연산
	  
	- Heapify (힙의 재구조화)
		- 수행과정에서 생길수도 있는 구조의 변화로 인해 힙의 속성이 깨질 수 있기 때문에, 삽입/삭제시 힙의 재구조화를 요구된다.
		  
	- Heapify Up (버블 업)
		1. 현재 노드의 인덱스를 구한다.
		2. 현재 노드의 부모 노드의 인덱스를 구한다.
		3. 현재 노드가 부모 노드보다 크다면 두 노드를 바꾼다.
		4. 현재 노드의 인덱스를 부모 노드의 인덱스로 바꾼다.
		5. 현재 노드의 부모 노드의 인덱스를 구한다. (반복..)
	
- heap의 삭제 연산
	- Heapify Down (버블 다운)
	1. 좌측 자식 > 현재 요소 : 다음 인덱스를 좌측 자식 인덱스로 설정
	2. 우측 자식 > 현재 요소 : 다음 인덱스를 우측 자식 인덱스로 설정
	3. 다음 인덱스 != 현재 인덱스 : 현재 요소와 다음 요소를 교환하고, 다음 인덱스를 기준으로 다시 heapifyDown 호출
	
- 삽입 / 삭제 시간 복잡도
	- 삭제 및 삽입 연산의 시간 복잡도는 heap의 높이에 의해 결정
	- heap의 높이는 log n에 비례하므로 O(log n)
	  
- heap의 주요 메서드
	- peek() - 최대/최소값 리턴
	- size() - 힙 사이즈 리턴
	- isEmpty() - 힙 사이즈 0 체크
	  
- 코딩 테스트 문제
	- K 번째 큰 수
	- 가장 빈번하게 나오는 수/글자 K개
	- 출현 빈도별로 문자 정렬
	- 더 맵개
	- 이중 우선 순위 큐
	  
- 사용 언어의 Heap 구현 여부
	
- 종류

---
##### 출처
- 
---