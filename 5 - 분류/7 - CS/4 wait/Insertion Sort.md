---
created:
---
---
- [[Algorithem]]
- 
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
- **출처**
	- [블로그]()
---