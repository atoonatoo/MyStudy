---
created:
---
---
- [[CS LoadMap]]
- 
- 
---
- [[Sorting]]
- [[]]
- [[]]
- [[]]
- [[]]
- [[]]
- [[]]
- [[]]
- [[]]
- [[]]
---
##### 삽입 정렬 Insertion Sort

- **시간 복잡도**
	- O(n^2)
	  
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
- pivot (기준값)을 정한 뒤 피벗의 위치를 확장해가며 정렬
	
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
	  
	- 퀵 정렬은 기준 값을 정해야한다.
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
	https://www.youtube.com/watch?v=gB7qYgikT1Y
	https://www.youtube.com/watch?v=rmtV_HcA6Oc
	https://www.youtube.com/watch?v=R7kURSaguIc

---

##### 선형검색트리

- 배열에서 데이터를 찾는 알고리즘
- 이진탐색과 달리 데이터의 순서가 뒤죽박죽 나열된 경우도 적용
- 찾는 방식은 단순히 배열 앞쪽부터 순서대로 데이터를 조사한다.
- 데이터의 처음부터 선대로 비교를 반복한다.
- 따라서 데이터가 배열의 끝에 있거나 없는 경우에는 비교 횟수가 많아져서 시간이 오래 걸린다.
- 시간복잡도 - O(n)
- 예시 - 순서없이 막 꽂힌 책장
- 선형 시간 복잡도
	- input이 많을 수록 수행하는 시간도 증가한다.
	
- 예제 코드
```java
class LinearSearchTree {

    private class Node {
        int value;
        Node next;
		
        Node(int value) {
            this.value = value;
            this.next = null;
        }
    }
	
    private Node head;
	
    public void insert(int value) {
        Node newNode = new Node(value);
        if (head == null) {
            head = newNode;
        } else {
            Node current = head;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newNode;
        }
    }
	
    public boolean search(int value) {
        Node current = head;
        while (current != null) {
            if (current.value == value) {
                return true;
            }
            current = current.next;
        }
        return false;
    }
	
    public void display() {
        Node current = head;
        while (current != null) {
            System.out.print(current.value + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }
}

public class LinearSearchTreeDemo {
    public static void main(String[] args) {
        LinearSearchTree tree = new LinearSearchTree();
        tree.insert(10);
        tree.insert(20);
        tree.insert(30);
		
        tree.display();
		
        System.out.println("Search 20: " + tree.search(20));
        System.out.println("Search 40: " + tree.search(40));
    }
}
```
##### 이진검색트리

- 데이터가 정렬된 경우에만 적용
- 이진 탐색은 배열이 정렬된 것을 이용하여 탐색 범위를 매번 절반싹 줄여 나간다.
- 그리고 탐색 범위의 데이터가 1개가 되었을 때 탐색을 종료
- n개가 있던 데이터를 절반씩 줄이는 조작을 O log(n2)번 반복하면, 데이터가 1개가 된다.
- 즉, 이진 탐색에서는 `배열의 정중앙에 있는 수와 비교하여 탐색 범위를 절반으로 줄이는` 작업을 log(n2)회 반복하면 데이터를 찾을 수 있다. 
- 찾지 못한 경우에는 데이터가 없다고 결론 내릴 수 있다.
  
- 빅오표기법
	- O(log n)
	  
- 예시 - 순서있게 잘 정리된 도서관 책장
	
- 예제 코드
```java
class BinarySearchTree {
    private class Node {
        int value;
        Node left, right;
		
        Node(int value) {
            this.value = value;
            left = right = null;
        }
    }
	
    private Node root;
	
    public void insert(int value) {
        root = insertRec(root, value);
    }
	
    private Node insertRec(Node root, int value) {
        if (root == null) {
            root = new Node(value);
            return root;
        }
        if (value < root.value) {
            root.left = insertRec(root.left, value);
        } else if (value > root.value) {
            root.right = insertRec(root.right, value);
        }
        return root;
    }
	
    public boolean search(int value) {
        return searchRec(root, value);
    }
	
    private boolean searchRec(Node root, int value) {
        if (root == null) {
            return false;
        }
        if (root.value == value) {
            return true;
        }
        if (value < root.value) {
            return searchRec(root.left, value);
        }
        return searchRec(root.right, value);
    }
	
    public void inorder() {
        inorderRec(root);
    }
	
    private void inorderRec(Node root) {
        if (root != null) {
            inorderRec(root.left);
            System.out.print(root.value + " ");
            inorderRec(root.right);
        }
    }
}

public class BinarySearchTreeDemo {
    public static void main(String[] args) {
        BinarySearchTree tree = new BinarySearchTree();
        tree.insert(50);
        tree.insert(30);
        tree.insert(70);
        tree.insert(20);
        tree.insert(40);
        tree.insert(60);
        tree.insert(80);
		
        System.out.print("Inorder Traversal: ");
        tree.inorder();
        System.out.println();
		
        System.out.println("Search 40: " + tree.search(40));
        System.out.println("Search 90: " + tree.search(90));
    }
}
```


##### 그래프

- 용어
	- 노드
		- 정점(Vertex) 이라고도 한다.
		- 그래프에서 특정 객체나 위치를 나타내는 단위.
		- 노드는 데이터 또는 정보를 나타낼 수 있으며, 노드 간의 관계(간선)를 통해 연결된다.
	- 간선
		- 노드와 노드를 연결하는 선(선분)으로, 노드 간의 관계를 표현.
		- 방향에 따라 두 가지 유형으로 나뉜다.
		  
- 그래프의 다양한 표현
	- 파티에 참석한 대인관계
	- 지하철 노선도
	  
- 컴퓨터 네트워크 접속관계
	
- 가중그래프
	- 간선에 값이 붙어 있는 그래프
	- 간선에 할당된 값을 간선의 `무게`나 `비용`이라고 부른다.
	- 간선에 비용이 없으면 정점 간 연결 여부만 표현할 수 있다.
	- 비용이 있으면 연결 강도를 표현하는 것이 가능
	  
- 방향성 그래프
	- 간선에 방향성을 부여한다.
	- 웹페이지의 링크도 방향성이 부여되기 때문에 방향성 그래프라고 표현하면 편리하다.
	- 반대로 방향이 없는 그래프를 무방향 그래프라고 한다.
	- 방향선 그래프는 간선에 비용을 부여할 수 있다.
	  
- 그래프를 사용하면 무엇이 편리한가?
	- 네트워크의 통신 시간이 가장 짧은 경로를 찾는 문제
	- 노선도에서 이동 시간이 가장 짧은 경로를 찾는 문제
	- 노선도에서 운임이 가장 작은 경로를 찾는 문제 등
	- 다양한 대상을 그래프라는 하나의 도구로 표현할 수 있기에 다양한 실생활 문제를 해결하는데 사용 가능하다.
	  
- 결론
	- 그래프에 대한 기본적인 문제를 살펴 볼 예정
	- 그래프 탐색은 한 정점에서 시작하여 간선을 타고 그래프를 탐색하며 목표를 찾는 문제
	- 탐색 순서에 따라 너비 우선 탐색, 깊이 우선 탐색으로 나뉜다.
	- 최단 경로 문제는 지정한 두 정점 s와 t를 연결하는 경로 중 간선의 비용 합이 가장 작은 것을 찾는 문제 등
	- 최소 신장 트리 문제는 그래프의 모든 정점이 연결되도록 간선을 선택할 때 선택된 간선의 비용 합이 최소가 되도록 하는 문제
	- 매칭 문제는 그래프에서 간선을 선택하여 정점의 쌍을 만드는 문제
	- 사람과 작업 관계를 표현한 이분 그래프에서 가능한 많은 쌍을 만드는 알고리즘을 소개할 예정


##### 너비 우선 탐색

- 그래프를 탐색하는 알고리즘이다.
	  
- 가정
	1. 정점(시작점)이 맨 위에 있다.
	2. 그래프의 전체구조는 모른다.
	   
- 목적
	- 시작점에서 간선을 따라가며 정점을 탐색하여 지정한 정점(목표)이 목표인지 여부를 판단할 수 있다.
	  
-  **너비 우선 탐색의 동작 구조**
	
	1. **시작 노드를 큐(Queue)에 추가하고 방문 처리한다.**
	    - 탐색을 시작할 초기 노드를 큐에 넣고, 해당 노드를 "방문 처리"한다.
	    - 방문 처리란, 해당 노드를 이미 방문한 것으로 표시하여 중복 탐색을 방지하는 작업을 의미한다.
	      
	2. **큐에서 노드를 하나 꺼내고 해당 노드의 인접 노드들을 확인한다.**
	    - 큐의 맨 앞에서 노드를 꺼낸다.
	    - 꺼낸 노드와 연결된 인접 노드들을 확인하며, 방문하지 않은 노드들을 찾아낸다.
	      
	3. **방문하지 않은 인접 노드를 큐에 추가하고 방문 처리한다.**
	    - 확인된 인접 노드 중 아직 방문하지 않은 노드들을 큐에 넣고, 방문 처리한다.
	      
	4. **큐가 빌 때까지 2~3 단계를 반복한다.**
	    - 모든 노드를 방문할 때까지 위 과정을 반복하며 탐색한다.
	
- **BFS의 특징**
	- 너비 우선 탐색은 **노드의 깊이를 기준으로 탐색**한다.
	- 먼저 시작 노드와 가까운 노드를 모두 방문한 뒤, 그다음 깊이로 넘어간다.
	- 일반적으로 큐(Queue)를 이용하여 구현된다.
	  
-  BFS 탐색 순서:
	
	- 시작 노드: A
		
	1. **A를 큐에 추가하고 방문 처리.**
	    
	    - 큐 상태: [A]
	2. **큐에서 A를 꺼내고 인접 노드 B, C를 추가.**
	    
	    - 큐 상태: [B, C]
	    - 방문 처리: A → B, C
	3. **큐에서 B를 꺼내고 인접 노드 D를 추가.**
	    
	    - 큐 상태: [C, D]
	    - 방문 처리: A → B → D
	4. **큐에서 C를 꺼내고 인접 노드 E를 추가.**
	    
	    - 큐 상태: [D, E]
	    - 방문 처리: A → B → C → E
	5. **큐에서 D를 꺼내지만, D에는 인접 노드가 없으므로 그대로 넘어감.**
	    
	    - 큐 상태: [E]
	6. **큐에서 E를 꺼내고, 더 이상 탐색할 노드가 없으므로 종료.**
	    
	    - 큐 상태: []
	
-  **BFS 구현 (자바 코드)**
```java
import java.util.*;

public class BFSExample {
    public static void main(String[] args) {
        // 그래프 초기화
        Map<String, List<String>> graph = new HashMap<>();
        graph.put("A", Arrays.asList("B", "C"));
        graph.put("B", Arrays.asList("D"));
        graph.put("C", Arrays.asList("E"));
        graph.put("D", new ArrayList<>());
        graph.put("E", new ArrayList<>());

        bfs(graph, "A");
    }

    public static void bfs(Map<String, List<String>> graph, String start) {
        Queue<String> queue = new LinkedList<>();
        Set<String> visited = new HashSet<>();

        queue.add(start);
        visited.add(start);

        while (!queue.isEmpty()) {
            String node = queue.poll();
            System.out.print(node + " "); // 현재 노드 출력

            for (String neighbor : graph.get(node)) {
                if (!visited.contains(neighbor)) {
                    queue.add(neighbor);
                    visited.add(neighbor);
                }
            }
        }
    }
}

```

---
##### 깊이 우선 탐색

- 그래프를 탐색하는 알고리즘이다.
	
- 하나의 길을 선택하여 갈 수 있는 만큼 진행하다가 더 이상 진행할 수 없으면 되돌아가서 다음 후보 경로를 탐색한다.
	  
-  **가정**
	1. **정점(시작점)이 맨 위에 있다.**  
	    시작점부터 탐색을 시작한다.
	    
	2. **그래프의 전체 구조는 모른다.**  
	    그래프의 모든 정점과 간선을 탐색하며 구조를 알아간다.
	
-  **목적**
	- 시작점에서 **한 경로를 끝까지 탐색**하며 정점을 방문한다.
	- **지정한 정점(목표)**에 도달했는지 여부를 판단할 수 있다.
	
-  **주요 특징**
	- 깊이 우선 탐색은 경로를 **최대한 깊이** 탐색한 후, 돌아와 다른 경로를 탐색한다.
	- 스택(또는 재귀)을 활용하여 탐색 과정을 관리한다.
	
-  **너비 우선 탐색의 동작 구조**
	
	1. **시작 노드를 큐(Queue)에 추가하고 방문 처리한다.**
	    - 탐색을 시작할 초기 노드를 큐에 넣고, 해당 노드를 "방문 처리"한다.
	    - 방문 처리란, 해당 노드를 이미 방문한 것으로 표시하여 중복 탐색을 방지하는 작업을 의미한다.
	      
	2. **큐에서 노드를 하나 꺼내고 해당 노드의 인접 노드들을 확인한다.**
	    - 큐의 맨 앞에서 노드를 꺼낸다.
	    - 꺼낸 노드와 연결된 인접 노드들을 확인하며, 방문하지 않은 노드들을 찾아낸다.
	      
	3. **방문하지 않은 인접 노드를 큐에 추가하고 방문 처리한다.**
	    - 확인된 인접 노드 중 아직 방문하지 않은 노드들을 큐에 넣고, 방문 처리한다.
	      
	4. **큐가 빌 때까지 2~3 단계를 반복한다.**
	    - 모든 노드를 방문할 때까지 위 과정을 반복하며 탐색한다.
	
-  **BFS의 특징**
	- 너비 우선 탐색은 **노드의 깊이를 기준으로 탐색**한다.
	- 먼저 시작 노드와 가까운 노드를 모두 방문한 뒤, 그다음 깊이로 넘어간다.
	- 일반적으로 큐(Queue)를 이용하여 구현된다.
	
- **BFS 탐색 순서**
	  
	- 시작 노드: A
	
	1. **A를 큐에 추가하고 방문 처리.**
	    - 큐 상태: [A]
	      
	2. **큐에서 A를 꺼내고 인접 노드 B, C를 추가.**
	    - 큐 상태: [B, C]
	    - 방문 처리: A → B, C
	      
	3. **큐에서 B를 꺼내고 인접 노드 D를 추가.**
	    - 큐 상태: [C, D]
	    - 방문 처리: A → B → D
	      
	4. **큐에서 C를 꺼내고 인접 노드 E를 추가.**
	    - 큐 상태: [D, E]
	    - 방문 처리: A → B → C → E
	      
	5. **큐에서 D를 꺼내지만, D에는 인접 노드가 없으므로 그대로 넘어감.**
	    - 큐 상태: [E]
	      
	6. **큐에서 E를 꺼내고, 더 이상 탐색할 노드가 없으므로 종료.**
	    - 큐 상태: []
	
- 예제 코드
```java
import java.util.*;

public class BFSExample {
    public static void main(String[] args) {
        // 그래프 초기화
        Map<String, List<String>> graph = new HashMap<>();
        graph.put("A", Arrays.asList("B", "C"));
        graph.put("B", Arrays.asList("D"));
        graph.put("C", Arrays.asList("E"));
        graph.put("D", new ArrayList<>());
        graph.put("E", new ArrayList<>());

        bfs(graph, "A");
    }

    public static void bfs(Map<String, List<String>> graph, String start) {
        Queue<String> queue = new LinkedList<>();
        Set<String> visited = new HashSet<>();

        queue.add(start);
        visited.add(start);

        while (!queue.isEmpty()) {
            String node = queue.poll();
            System.out.print(node + " "); // 현재 노드 출력

            for (String neighbor : graph.get(node)) {
                if (!visited.contains(neighbor)) {
                    queue.add(neighbor);
                    visited.add(neighbor);
                }
            }
        }
    }
}

```

---
##### 벨먼-포드 알고리즘

- 그래프의 최단 경로를 찾는 알고리즘
- 최단 경로 문제는 시작점과 끝점이 지정되어 있고,
- 간선에 비용이 부여된 가중 그래프가 주어졌을때, 
- 시작점과 끝점까지의 경로 중 비용의 합이 가장 작은 것을 찾는 문제
	
- 시간복잡도
	- O(VE)
	
- **동작 원리:**
	
1. 벨먼-포드 알고리즘은 **모든 간선**을 반복적으로 확인하여 최단 경로를 계산한다.
2. **그래프에 음의 가중치가 포함되어 있을 때** 사용할 수 있으며, 음수 사이클을 탐지할 수 있다.
3. **초기화**:
    - 시작점의 거리는 0, 나머지 노드의 거리는 무한대(∞)로 설정한다.
4. **간선 순회**:
    - 모든 간선을 반복하면서, 경로를 갱신한다.
5. **음수 사이클 탐지**:
    - 마지막 단계에서 경로가 더 갱신될 수 있다면, 음수 사이클이 존재한다고 판단한다.
	
**알고리즘 흐름:**
	
- 1. 모든 간선에 대해 `Relaxation`을 반복하여 최단 경로를 구한다.
- 2. 음수 사이클이 존재하면 이를 탐지한다.
	
- 예제 코드
```java
import java.util.Arrays;

class BellmanFord {
    static final int INF = Integer.MAX_VALUE;
    
    public static void bellmanFord(int[][] graph, int V, int start) {
        int[] dist = new int[V];
        Arrays.fill(dist, INF);
        dist[start] = 0;
        
        // V-1번 반복
        for (int i = 1; i < V; i++) {
            for (int u = 0; u < V; u++) {
                for (int v = 0; v < V; v++) {
                    if (graph[u][v] != INF && dist[u] != INF && dist[u] +
                     graph[u][v] < dist[v]) {
                        dist[v] = dist[u] + graph[u][v];
                    }
                }
            }
        }
        
        // 음수 사이클 체크
        for (int u = 0; u < V; u++) {
            for (int v = 0; v < V; v++) {
                if (graph[u][v] != INF && dist[u] != INF && dist[u] + 
                graph[u][v] < dist[v]) {
                    System.out.println("그래프에 음수 사이클이 존재합니다.");
                    return;
                }
            }
        }
        
        // 결과 출력
        System.out.println("최단 경로:");
        for (int i = 0; i < V; i++) {
            System.out.println("노드 " + i + "까지의 최단 거리: " + 
            (dist[i] == INF ? "INF" : dist[i]));
        }
    }
	
    public static void main(String[] args) {
        int V = 5; // 정점 수
        int[][] graph = new int[V][V];
        
        // 그래프 초기화 (INF는 연결되지 않은 간선)
        for (int[] row : graph) {
            Arrays.fill(row, INF);
        }
        
        // 간선 추가 (u, v, weight)
        graph[0][1] = 6;
        graph[0][2] = 7;
        graph[1][2] = 8;
        graph[1][3] = 5;
        graph[2][3] = -3;
        graph[3][4] = 2;
        
        bellmanFord(graph, V, 0);  // 시작 정점 0
    }
}
```

- 학습 자료
	- https://www.youtube.com/watch?v=Ppimbaxm8d8

---
##### 다익스트라 알고리즘

**동작 원리:**

1. **다익스트라 알고리즘**은 **가중치가 양수인 그래프**에서 최단 경로를 구하는 알고리즘입니다.
2. **우선순위 큐** (최소 힙)을 사용하여 가장 짧은 거리를 가진 정점을 빠르게 찾습니다.
3. **초기화**:
    - 시작점의 거리는 0, 나머지 노드의 거리는 무한대로 설정합니다.
4. **경로 갱신**:
    - 방문하지 않은 인접 정점들의 거리를 갱신하고, 우선순위 큐에 삽입합니다.
	
- **알고리즘 흐름:**
	
- 1. 각 정점에 대해 최소 거리를 갱신합니다.
- 2. 큐에서 가장 가까운 노드를 선택하고, 그 인접 노드를 갱신합니다.
	
- 시간복잡도
	- O(N2)
	 
- 예제 코드
```java
import java.util.*;

class Dijkstra {
    static final int INF = Integer.MAX_VALUE;
    
    public static void dijkstra(int[][] graph, int V, int start) {
        int[] dist = new int[V];
        Arrays.fill(dist, INF);
        dist[start] = 0;
        
        // 우선순위 큐 (최소 힙)
        PriorityQueue<int[]> pq = 
        new PriorityQueue<>(Comparator.comparingInt(a -> a[1]));
        pq.add(new int[]{start, 0});
        
        while (!pq.isEmpty()) {
            int[] current = pq.poll();
            int u = current[0];
            int currentDist = current[1];
            
            if (currentDist > dist[u]) continue;
            
            for (int v = 0; v < V; v++) {
                if (graph[u][v] != INF && dist[u] + graph[u][v] < dist[v]) {
                    dist[v] = dist[u] + graph[u][v];
                    pq.add(new int[]{v, dist[v]});
                }
            }
        }
        
        // 결과 출력
        System.out.println("최단 경로:");
        for (int i = 0; i < V; i++) {
            System.out.println("노드 " + i + "까지의 최단 거리: " + 
            (dist[i] == INF ? "INF" : dist[i]));
        }
    }
	
    public static void main(String[] args) {
        int V = 5; // 정점 수
        int[][] graph = new int[V][V];
        
        // 그래프 초기화 (INF는 연결되지 않은 간선)
        for (int[] row : graph) {
            Arrays.fill(row, INF);
        }
        
        // 간선 추가 (u, v, weight)
        graph[0][1] = 6;
        graph[0][2] = 7;
        graph[1][2] = 8;
        graph[1][3] = 5;
        graph[2][3] = -3;
        graph[3][4] = 2;
        
        dijkstra(graph, V, 0);  // 시작 정점 0
    }
}
```

- 벨먼-포드 vs 다익스트라 차이점
	
	1. **벨먼-포드 알고리즘**:
	    - **음수 가중치**를 다룰 수 있다.
	    - **모든 간선을 반복**해서 체크하므로 계산이 더 느림.
	    - 음수 사이클을 탐지할 수 있음.
	      
	2. **다익스트라 알고리즘**:
	    - **음수 가중치**가 있을 경우 동작하지 않음.
	    - **우선순위 큐**를 사용하여 최단 경로를 빠르게 구할 수 있음.
	    - **빠르게 실행**되며, 시간 복잡도가 벨먼-포드보다 유리함.
	
- 학습자료
	- https://www.youtube.com/watch?v=611B-9zk2o4
---
##### 그리드 알고리즘

- 당장의 최적의 선택을 하는 알고리즘
- 당장의 최단 속도, 최단 거리, 최단 비용들을 계산한다.
- 근사 알고리즘이라고도 불린다.
	  
- 마시멜로우 이야기
	당장 1개의 마시멜로우가 있고 10분만 안먹고 기다리면 2개를 준다고 가정하자.
	그리드 알고리즘은 당장 먹는 것이 이득이라는 알고리즘이다.
	
- 나름의 최선을 찾을 수는 있지만 항상 최선의 결과를 찾을 것이라는 보장은 없다.
	  
- 코딩테스트의 특셩상 항상 최적 해를 찾아야 한다. 따라서 최적 해를 보장하는 조건에서만 그리드 알고리즘을 사용해야 한다.
	- 조건
		1. 탐욕스러운 선택 조건 (Greedy Choice Property)
			- 현재의 선택이 미래에 영향을 주지 않는다.
		2. 최적 부분 구조 조건 (Optimal Substructure)
			-  부분의 최적 해가 모이면 전체의 최적 해가 된다.
		3. 그리디 전략
			- 어떻게 하면 이러한 조건으로 어떻게 문제를 풀어야할까?
				- **핵심은 정렬이다.**
			- 어떻게 정렬을 해야 미래의 선택을 따지지않아도 최적의 해를 구할 수 있을까?
				- 회의실 배정 (백준 1931)
		4. 이 복잡한 것을 왜 사용하는가?
			- 속도 때문이다, DP보다 더 빠르다는 특징이 있다.
			- 최적 해가 보장되있는 경우에는 그리디 알고리즘을 사용해서 조금 더 빠른 문제를 풀 수 있다.
			- 근사치로도 만족할 수 있는 기능에는 성능의 개선을 위해 사용되곤 한다.
				- 지하철 노선도의 최적 경로가 몇분 오차가 나도 성능적으로는 크게 불만 없다.
		5. 추천 문제
			- 브론즈
				- 세탁소 사장 동혁 - 2720
				- 전자레인지 - 10162
				- 거스름돈 - 5585
				- 캠핑 - 4796
				- 컵홀더 - 2810
			- 실버
				- 설탕배달 - 2839
				- ATM - 11399
				- 동전 0 - 11047
				- 잃어버린 괄호 - 1541
				- 회의실 배정 - 1931
			- 골드
				- 강의실 배정 - 11000
				- 카드 정렬하기 - 1715
				- 단어 수학 - 1339
				- 수 묶기 - 1744
				- 보석 도둑 - 1202
- 코드
```java
public class MaxSubArraySum {
    public static int maxSubArraySum(int[] nums) {
        // DP 테이블을 초기화
        int n = nums.length;
        int maxSum = nums[0];  // 첫 번째 값을 최대값으로 설정
        int currentSum = nums[0];  // 현재까지의 합
        
        // 배열을 순회하면서 현재까지의 합을 갱신하고 최대값을 찾음
        for (int i = 1; i < n; i++) {
            currentSum = Math.max(nums[i], currentSum + nums[i]);
            maxSum = Math.max(maxSum, currentSum);
        }
        
        return maxSum;
    }
	
    public static void main(String[] args) {
        // 테스트용 배열
        int[] nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println("최대 부분 합: " + maxSubArraySum(nums));  // 출력: 6
    }
}

// `currentSum`은 현재까지의 연속된 부분 배열의 합을 추적.
// `maxSum`은 현재까지 발견된 최대 부분 합을 저장.
// 배열을 한 번 순회하면서 `currentSum`을 갱신, 
// 그 값이 `maxSum`보다 크면 `maxSum`을 업데이트.
```
---
##### 다이나믹 프로그래밍
- 다이나믹 프로그래밍의 탄생 계기
	- 다이나믹 프로그래밍은 완전 탐색 , DFS, BFS와 같이 수많은 경우에 수를 따져봐야하는데 그 경우의 수가 너무 많아서 속도가 느려지는 것을 개선하고자, 수행 시간을 단축하고자 만들어진 알고리즘이다.
	
- 다이나믹 프로그래밍의 목적
	- **메모리를 사용해서 중복 연산을 줄이고 중복 연산을 줄여서 수행 속도를 개선한다.**
	- 메모리를 사용한다. -> 배열 혹은 자료구조를 만든다.
	- 중복연산을 줄인다. -> 연산한 결과를 배열에 담는다.
	
- 정수 삼각형 문제
	- 핵심
		- DP 삼각형을 어떻게 정의하고, 값을 차곡차곡 쌓아서 중복 연산을 줄이느냐.
	
- 왜 이걸 다이나믹 프로그래밍이라고 불리는 이유
	- 기억하기 알고리즘
	- 기억하며 알고리즘
	- 연산한 내용을 기억하고, 기억한 값을 사용해서 문제를 푸는게 다이나믹프로그래밍의 전부
	  
- 구분법
	- 다양한 유형의 문제를 최적화 할 때 고려될 수 있는 알고리즘이다.
	- 코딩 테스트, 알고리즘 문제에서 이건 DP로 풀어야겠다고 판단할 수 있는 기준
		1. DFS/BFS로 풀 수는 있지만, 경우의 수가 너무 많은 문제
		- 최악의 경우의 수를 계산하는 가장 쉬운 방법
			- 직접 계산해보는 방법
				- 초반부에 직접 계산해보면 패턴이 보일 것이고 그 패턴으로 최대 경우의 수를 유추할 수 있다. 그리고 DP에 사용하기 적합한지 여부를 판단.
		2. 경우의 수들에 중복적인 연산이 많은 경우
- 풀이법
	- 최대한 많은 문제들을 풀어보고 풀이들을 참고하면서
	- DP식 사고방식을 습득할 필요가 있다.
	- 혼자서 스스로 풀이하기에는 아주 많은 시간이 걸린다.
	- 오래 붙잡고 있기보다는 30분 정도 고민해보고 답이 안나오면 풀이를 참고해서 구현만 해보는 방식을 강하게 추천
	- 30분동안은 어떻게하면 뒤로 돌아가지 않을 수 있을까를 고민
	- 현재 단계까지는 연산을 잘했는데 그 연산을 또 하지않으려면 어떤 정보를 남겨야 하지?
	- 어떤 식으로 정보를 누적해야되지?
	- DP 삼각형 같이 나만의 자료구조를 하나 더 만들고 거기에 어떤 정보를 담아야 이전 단계로 돌아가지 않을지 고민해 봐야한다. 
	  
- 코드
```java
// 미로 탈출 문제 (DFS)

public class MazeEscape {
    private static final int[] dx = {-1, 1, 0, 0};  // 상, 하, 좌, 우
    private static final int[] dy = {0, 0, -1, 1};
	
    public static boolean canEscape(
    int[][] maze, int startX, int startY, int endX, int endY) {
    
        int m = maze.length;
        int n = maze[0].length;
        
        // 방문 여부를 체크할 배열
        boolean[][] visited = new boolean[m][n];
        
        // DFS 탐색
        return dfs(maze, startX, startY, endX, endY, visited);
    }
	
    private static boolean dfs(
    int[][] maze, int x, int y, int endX, int endY, boolean[][] visited) {
    
        // 경계를 벗어나거나 벽에 막혔을 때
        if (x < 0 || x >= maze.length 
        || y < 0 
        || y >= maze[0].length 
        || maze[x][y] == 1 
        || visited[x][y]) {
        
            return false;
        }
		
        // 도착지점에 도달했을 경우
        if (x == endX && y == endY) {
            return true;
        }

        visited[x][y] = true;

        // 4방향으로 이동 시도
        for (int i = 0; i < 4; i++) {
            int newX = x + dx[i];
            int newY = y + dy[i];

            // DFS를 통해 탈출 가능 여부 확인
            if (dfs(maze, newX, newY, endX, endY, visited)) {
                return true;
            }
        }

        return false;  // 탈출 불가능
    }

    public static void main(String[] args) {
        // 0은 길, 1은 벽
        int[][] maze = {
            {0, 1, 0, 0, 0},
            {0, 1, 0, 1, 0},
            {0, 0, 0, 1, 0},
            {1, 1, 0, 1, 0},
            {0, 0, 0, 0, 0}
        };
        
        // 시작점 (0,0)에서 종료점 (4,4)로 탈출 가능한지 확인
        if (canEscape(maze, 0, 0, 4, 4)) {
            System.out.println("탈출 가능!");
        } else {
            System.out.println("탈출 불가능!");
        }
    }
}

//`maze`는 미로를 나타내는 2D 배열입니다. `0`은 길, `1`은 벽을 의미.
// `dfs` 함수는 깊이 우선 탐색을 사용하여 
// 현재 위치에서 출구로 가는 경로가 있는지 찾는다.
// 4방향으로 이동할 수 있도록 `dx`, `dy` 배열을 사용해 상하좌우를 탐색한한다.

```
	
- 학습 자료
	- https://www.youtube.com/watch?v=0bqfTzpWySY

---
##### A*

##### 크루스칼 알고리즘

##### 프림 알고리즘

##### 매칭 알고리즘

##### 보안 알고리즘

##### 암호의 기본
##### 해시 함수
##### 대칭키 암호 방식
##### 공개키 암호 방식
##### 하이브리드 암호 방식
##### 디퍼-헬먼 키 교환법
##### 메시지 인증 코드
##### 디지털 서명
##### 디지털 인증서
##### 클러스터링이란?
##### k-평균 알고리즘
##### 데이터 압축과 부호화
##### 런 렝스 부호화
##### 유일 복호 가능 부호
##### 순시 부호
##### 하프만 코드
##### 유클리드 호제법

##### 소수판별법
##### 문자열 매칭
##### 커누스-모리스-프랫 알고리즘
##### 페이지랭크
##### 하노이의 탑
---
##### 출처
- 
---