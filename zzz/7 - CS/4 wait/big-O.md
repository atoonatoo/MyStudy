---
created:
---
---
- [[zzz/7 - CS/4 wait/Data Structure]]
- [[Algorithem]]
- 
---
### big O 표기법

- 알고리즘의 성능을 나타내는 표기법
- 시간 / 공간 복잡도 예측시 사용
- n(input)값의 증가에 따른 처리 시간 또는 필요 공간 계산

- 점근적 표현법 중 하나이며, 일반적으로 상수와 계수를 제거 하고 알고리즘의 복잡도를 단순화하여 나타낸다.

- 애매해질 수 있는 연산 횟수 계산법을 하나의 일관된 형식으로 만들어준다.

- 즉 알고리즘의 직접적인 모든 연산횟수를 계산하는 것이 아닌 인풋의 증가에 따른 연산 `처리시간의 증가율`을 예측하는 척도
  
- 주요 시간복잡도 & 성능![[Pasted image 20241119140620.png]]

### 시간 복잡도 종류

- **O(1) - Constant Time**
	- input의 크기와 상관없이 항상 일정한 시간소요
	  
```java
public class BigONotation {
    public static void constantTimeExample(int[] arr) {
        // 항상 첫 번째 요소를 출력 (입력 크기와 무관)
        System.out.println(arr[0]);
    }
	
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        constantTimeExample(arr);
    }
}
```
	
- **O(log n)- Logarithmic**
	- 로그 시간, O(1) 다음으로 빠른 시간 복잡도
	  
```java
public class BigONotation {
    public static void logarithmicTimeExample(int n) {
        // n을 2로 나누면서 0이 될 때까지 반복
        while (n > 0) {
            System.out.println(n);
            n = n / 2; // 로그의 핵심: 매 반복마다 검색 범위를 반으로 줄임
        }
    }
	
    public static void main(String[] args) {
        logarithmicTimeExample(16); // 입력 크기 16
    }
}
``` 
	
- **O(n) - Linear**
	- 선형 시간, 인풋의 증가 시 같은 비율로 증가
	  
```java
public class BigONotation {
    public static void linearTimeExample(int[] arr) {
        // 배열을 순차적으로 탐색하며 모든 요소 출력
        for (int num : arr) {
            System.out.println(num);
        }
    }
	
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        linearTimeExample(arr);
    }
}
``` 
	
- **O(n2) - Quadratic**
	- 2차 시간, 인풋의 증가 시 n의 제곱 비율로 증가
	  
```java
public class BigONotation {
    public static void quadraticTimeExample(int[] arr) {
        // 배열의 모든 요소를 두 번 반복하며 출력
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr.length; j++) {
                System.out.println("Pair: " + arr[i] + ", " + arr[j]);
            }
        }
    }
	
    public static void main(String[] args) {
        int[] arr = {1, 2, 3};
        quadraticTimeExample(arr);
    }
}
``` 
	
- **O(n!) - Factorial**
	- 팩토리얼 시간 복잡도, 가장 느린 속도
	  
```java
public class BigONotation {
    public static void factorialTimeExample(int n, String result) {
        // 순열을 생성 (팩토리얼 알고리즘의 특성)
        if (n == 0) {
            System.out.println(result);
            return;
        }
        for (int i = 0; i < n; i++) {
            factorialTimeExample(n - 1, result + i);
        }
    }
	
    public static void main(String[] args) {
        factorialTimeExample(3, ""); // 3! = 6개의 결과 생성
    }
}
``` 
  
* wtat ?
	* 점근적 표현법 : 입력 크기(n)이 매우 크거나, 무한히 증가한다고 가정을 하고 알고리즘 실행시간을 단순화하여 비교하기 위한 수학적 표현
	* 상수 : 알고리즘에서 특정 작업을 수행하는데 걸리는 고정된 시간이나 반복 횟수
	* 계수 : 입력 크기와 함께 곱해지는 숫자, 루프가 실행되는 반복 횟수와 같은 값을 의미


### Big O 표기법의 규칙

1. 최고차항만 표기한다.
2. 상수항 & 영향력 없는 항은 무시한다.
3. "최대한 심플화된 표현을 사용"

- 상수는 인풋 증가의 영향을 받지 않고, 때문에, 증가율 계산에 포함시키지 않는다. 

```java
// 예제 1
1. T(f) = 3n + 1000
2. T(f) = 3n + 1000
3. T(f) = 3n
4. T(f) = n  
5. T(f) = O(n)
   
// 예제 2
1. T(f) = (3n) * (n²)
2. T(f) = 3n * n²
3. T(f) = n * n
4. T(f) = O(n²)

// 예제 3

1. T(f) = 3 * log(n) + 1000
2. T(f) = 3 * log(n) + 1000
3. T(f) = 3 * log(n)
4. T(f) = log(n)
5. T(f) = O(log n)

// 예제 4

1. T(f) = 1000
2. T(f) = 1000
3. T(f) = 1
4. T(f) = O(1)

// 예제 5

1. T(f) = (n) * (n - 1) * (n - 2) * ... * 1
2. T(f) = n!
3. T(f) = O(n!)

```

- **일반적으로 최고차항만 신경하면 된다.**


### 시간 복잡도 계산

#### 예제

- 예제 1
```java
public class BigOExample {
    public static void printElement(int[] arr, int index) {
        // 각 연산이 O(1) (상수 시간 복잡도)
        System.out.println(arr[index]); // 첫 번째 O(1)
        System.out.println(arr[index]); // 두 번째 O(1)
        System.out.println(arr[index]); // 세 번째 O(1)
    }

    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50}; // 배열 선언
        int index = 2; // 특정 인덱스 지정
        printElement(arr, index); // 배열의 인덱스에 해당하는 값 출력
    }
}

// 실행 결과

30 -> O(1) 
30 -> O(1) 
30 -> O(1)

```
- **`arr[index]` 접근:**  
    배열의 특정 인덱스에 접근하는 것은 Java에서 **O(1)** 시간 복잡도를 가집니다.  
    이유는 배열이 메모리 상에서 연속적으로 저장되어 있어, 인덱스를 기반으로 바로 값에 접근하기 때문입니다.
    
- **`System.out.println()` 호출:**  
    각 `System.out.println()` 함수도 상수 시간 연산입니다. (해당 연산은 단순 출력이므로 데이터 크기에 관계없이 일정한 시간에 실행됩니다.)
    
- **최종 시간 복잡도:**  
    T(f) = O(1) + O(1) + O(1) = O(1).
    
    
- 예제 2
```java
public class BigOExample {
    public static void printElements(int n) {
        // 첫 번째 for문
        for (int i = 0; i < n; i++) {
            System.out.println(i + " -> O(1)");
        }
        
        // 두 번째 for문
        for (int i = 0; i < n; i++) {
            System.out.println(i + " -> O(1)");
        }
    }

    public static void main(String[] args) {
        int n = 5; // 반복 횟수
        printElements(n); // n번 반복하며 숫자와 시간 복잡도를 출력
    }
}

// 실행결과

0 -> O(1)
1 -> O(1)
2 -> O(1)
3 -> O(1)
4 -> O(1)
0 -> O(1)
1 -> O(1)
2 -> O(1)
3 -> O(1)
4 -> O(1)
```

1. **첫 번째 루프**와 **두 번째 루프**:
    - 각 루프는 `n`번 반복합니다.
    - 각 반복에서 숫자(`i`)와 해당 연산의 시간 복잡도 **O(1)**을 출력합니다.
      
2. **최종 시간 복잡도**:
    - 첫 번째 루프: `n * O(1)`
    - 두 번째 루프: `n * O(1)`
    - 합하면 `T(f) = n * O(1) + n * O(1) = O(n)`.
	
- 예제 3
```java
import java.util.ArrayList;
import java.util.List;

public class BigOExample {
    public static List<List<Integer>> buildMatrix(int[] arr) {
        List<List<Integer>> matrix = new ArrayList<>(); // O(1)

        // 첫 번째 for문: 배열 크기만큼 반복
        for (int i = 0; i < arr.length; i++) { // 반복 횟수: n
            matrix.add(new ArrayList<>()); // O(1)
            
            // 두 번째 for문: 배열 크기만큼 반복
            for (int j = 0; j < arr.length; j++) { // 반복 횟수: n
                matrix.get(i).add(arr[j]); // O(1)
            }
        }

        return matrix; // O(1)
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3}; // 예제 입력 배열
        List<List<Integer>> result = buildMatrix(arr);

        // 결과 출력
        for (List<Integer> row : result) {
            System.out.println(row);
        }
    }
}

// 실행 결과

[1, 2, 3] 
[1, 2, 3] 
[1, 2, 3]
```

- **`List<List<Integer>> matrix = new ArrayList<>(); -> O(1)`**
    - 배열 리스트를 초기화하는 작업은 상수 시간에 수행됩니다.
      
- **첫 번째 `for` 루프 (외부 루프):**
    - 배열 크기 `n`만큼 반복.
    - 각 반복에서 `matrix.add(new ArrayList<>());`는 **O(1)**.
      
- **두 번째 `for` 루프 (내부 루프):**
    - 외부 루프의 각 반복에서 내부 루프는 배열 크기 `n`만큼 반복.
    - 각 반복에서 `matrix.get(i).add(arr[j]);`는 **O(1)**.
      
- **전체 반복 시간 복잡도:**
    - 외부 루프(`n`) × 내부 루프(`n`) = `O(n * n) = O(n²)`.
      
- **`return matrix; -> O(1)`**
    - 리스트 참조를 반환하는 작업은 **O(1)**.
      
- 최종 시간 복잡도
	T(f) = O(1) + n * O(1) + (n * O(1)) * n + O(1)
	T(f) = O(n²)


### 결론
- input 증가에 따른 연산 **처리시간의 증가율**을 예측하는 척도
- **상수**는 계산에서 **제외**
- **최고차항**만 신경 쓰면된다.

### JS에서 유용한 함수들의 시간복잡도

![[Pasted image 20241119145728.png]]

---
##### 출처
- 
---