
---
- [[CS]]
---
# 1. JVM의 Class Loader

자바의 클래스들이 언제 어디서 메모리에 올라가고 클래스 멤버들이 초기화되는지, 원리를 알기 위해선 우선 JVM의 클래스 로더의 진행 방식에 대해 알 필요가 있다.

특히나 다음과 같이 내부(중첩) 클래스 중에 static 키워드가 붙고 안붙고의 유무에 따른 메모리 로드 차이와 쓰레드에 세이프하다는 등을 이해하기 위해서는 클래스 로더에 대한 이해가 필요하다.

```java
class Outer {
	class Inner {
    }
    
    static class Holder {
    }
}
```


---

# 참고 문헌

1. https://inpa.tistory.com/entry/JAVA-%E2%98%95-%ED%81%B4%EB%9E%98%EC%8A%A4%EB%8A%94-%EC%96%B8%EC%A0%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC%EC%97%90-%EB%A1%9C%EB%94%A9-%EC%B4%88%EA%B8%B0%ED%99%94-%EB%90%98%EB%8A%94%EA%B0%80-%E2%9D%93
2. https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%9E%90%EB%B0%94%EC%9D%98-%EB%82%B4%EB%B6%80-%ED%81%B4%EB%9E%98%EC%8A%A4%EB%8A%94-static-%EC%9C%BC%EB%A1%9C-%EC%84%A0%EC%96%B8%ED%95%98%EC%9E%90