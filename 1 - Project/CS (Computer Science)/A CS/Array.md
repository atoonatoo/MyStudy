---
created:
---
---
# **README**

- 이 문서는 자료 구조의 배열에 대해 다룬다.

### 정의

- 같은 타입의 데이터를 순차적으로 저장하는 자료 구조
- 배열은 고정된 크기를 가지고 있으며, 이 크기는 배열을 생성할 때 정해진다.
- 각 데이터는 배열의 인덱스를 통해 접근할 수 있다.
- 배열은 가장 기본적인 자료구조이다.

```java
package com.study.practice.dataStructrue;  
  
public class Array {  
    public static void main(String[] args) {  
  
        int[] A = new int[5];  
        A[0] = 1;  
        A[1] = 2;  
        A[2] = 3;  
        A[3] = 4;  
        A[4] = 5;  
  
        String[] B = new String[5];  
        B[0] = "Hello";  
        B[1] = "World";  
        B[2] = "Hello";  
        B[3] = "World";  
        B[4] = "Hello";  
  
        System.out.println(A[0] + B[0]);  
        System.out.println(A[1] + B[1]);  
    }  
}
```

### 특징

- 배열은 같은 타입의 데이터를 여러개 나열한 선형 자료구조이다.
- 대부분 프로그램 언에서 동일한 타입의 데이터를 저장한다.
	- int 타입 배열으로 선언된 경우 정수요소만 저장 가능하다.
- 배열은 생성시 크기를 정하면, 그 크기로 고정이 된다.
- 배열을 구성하는 각각의 값을 요소(element)라고 한다.
- 배열에서의 위치를 가리키는 숫자는 인덱스(index)라고 한다.
	- 각 요소는 인덱스를 사용하여 접근할 수 있다.
- 반복문과 결합하면 많은 데이터로 효율적으로 처리할 수 있다.

### 배열의 사용 

#### 배열 선언

```java
// 1차원 배열 선언
int[] arr1 = new int[5];

// 2차원 배열 선언
int[][] arr2 = new int[3][3];
```

```python
// 1차원 배열 선언
arr1 = [1, 2, 3, 4, 5]

// 2차원 배열 선언
arr2 = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

```c
// 1차원 배열 선언
int arr1[5];

// 2차원 배열 선언
int arr2[3][3];
```

#### 배열 복사

```java
1. 배열의 얕은 복사 -> 주소 값 복사

int[] a = {1,2,3,4,5};
int[] b;
b = a;

2. 배열의 깊은 복사 -> 요소 값 복사

int[] a = {1,2,3,4,5};
int[] b;
b = a.clone();
```

#### for문을 이용한 배열의 간단한 예시

```java
// 정수형 배열 선언과 초기화
   int[] arr = {5, 10, 15, 20, 25};
   
// 배열 요소들의 합을 저장할 변수 초기화
	int sum = 0;

// for 문을 이용하여 배열 요소들의 합 계산
	for (int i = 0; i < arr.length; i++) {
		sum += arr[i];
 }
 
// 결과 출력
   System.out.println("배열 요소들의 합: " + sum);
 }
```








