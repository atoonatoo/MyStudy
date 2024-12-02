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

- 벙합 정렬의 동작은 **분할(Divide)**, **정복(Conquer)**, **병합(Merge)** 3단계를 반복하는 생명주기를 가지고 있다
	
- 분할 단계 (Divide)
	- 배열을 두 개의 하위 배열로 나눕니다.
	- 이 과정을 **재귀적으로** 반복하며, 배열의 크기가 1이 될 때까지 계속 나누어 갑니다.
	- 배열의 크기가 1이 되면 더 이상 나눌 수 없으므로 이 단계는 종료됩니다.
	
- 예시
	- 입력 배열
		- `[38, 27, 43, 3, 9, 82, 10]`
    - 분할 → 왼쪽: `[38, 27, 43]` / 오른쪽: `[3, 9, 82, 10]`
    - 다시 분할 → `[38]`, `[27, 43]` / `[3, 9]`, `[82, 10]`
    - 더 분할 → `[27]`, `[43]` / `[3]`, `[9]`, `[82]`, `[10]`
	- 결과적으로 각 배열이 1개 원소로 나뉘게 된다.
		- `[38]`, `[27]`, `[43]`, `[3]`, `[9]`, `[82]`, `[10]`
	
- 정복 단계 (Conquer)
	- 분할된 작은 배열들을 비교하고, 두 개씩 정렬하면서 병합을 시작합니다.
	- 작은 배열에서 큰 배열로 합쳐지며, 정렬된 상태를 유지합니다.
	- 이 과정은 재귀 호출이 종료되면서 **재귀 호출이 반환되는 순서대로** 실행됩니다.
	  
- 예시
	- `[27]`과 `[43]` 병합 → `[27, 43]`
	- `[38]`과 `[27, 43]` 병합 → `[27, 38, 43]`
	- `[3]`과 `[9]` 병합 → `[3, 9]`
	- `[82]`과 `[10]` 병합 → `[10, 82]`
	- `[3, 9]`과 `[10, 82]` 병합 → `[3, 9, 10, 82]`
	
- 병합 단계 (Merge)
	- 정렬된 하위 배열들을 다시 병합하면서 원래 크기의 배열로 합쳐나갑니다.
	- 최종적으로 모든 하위 배열이 병합되어 **완전한 정렬된 배열**이 생성됩니다.
	
- 예시
	- `[27, 38, 43]`과 `[3, 9, 10, 82]` 병합 → `[3, 9, 10, 27, 38, 43, 82]`
	
-  병합 정렬의 전체 생명주기 요약:
	1. **분할 (Divide):** 배열을 절반씩 나누어 더 이상 나눌 수 없을 때까지 반복합니다.
	2. **정복 (Conquer):** 각 하위 배열에서 정렬하면서 병합합니다.
	3. **병합 (Merge):** 병합된 하위 배열을 다시 합쳐 최종 정렬된 배열을 만듭니다.
	
- 시간복잡도
	- `O(n log n)`
	- n개 만큼씩 log n번 돌기 때문이다.
	
- 병합 정렬은 실행시에 별도의 저장공간이 필요로하다.
- 공간을 사용할 수 없는 경우는 퀵 정렬을 해야 한다.
	  
- 코드 실행시 각 단계별 진행 과정
```java
코드 실행 시 각 단계별 진행 과정

1.초기 배열 → 
	
	`[38, 27, 43, 3, 9, 82, 10]`
    
2.분할 완료 후 배열들 → 
	
	`[38]`, `[27]`, `[43]`, `[3]`, `[9]`, `[82]`, `[10]`
    
3.병합 진행 중 →
	
    - `[27] + [43]` → `[27, 43]`
    - `[38] + [27, 43]` → `[27, 38, 43]`
    - `[3] + [9]` → `[3, 9]`
    - `[82] + [10]` → `[10, 82]`
    - `[3, 9] + [10, 82]` → `[3, 9, 10, 82]`
    - `[27, 38, 43] + [3, 9, 10, 82]` → `[3, 9, 10, 27, 38, 43, 82]`
	
4. 최종 배열 → 
	
	 `[3, 9, 10, 27, 38, 43, 82]`
    
```
		  
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
	
- 학습 자료
	https://www.youtube.com/watch?v=rmtV_HcA6Oc
	https://www.youtube.com/watch?v=R7kURSaguIc

---

### 정렬 알고리즘 비교:

|정렬 알고리즘|시간 복잡도 평균|시간 복잡도 최악|공간 복잡도|정렬 안정성|
|---|---|---|---|---|
|병합 정렬|O(n log n)|O(n log n)|O(n)|안정적|
|퀵 정렬|O(n log n)|O(n²)|O(log n)|비안정적|
|힙 정렬|O(n log n)|O(n log n)|O(1)|비안정적|
