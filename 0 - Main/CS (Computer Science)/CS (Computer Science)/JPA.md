---
created: 2024-01-04
updated: 2024-09-19
---
----
##### 연결 문서

- 
- 
- 
---

# **README**



### JPA 기본 문법 및 규칙

##### **Method**

|            |                                         |
| ---------- | --------------------------------------- |
| **method** | **기능**                                  |
| save()     | 레코드 저장 (insert, update)                 |
| findOne()  | primary key로 레코드 한건 찾기                  |
| findAll()  | 전체 레코드 불러오기. 정렬(sort), 페이징(pageable) 가능 |
| count()    | 레코드 갯수                                  |
| delete()   | 레코드 삭제                                  |

##### **Keyword**

|   |   |   |
|---|---|---|
|**메서드 이름 키워드**|**샘플**|**설명**|
|And|findByEmailAndUserId(String email, String userId)|여러필드를 and 로 검색|
|Or|findByEmailOrUserId(String email, String userId)|여러필드를 or 로 검색|
|Between|findByCreatedAtBetween(Date fromDate, Date toDate)|필드의 두 값 사이에 있는 항목 검색|
|LessThan|findByAgeGraterThanEqual(int age)|작은 항목 검색|
|GreaterThanEqual|findByAgeGraterThanEqual(int age)|크거나 같은 항목 검색|
|Like|findByNameLike(String name)|like 검색|
|IsNull|findByJobIsNull()|null 인 항목 검색|
|In|findByJob(String … jobs)|여러 값중에 하나인 항목 검색|
|OrderBy|findByEmailOrderByNameAsc(String email)|검색 결과를 정렬하여 전달|

##### **Quary문 사용가능

- SQL문이 복잡해서 메서드 이름만으로 해결이 안될 때는 직접 쿼리하는 방법도 있다.
- 쿼리문 사용 방법은 참조 문서를 보면 자세히 나와있다.
	- 답은 참조문서에 다 있는거 같다.

```java
public interface UserRepository extends JpaRepository<User, Long> { 
	@Query("select u from User u where u.emailAddress = ?1") 
	User findByEmailAddress(String emailAddress); 
	
	}
```