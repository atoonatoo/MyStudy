---
created:
---

---
- [[Algorithem]]
- 
- 
---
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
##### 출처
- 
---