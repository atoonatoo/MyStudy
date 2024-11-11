


----
##### 연결 문서

- 
- 
- 
---

##### 문자열 정수의 합

``` java
- 문제 설명
	한 자리 정수로 이루어진 문자열 `num_str`이 주어질 때, 
	각 자리수의 합을 return하도록 solution 함수를 완성해주세요.
	
- 제한사항
	3 ≤ `num_str` ≤ 100
	
- 입출력의 예
	- num_str
		- "123456789"
		- "100000000"
	- result
		- 45
		- 1
		  
- 입출력 예 설명
	- 문자열 안의 모든 숫자를 더하면 45가 됩니다.
	- 문자열 안의 모든 숫자를 더하면 1이 됩니다.
	
class Solution { public int solution(String num_str) { 
	int answer = 0; // 문자열의 각 문자를 순회 
			
			for (int i = 0; i < num_str.length(); i++) { 
			// 각 문자를 숫자로 변환하고 더하기
				answer += Character.getNumericValue(num_str.charAt(i)); 
			} 
			
			return answer; 
		} 
	}
	
- 비고
	- Character.getNumericValue(num_str.charAt(i));
		- 문자열을 숫자로 바꿔주는 Character 클래스 메서드이다.
		- 알파벳 문자는 유니코드식으로 변환한다.


```
``

##### 정수 부분
``` java
##### 제한사항

- 0 ≤ `flo` ≤ 100
 
- 입출력 예
	- flo
		- 1.42
		- 69.42
	- result
		- 1
		- 69
  
- 입출력 예 설명
	- 1.42의 정수 부분은 1입니다.
	- 69.32의 정수 부분은 69입니다.


class Solution {
    public int solution(double flo) {
        int answer = (int) flo;
        return answer;
    }
}


- 비고
	- 형변환으로 간단하게 해결할 수 있는 문제이다.
	- 처음엔 %로 해결하려 했지만, %는 나머지를 구하는 연산자이기에 
	  적합하지 않다.

```

###
``` java
```

###
``` java
```

###
``` java
```

###
``` java
```

###
``` java
```

###
``` java
```

###
``` java
```

###
``` java
```

