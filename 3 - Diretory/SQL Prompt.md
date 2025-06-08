---
created:
---
---
- [[0 Home]]
---

- DB 테이블 전부 삭제 및 재생성
```sql
DROP DATABASE your_database_name;
CREATE DATABASE your_database_name;
USE your_database_name;
	
 - 이 명령어는 기존 데이터베이스를 삭제한 후 다시 생성하고, 
 - 해당 데이터베이스를 사용하기 위한 명령어이다.
```

- 테이블 데이터 지우기
```sql
SET FOREIGN_KEY_CHECKS = 0;

DELETE FROM users;

SET FOREIGN_KEY_CHECKS = 1;


- 주의 사항
	- 테이블 참조가 되어서 외래 키 제약조건때문에 직접 지우기 불가능한 경우
	- 일시적으로 외래키 제약 비활성화 후
	- `실제 업무에는 위험` `테스트 DB에만 사용할 것`
```

- sql 파일 cli을 통하여 Local DB에 삽입하기
```sql
SOURCE C:/Users/kkk96/Downloads/jmeter/playlist2/test02/users.sql;
SOURCE C:/Users/kkk96/Downloads/jmeter/playlist2/test02/video.sql;
SOURCE C:/Users/kkk96/Downloads/jmeter/playlist2/test02/playlist.sql;
SOURCE C:/Users/kkk96/Downloads/jmeter/playlist2/test02/playlist_video.sql;
```

- 테이블 가장 위에 있는 데이터만 SELECT 하는 명령어
```SQL
SELECT * FROM users ORDER BY id ASC LIMIT 1;
```

- 테이블 가장 아래에 있는 데이터만 SELECT 하는 명령어
```SQL
SELECT * FROM users ORDER BY id DESC LIMIT 1;
```
---