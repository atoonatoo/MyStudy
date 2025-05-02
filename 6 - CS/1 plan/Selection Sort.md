
---
- [[CS]]
---

### 선택 정렬 Selection Sort

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
