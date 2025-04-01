---
created:
---
---
- [[CS]]
- [[DataBase]]
---
# 1. 정규화(Normailzation)

## 1.2 목적

---

### 1.2.1 데이터 중복 제거


---

### 1.2.2 이상 현상(Anomaly) 예방

삽입, 갱신, 삭제 등의 작업 시 발생할 수 있는 문제를 최소화

---

## 1.3 주요 정규화

---

### 1.3.1 제1정규형(1NF)

각 필드의 값이 원자값(더 이상 분해할 수 없는 단일 값)이어야 한다.

---

### 1.3.2 제2정규형(2NF)

1NF를 만족하면서, 기본 키에 종속되지 않은 속성이 없어여 한다.

---

### 1.3.3 제3정규형(3NF)

2NF를 만족하면서, 기본 키가 아닌 속성들 사이에 이행적종속(Transitively dependent)이 없어야 한다.

---

### 1.3.4 보이스-코드 정규형(BCNF)

3NF보다 더 엄격한 조건을 추가하여 모든 결정자가 후보 키가 되어야 한다는 규칙이다.

---

## 1.4 비정규화

성능 최적화를 위해 일부러 정규화 과정을 해제하는 전략이 될 수 있다.


---
# 참고 문헌

1. [참고 블로그](https://superohinsung.tistory.com/111)
2. [참고 블로그](https://mangkyu.tistory.com/110)
3. [참고 블로그](https://velog.io/@sukyeongs/Database-Normalization)
4. [참고 블로그](https://hstory0208.tistory.com/entry/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%A0%95%EA%B7%9C%ED%99%94Normalization%EB%9E%80-%EC%98%88%EC%8B%9C%EB%A5%BC-%ED%86%B5%ED%95%B4-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%B4%EB%B3%B4%EC%9E%90)
5. [참고 블로그](https://dev-coco.tistory.com/62)
