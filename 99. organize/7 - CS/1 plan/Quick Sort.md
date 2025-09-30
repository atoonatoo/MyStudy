
---
- [[CS]]
---
### 퀵 정렬 Quick Sort

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

