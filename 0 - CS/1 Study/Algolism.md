---
created:
---
---
- [[CS LoadMap]]
---

##### **정렬 (Sorting)**

- **무언가를 정리한다.**
	
- 정렬 종류
	- **Bubble Sort**
	- **Selection Sort**
	- **Insertion Sort**
	- **Heap Sort**
	- **Merge Sort**
	- **Quick Sort**

##### 버블 정렬 Bubble Srot

- 시간복잡도
	- O(n^2)
	
- 내림차순 예시와 동작 설명
	
	1. **왼쪽 요소와 오른쪽 요소 비교**:
	    - 리스트의 첫 번째 요소와 두 번째 요소를 비교한다.
	    - **왼쪽 값이 더 작으면 교환**한다.
	        - (내림차순: 큰 값이 앞으로 오게끔 정렬)
	    - 그렇지 않으면 그대로 둔다.
	      
	2. **다음 요소로 이동**:
	    - 오른쪽으로 한 칸 이동하여 다시 비교하고 교환 여부를 결정한다.
	    - 리스트 끝까지 비교를 반복한다.
	      
	3. **끝까지 이동하면 한 사이클 완료**:
	    - 한 번의 순회가 끝나면 가장 작은 값이 리스트의 맨 뒤로 이동한다.
	    - **비교 범위를 줄이고** 다시 왼쪽부터 반복한다.
	      
	4. **필요 없을 때 멈춤**:
	    - 만약 순회 중에 교환이 한 번도 발생하지 않으면 정렬이 완료된 것으로 판단하고 멈춘다.
- 예제 코드
``` java
public class BubbleSort {
    public static void bubbleSortDescending(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) { // 전체 리스트를 반복
            boolean swapped = false; // 교환 여부 확인
            for (int j = 0; j < n - i - 1; j++) { // 점점 줄어드는 비교 범위
                if (arr[j] < arr[j + 1]) { // 내림차순: 왼쪽이 작으면 교환
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true; // 교환 발생
                }
            }
            if (!swapped) { // 교환이 없으면 정렬 완료
                break;
            }
        }
    }

    public static void main(String[] args) {
        int[] numbers = {3, 1, 4, 1, 5, 9, 2, 6, 5};
        System.out.println("정렬 전:");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
        
        bubbleSortDescending(numbers);
        
        System.out.println("\n내림차순 정렬 후:");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
    }
}
```

- 실행 결과
```java
정렬 전:
3 1 4 1 5 9 2 6 5 

내림차순 정렬 후:
9 6 5 5 4 3 2 1 1 
```

---
##### 선택 정렬 Selection Sort

- 시간 복잡도
	  
	- O(n2)
---
- 내림차순 예시와 동작 설명
	
1. **최대값 선택**:
    - 리스트에서 남아 있는 범위 중 가장 큰 값을 찾는다.
    - 해당 값을 **가장 왼쪽의 위치**로 이동시킨다. (스와핑)
      
2. **정렬된 범위 확장**:
    - 한 번의 순회가 끝나면 가장 큰 값이 리스트의 맨 앞에 고정된다.
    - 정렬된 범위를 확장하고, 남은 범위에서 다시 최대값을 찾는다.
      
3. **다음 위치로 반복**:
    - 두 번째로 큰 값을 두 번째 위치로 이동, 이후에도 같은 방식으로 반복한다.
      
4. **정렬 완료**:
    - 리스트의 모든 요소가 정렬될 때까지 반복한다.
	
- 예제 코드
``` java
public class SelectionSort {
    public static void selectionSortDescending(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) { // 정렬되지 않은 범위 반복
            int maxIdx = i; // 현재 범위에서 최대값의 인덱스 찾기
            for (int j = i + 1; j < n; j++) {
                if (arr[j] > arr[maxIdx]) { // 내림차순: 더 큰 값 찾기
                    maxIdx = j;
                }
            }
            // 최대값을 현재 위치로 이동
            int temp = arr[maxIdx];
            arr[maxIdx] = arr[i];
            arr[i] = temp;
        }
    }

    public static void main(String[] args) {
        int[] numbers = {3, 1, 4, 1, 5, 9, 2, 6, 5};
        System.out.println("정렬 전:");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
        
        selectionSortDescending(numbers);
        
        System.out.println("\n내림차순 정렬 후:");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
    }
}
```
- 실행 결과
```java
정렬 전:
3 1 4 1 5 9 2 6 5 

내림차순 정렬 후:
9 6 5 5 4 3 2 1 1 
```

---
- 선택 정렬 요약
	
1. **최대값 선택**:
    - 남아 있는 범위에서 가장 큰 값을 찾는다.
2. **최대값을 정렬된 위치로 이동**:
    - 최대값을 스와핑하여 정렬된 위치로 이동한다.
3. **남은 범위에서 반복**:
    - 정렬되지 않은 범위를 계속 줄여가며 반복한다.
4. **완료 시 정렬 결과**:
    - 내림차순일 경우, 큰 값부터 순차적으로 정렬된다.

---
##### 삽입 정렬 Insertion Sort

- **시간 복잡도**
	- O(n^2)
---

- **내림차순 예시와 동작 설명**

1. **정렬된 부분 확장**:
    
    - 리스트의 첫 번째 요소는 이미 정렬된 것으로 간주한다.
    - 두 번째 요소부터 시작해 **정렬된 부분에 올바른 위치를 찾아 삽입**한다.
2. **비교 및 이동**:
    
    - 현재 요소를 정렬된 부분의 요소들과 비교한다.
    - 내림차순이라면 **현재 요소가 더 크면 오른쪽으로 이동**한다.
3. **삽입**:
    
    - 정렬된 부분에서 현재 요소의 적절한 위치를 찾았다면 그 자리에 삽입한다.
4. **다음 요소로 이동**:
    
    - 리스트의 다음 요소를 선택하고 같은 과정을 반복한다.
5. **정렬 완료**:
    
    - 리스트 끝까지 이동하면 정렬이 완료된다.
---
- 예제 코드
```java
public class InsertionSort {
    public static void insertionSortDescending(int[] arr) {
        int n = arr.length;
        for (int i = 1; i < n; i++) { // 두 번째 요소부터 시작
            int key = arr[i]; // 삽입할 요소
            int j = i - 1;
            
            // 내림차순: 정렬된 부분에서 key보다 작은 요소들을 오른쪽으로 이동
            while (j >= 0 && arr[j] < key) {
                arr[j + 1] = arr[j];
                j--;
            }
            arr[j + 1] = key; // key를 적절한 위치에 삽입
        }
    }

    public static void main(String[] args) {
        int[] numbers = {3, 1, 4, 1, 5, 9, 2, 6, 5};
        System.out.println("정렬 전:");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
        
        insertionSortDescending(numbers);
        
        System.out.println("\n내림차순 정렬 후:");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
    }
}
```
- 실행 결과
```java
정렬 전:
3 1 4 1 5 9 2 6 5 

내림차순 정렬 후:
9 6 5 5 4 3 2 1 1 
```
---
- **삽입 정렬 요약**

1. **정렬된 부분 확장**:
    - 첫 번째 요소는 이미 정렬된 상태로 간주한다.
      
2. **비교 및 이동**:
    - 삽입할 위치를 찾기 위해 정렬된 부분을 순차적으로 비교하며 필요한 요소를 오른쪽으로 이동한다.
      
3. **삽입**:
    - 현재 요소를 적절한 위치에 삽입한다.
      
4. **다음 요소로 반복**:
    - 리스트 끝까지 반복하면 정렬이 완료된다.
      
5. **완료 시 정렬 결과**:
    - 내림차순일 경우, 큰 값부터 순차적으로 정렬된다.
---
##### 병합 정렬 Merge Sort

- 핵심은 분할, 병합이다.
- 함수가 호출될 때마다 절반씩 잘라서 재귀적으로 함수를 호출한다.
- 맨끝에 제일 작은 조각부터 2개씩 병합헤서 정렬된 배열을 merge해 나가는 정렬이다.
	
- 시간복잡도
	- `O(n log n)`
	
- 병합 정렬은 실행시에 별도의 저장공간이 필요로하다.
- 공간을 사용할 수 없는 경우는 퀵 정렬을 해야 한다.
  
- 예제 코드
```java
import java.util.Arrays;

public class MergeSort {

    // 병합 정렬 함수
    public static void mergeSort(int[] array) {
        // 배열의 길이가 1 이하인 경우 정렬할 필요 없음
        if (array.length < 2) {
            return;
        }
		
        // 배열을 두 부분으로 나눔
        int mid = array.length / 2;
        int[] left = Arrays.copyOfRange(array, 0, mid);
        int[] right = Arrays.copyOfRange(array, mid, array.length);
		
        // 재귀적으로 두 부분을 정렬
        mergeSort(left);
        mergeSort(right);
		
        // 두 정렬된 배열을 병합
        merge(array, left, right);
    }
	
    // 두 배열을 병합하는 함수
    public static void merge(int[] array, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;
		
        // 왼쪽 배열과 오른쪽 배열을 비교하면서 작은 값을 array에 채워 넣음
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) {
                array[k] = left[i];
                i++;
            } else {
                array[k] = right[j];
                j++;
            }
            k++;
        }
		
        // 왼쪽 배열에 남아있는 값이 있으면 넣어줌
        while (i < left.length) {
            array[k] = left[i];
            i++;
            k++;
        }
		
        // 오른쪽 배열에 남아있는 값이 있으면 넣어줌
        while (j < right.length) {
            array[k] = right[j];
            j++;
            k++;
        }
    }
	
    // 테스트용 main 함수
    public static void main(String[] args) {
        int[] array = {38, 27, 43, 3, 9, 82, 10};
        
        System.out.println("원본 배열: " + Arrays.toString(array));
        
        mergeSort(array); // 병합 정렬 수행
        
        System.out.println("정렬된 배열: " + Arrays.toString(array));
    }
}
```
	
- 학습자료
	https://www.youtube.com/watch?v=QAyl79dCO_k

##### 퀵 정렬 Quick Sort

- 정렬계 레전드
- 분할정복 알고리즘
- pivot을 정한 뒤 피봇의 위치를 확장해가며 정렬
	
- 퀵소트의 존엄성
	- pivot
		- pivot의 기준점에 따라 속도가 다르다.
		- 가장 베스트의 기준점은 아직까지는 없다.

1. 정렬이 안되어 있는 배열이 있다.
2. 배열안에 임의의 값을 지정한다.
3. 그 값을 기준으로 그 값보다 작은 값은 왼쪽, 큰 값은 오른쪽으로 옮긴다.
4. 파티션이 2개로 나뉜다.
5. 작은 파티션, 큰 파티션도 똑같이 반복
	   
- 시간복잡도
	- `O(n log n)`
	  
- 퀵 정렬은 기준 값을 정해야한다.,
- 가능한 중간 값을 선택하는게 좋다.
	
- 예제 코드
```java
public class QuickSort {
    // 퀵 정렬 함수
    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            // 피벗을 기준으로 배열을 분할
            int pivotIndex = partition(arr, low, high);
			
            // 피벗을 기준으로 배열을 두 부분으로 나누어 각각 재귀적으로 정렬
            quickSort(arr, low, pivotIndex - 1);  // 왼쪽 부분
            quickSort(arr, pivotIndex + 1, high); // 오른쪽 부분
        }
    }
	
    // 배열을 피벗을 기준으로 분할하는 함수
    public static int partition(int[] arr, int low, int high) {
        // 피벗을 배열의 마지막 원소로 선택
        int pivot = arr[high];
        int i = low - 1;
		
        // low부터 high-1까지의 배열을 순회하면서 피벗보다 작은 값을 왼쪽에, 
        // 큰 값을 오른쪽에 배치
        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                // 작은 값이 나오면 i와 j를 교환
                swap(arr, i, j);
            }
        }
		
        // 피벗을 적절한 위치로 교환
        swap(arr, i + 1, high);
        return i + 1; // 피벗의 인덱스를 반환
    }
	
    // 두 원소를 교환하는 함수
    public static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
	
    // 테스트용 main 함수
    public static void main(String[] args) {
        int[] arr = {38, 27, 43, 3, 9, 82, 10};
		
        System.out.println("원본 배열: ");
        printArray(arr);
		
        // 퀵 정렬 수행
        quickSort(arr, 0, arr.length - 1);
		
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
38 27 43 3 9 82 10 
정렬된 배열: 
3 9 10 27 38 43 82 

```
	
- 학습 자료
	https://www.youtube.com/watch?v=7BDzle2n47c

---
##### 힙 정렬 Heap Sort

- 힙 정렬(Heap Sort)은 **완전 이진 트리**를 기반으로 하는 **정렬 알고리즘**이다.
- **최대 힙(Max Heap)** 또는 **최소 힙(Min Heap)** 을 사용하여 배열을 정렬하는 방식
- 힙 정렬은 주로 **선택 정렬(Selection Sort)** 과 유사한 방식으로 동작
- 배열에서 최대값 또는 최소값을 반복적으로 선택하여 정렬합니다.
	
- 힙 정렬의 특징:
	
	1. **시간 복잡도**:
	    - **평균 시간 복잡도**: **O(n log n)** 
		    - 배열을 힙으로 만드는 과정과 힙에서 값을 빼는 과정이 모두 **O(log n)**이므로
		      
	    - **최악 시간 복잡도**: **O(n log n)** 
		    - 모든 경우에 대해 동일한 시간 복잡도
		      
	    - **최선 시간 복잡도**: **O(n log n)** 
		    - 항상 로그 시간의 비용이 듬
	      
	2. **공간 복잡도**:
	    - 힙 정렬은 **O(1)**의 추가 공간을 사용**
		    - 배열 내에서 직접 정렬을 수행하기 때문
	      
	3. **불안정한 정렬**:
	    - 힙 정렬은 **불안정한 정렬** 알고리즘
	    - 이는 동일한 값들에 대해 원래의 상대적인 순서를 보장하지 않음을 의미
	
- 힙 정렬의 작동 원리:
	
- 힙 정렬은 크게 **힙화(Heapify)** 와 **정렬** 두 단계로 나눌 수 있다.
	
- **힙화(Heapify) 과정**
	
	- 힙 정렬에서 먼저 배열을 **최대 힙(Max Heap)** 또는 **최소 힙(Min Heap)** 으로 변환
	- 힙은 완전 이진 트리의 특성을 가지고 있으며, **부모 노드는 자식 노드보다 크거나 작아야** 하는 조건을 만족해야 한다.
    - **최대 힙**: 부모 노드가 자식 노드보다 커야 한다.
    - **최소 힙**: 부모 노드가 자식 노드보다 작아야 한다.
      
	- 배열을 힙으로 변환하는 과정은 `heapify` 함수로 수행되며, 배열의 요소들이 이 조건을 만족하도록 트리 구조를 재구성한다.
	
- 정렬 과정
	
	1. 힙이 완성되면, **루트**(가장 큰 값 또는 가장 작은 값)가 배열의 첫 번째에 위치하게 된다.
	2. 이 값을 배열의 끝과 교환하고, **힙의 크기를 하나 줄인 후**, `heapify`를 호출하여 힙을 다시 정렬한다.
	3. 이 과정을 반복하여 배열의 모든 원소가 정렬될 때까지 힙을 재구성합니다.
	
-  힙 정렬 과정 예시
	
	1. 주어진 배열: **[12, 11, 13, 5, 6, 7]**
    
	2. **최대 힙**으로 배열을 변환
	    - 배열을 힙화하여 **[13, 12, 7, 5, 6, 11]** 로 만듭니다. 이제 루트(13)는 가장 큰 값 이다.
	      
	3. **루트와 마지막 값을 교환** (13과 11 교환)
	    - 교환 후 배열은 **[11, 12, 7, 5, 6, 13]** 가 되며, 13은 정렬된 상태이므로 제외합니다.
	      
	4. **힙 크기 줄이기**:
	    - 힙의 크기를 줄이고 나머지 부분에 대해 `heapify`를 적용합니다.
	      
	5. 이 과정을 반복하여 최종적으로 **[5, 6, 7, 11, 12, 13]** 과 같이 정렬된 배열을 얻을 수 있다.
	
-  힙 정렬의 장점:
	  
	- **빠른 정렬**
		- 힙 정렬은 최악의 경우에도 O(n log n) 시간 복잡도를 보장하므로 예측 가능한 성능을 제공한다.
		   
	-  **추가 공간을 적게 사용**
		- 힙 정렬은 추가적인 메모리를 거의 사용하지 않고 배열 내에서 정렬을 수행한다. 
		- 이는 **O(1)**의 공간 복잡도를 의미**
	
-  힙 정렬의 단점
	
	-  **불안정한 정렬**
		- 동일한 값을 가진 원소들의 상대적인 순서가 변경될 수 있기 때문에, 순서가 중요한 데이터에 대해서는 불안정한 정렬이 단점이 될 수 있다.
		  
	-  **속도**
		- 평균적으로 퀵 정렬이나 병합 정렬보다 다소 느릴 수 있다. 
		- 이론적으로는 동일한 시간 복잡도를 가지지만, 힙 정렬은 구현상의 오버헤드가 더 크기 때문이다.
	
-  결론
	- 힙 정렬은 **O(n log n)**의 시간 복잡도를 보장하는 효율적인 정렬 알고리즘이다.** 
	- **추가 공간을 거의 사용하지 않는** 특징을 가지고 있다.
	- 그러나 **불안정한 정렬**이므로, 이 점을 고려하여 사용하는 것이 좋다.
	  
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
	
- 학습 자료
	https://www.youtube.com/watch?v=rmtV_HcA6Oc
	https://www.youtube.com/watch?v=R7kURSaguIc

---