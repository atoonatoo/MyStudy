---
created:
---

---
- [[Algorithem]]
- 
- 
---
##### 힙 정렬 Heap Sort

- 힙 정렬은 **힙 자료구조(Heap)** 를 이용한 정렬 알고리즘으로, 다음과 같은 생명주기를 따른다.
	
- **힙 구성 단계 (Build Heap)**
	
	- 주어진 배열을 **완전 이진 트리** 형태로 변환합니다.
	- 이 트리를 **최대 힙(Max Heap)** 또는 **최소 힙(Min Heap)**으로 재구성합니다.
	- 최대 힙: 부모 노드가 항상 자식보다 크거나 같음.  
	    최소 힙: 부모 노드가 항상 자식보다 작거나 같음.
	- 최대 힙을 사용하면 정렬이 오름차순으로 수행됩니다.
	
- 예시
	- 배열 `[38, 27, 43, 3, 9, 82, 10]` → 최대 힙으로 변환:
```java
       82
     /    \
   38      43
  /  \    /  \
 3   9  27   10
```
	
- 힙 정렬의 단계 
	- 힙의 루트(가장 큰 값)를 배열의 마지막 요소와 교환합니다.
	- 교환 후 배열의 마지막 요소를 제외하고 다시 힙을 재구성합니다.
	- 이 과정을 반복하여 정렬된 배열을 만듭니다.
	  
- 예시
	- 최대 힙에서 루트 `82`를 마지막 요소와 교환 → `[10, 38, 43, 3, 9, 27, 82]`
	- 나머지 `[10, 38, 43, 3, 9, 27]`을 최대 힙으로 재구성 → `[43, 38, 27, 3, 9, 10]`
	- 다시 루트 `43`과 마지막 요소 교환 → `[10, 38, 27, 3, 9, 43, 82]`
	- 이 과정을 반복하여 최종 정렬: `[3, 9, 10, 27, 38, 43, 82]`
	
- 힙을 재구성하고 루트를 교환하는 과정이 끝나면 배열이 정렬됩니다.
	  
-  힙 정렬 생명주기 요약
	1. **힙 구성(Build Heap):** 배열을 힙 자료구조로 변환합니다.
	2. **정렬(Sort):** 루트와 마지막 요소를 교환하고, 힙을 재구성하는 과정을 반복합니다.
	3. **완료:** 힙 정렬이 완료되면 배열이 정렬됩니다.
	
- 힙 정렬의 특징
	
	- 시간 복잡도: **O(n log n)**
	- 공간 복잡도: **O(1)** (제자리 정렬)
	- 정렬 안정성: **비안정 정렬**
	  
- 예제 코드
``` java
public class HeapSort {
	
    // 힙 정렬 함수
    public static void heapSort(int[] arr) {
        int n = arr.length;
		
        // 배열을 힙으로 만드는 과정 (최대 힙)
        for (int i = n / 2 - 1; i >= 0; i--) {
            heapify(arr, n, i);
        }
		
        // 힙에서 가장 큰 값을 배열의 끝과 교환하고, 힙을 재구성
        for (int i = n - 1; i > 0; i--) {
            // 가장 큰 원소를 배열의 마지막 원소와 교환
            swap(arr, 0, i);
			
            // 교환 후, 힙의 크기를 하나 줄이고, 힙을 재구성
            heapify(arr, i, 0);
        }
    }
	
    // 힙을 재구성하는 함수 (최대 힙을 유지)
    public static void heapify(int[] arr, int n, int i) {
        int largest = i; // 루트
        int left = 2 * i + 1; // 왼쪽 자식
        int right = 2 * i + 2; // 오른쪽 자식
		
        // 왼쪽 자식이 루트보다 크면 largest를 왼쪽 자식으로 변경
        if (left < n && arr[left] > arr[largest]) {
            largest = left;
        }
		
        // 오른쪽 자식이 현재 largest보다 크면 largest를 오른쪽 자식으로 변경
        if (right < n && arr[right] > arr[largest]) {
            largest = right;
        }
		
        // largest가 루트가 아니라면, 값을 교환하고 재귀적으로 힙을 재구성
        if (largest != i) {
            swap(arr, i, largest);
            heapify(arr, n, largest);
        }
    }
	
    // 두 원소를 교환하는 함수
    public static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
	
    // 테스트용 main 함수
    public static void main(String[] args) {
        int[] arr = {12, 11, 13, 5, 6, 7};
		
        System.out.println("원본 배열: ");
        printArray(arr);
		
        // 힙 정렬 수행
        heapSort(arr);
		
        System.out.println("정렬된 배열: ");
        printArray(arr);
    }
	
    // 배열 출력 함수
    public static void printArray(int[] arr) {
        for (int i : arr) {
            System.out.print(i + " ");
        }
        System.out.println();
    }
}

원본 배열: 
12 11 13 5 6 7 
정렬된 배열: 
5 6 7 11 12 13
```

---
- **출처**
	- [유튜브 1](https://www.youtube.com/watch?v=gB7qYgikT1Y)
	- [유튜브 2](https://www.youtube.com/watch?v=rmtV_HcA6Oc)
	- [유튜브 3](https://www.youtube.com/watch?v=R7kURSaguIc)
---