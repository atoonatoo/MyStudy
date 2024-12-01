---
created:
---
---
# **README**




---
##### **정렬 (Sorting)**

- **무언가를 정리한다.**
- 

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




