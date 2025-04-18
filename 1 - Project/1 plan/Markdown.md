
---
- [[CS]]
---

# 1. 마크다운 문법이란

마크다운(Markdown)은 텍스트 기반의 마크업 언어로, 간결한 문법을 사용하여 쉽게 문서를 작성할 수 있도록 만들어졌다.

주로 `README 파일`, `블로그`, `문서화`, `노트 작성` 등에 사용된다.

HTML보다 가독성이 좋고 간단하게 문서를 구조화할 수 있다.

---

# 2. 마크다운 기본 문법

## 2.1 제목 (Headers)
> `#`을 사용하여 제목을 만들 수 있다.
`#`의 개수에 따라 제목의 크기가 달라진다.

```markdown
# 제목 1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6
```
---

## 2.2 강조 (Emphasis)
> - 텍스트를 굵게, 기울임, 취소선을 넣을 수 있다.

```markdown
**굵게**
__굵게__
*기울임*
_기울임_
~~취소선~~
```
---

## 2.3 목록 (Lists)
>, *, +를 사용하여 리스트를 만들 수 있다.

```markdown
- 항목 1
- 항목 2
  - 하위 항목 1
  - 하위 항목 2
```
> 1.을 사용하면 번호가 자동으로 매겨진다.

```markdown
1. 첫 번째 항목
2. 두 번째 항목
3. 세 번째 항목
```
---
## 2.4 코드 블록 (Code Block)

> - 백틱(`)을 사용하여 인라인 코드 또는 블록 코드를 작성할 수 있다.

- 인라인 코드
```
```
- 코드 블록 (여러 줄)
```



```
- 프로그래밍 언어 강조
```python
def hello():
    print("Hello, Markdown!")
```
---

## 2.5 링크 (Link)

```markdown
[Google](https://www.google.com)
```
---

## 2.6 이미지 (Images)
```
![이미지 설명](이미지URL)

![Markdown 로고](https://upload.wikimedia.org/wikipedia/commons/4/48/Markdown-mark.svg)
```
---
## 2.7 인용문 (Blockquotes)
> 기호를 사용하여 인용문을 작성할 수 있다.

```markdown
> 이것은 인용문입니다.
>> 중첩된 인용문입니다.
```
---
## 2.8. 수평선 (Horizontal Rules)
> 세 개 이상의 -, *, _을 사용하면 가로선을 만들 수 있습니다.

```markdown
---
***
___
```

---

## 2.9 표 (Tables)
```markdown
| 이름   | 나이 | 직업   |
|--------|-----|-------|
| 김소희 | 25  | 개발자 |
| 홍길동 | 30  | 디자이너 |
```
---

## 2.10. 체크리스트 (Task Lists)

```markdown
- [x] 완료된 항목
- [ ] 미완료된 항목
```
---

## 2.11. 콜아웃 (Call Out)

```markdown
> [!info] 정보
> 이 부분은 정보(Callout) 상자로 표시됩니다.

> [!tip] 팁
> 유용한 팁을 강조하는 Callout 상자입니다.

> [!warning] 경고
> 주의가 필요한 내용이 있을 때 사용합니다.

> [!danger] 위험
> 심각한 경고를 전달할 때 사용합니다.
```
---
# 참고 문헌

1. https://inpa.tistory.com/entry/MarkDown-%F0%9F%93%9A-%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4-%EB%AC%B8%EB%B2%95-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC

---