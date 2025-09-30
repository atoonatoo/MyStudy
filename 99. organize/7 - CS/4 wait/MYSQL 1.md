---
created: 2024-01-04
updated: 2024-09-16
---
----
##### 연결 문서

- 
- 
- 
---

# **README**






### 명령어

##### root와 같은 모든 권한을 가진 사용자를 만들기

``` sql

-- 1. 새로운 사용자 생성
CREATE USER 'new_user'@'localhost' IDENTIFIED BY 'your_strong_password';

-- 2. 모든 데이터베이스와 테이블에 대한 모든 권한 부여
GRANT ALL PRIVILEGES ON *.* TO 'new_user'@'localhost' WITH GRANT OPTION;

-- 3. 권한 변경 사항 적용
FLUSH PRIVILEGES;

```
