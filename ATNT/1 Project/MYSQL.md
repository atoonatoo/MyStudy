
----
##### 연결 문서

- 
- 
- 
---

##### 명령어

- SQL
	
- DATABASE (SCHEMA)
	- 스키마(데이터베이스) 조회
		- SHOW DATABASES;
	- 스키마 접속 (변경)
	- USE [SCHEMA]

	- CREATE SCHEMA [SCHEMA];
		- 스키마 생성
	- DROP SCHEMA schema_name;
		- 스키마 삭제
	- ALTER AUTHORIZATION ON SCHEMA::schema_name TO new_owner;
		- 
	
- TABLE
	- SHOW TABLES;
		- 테이블 조회
	- DESC [TABLES]
		- 테이블 칼럼 정보
	- CREATE TABLE 
	  
- DELETE FROM [테이블명];
	  
- 테이블 생성
	- User
		CREATE TABLE USER (
	    id INT PRIMARY KEY AUTO_INCREMENT,
	    username VARCHAR(20) NOT NULL,
	    password VARCHAR(20) NOT NULL,
	    nickname VARCHAR(20) NOT NULL
		);
		
	- Board
		CREATE TABLE board ( 
		id INT AUTO_INCREMENT PRIMARY KEY, 
		title VARCHAR(255) NOT NULL, 
		content TEXT NOT NULL, 
		writerId INT DEFAULT NULL, 
		entry_date DATETIME DEFAULT NOW(), 
		modify_date DATETIME DEFAULT NOW() ON UPDATE NOW(), 
		FOREIGN KEY (writerId) REFERENCES `user` (id) 
		ON UPDATE CASCADE ON DELETE CASCADE
		);
		
	- Reply
		CREATE TABLE `board`.`reply` (
		`id` INT NOT NULL AUTO_INCREMENT, 
		`writer_id` INT NOT NULL, 
		`board_id` INT NOT NULL, 
		`content` TEXT NOT NULL, 
		`entry_date` DATETIME NULL DEFAULT NOW(), 
		`modify_date` DATETIME NULL DEFAULT NOW(), 
		PRIMARY KEY (`id`), 
		INDEX `reply_board_fkey_idx` (`board_id` ASC) VISIBLE, 
		INDEX `reply_user_fkey_idx` (`writer_id` ASC) VISIBLE, 
		CONSTRAINT `reply_board_fkey` 
		FOREIGN KEY (`board_id`) 
		REFERENCES `board`.`board` (`id`) 
		ON DELETE CASCADE 
		ON UPDATE CASCADE, 
		CONSTRAINT `reply_user_fkey` 
		FOREIGN KEY (`writer_id`) 
		REFERENCES `board`.`user` (`id`) 
		ON DELETE CASCADE 
		ON UPDATE CASCADE
		);
		
- 테이블 생성 (ver 2.0)
		-- 사용자 테이블 생성
		CREATE TABLE user (
		    id INT PRIMARY KEY AUTO_INCREMENT,
		    username VARCHAR(255) NOT NULL UNIQUE,
		    password VARCHAR(255) NOT NULL,
		    nickname VARCHAR(255) NOT NULL UNIQUE,
		    level ENUM('user', 'expert', 'admin') NOT NULL DEFAULT 'user' 
		);
		
		-- 영화 테이블 생성
		CREATE TABLE movie (
		    id INT PRIMARY KEY AUTO_INCREMENT,
			title VARCHAR(255) NOT NULL UNIQUE,
		    story TEXT NOT NULL,
		    rating VARCHAR(20) NOT NULL
		);
		
		-- CGV 테이블 생성
		CREATE TABLE cgv (
		    id INT PRIMARY KEY AUTO_INCREMENT,
		    name VARCHAR(255) NOT NULL UNIQUE,
		    location VARCHAR(255) NOT NULL,
		    contact INT NOT NULL
		);
		
		-- 사용자와 영화를 연결하는 중간 테이블 생성
		CREATE TABLE user_movie (
		    id INT PRIMARY KEY AUTO_INCREMENT,
		    user_id INT NOT NULL,
		    movie_id INT NOT NULL,
		    FOREIGN KEY (user_id) REFERENCES user(id) ON DELETE CASCADE,
		    FOREIGN KEY (movie_id) REFERENCES movie(id) ON DELETE CASCADE
		);
		
		-- 영화와 CGV를 연결하는 중간 테이블 생성
		CREATE TABLE movie_cgv (
		    id INT PRIMARY KEY AUTO_INCREMENT,
		    movie_id INT NOT NULL,
		    cgv_id INT NOT NULL,

		    FOREIGN KEY (movie_id) REFERENCES movie(id) ON DELETE CASCADE,
		    FOREIGN KEY (cgv_id) REFERENCES cgv(id) ON DELETE CASCADE
		);
	
	  
- 테이블 뒤로 가는 방법
	- DROP TABLE IF EXISTS 테이블명;
	
- 스키마 뒤로 가는 방법
	- USE 데이터베이스명;
	- SELECT * FROM 데이터베이스명.테이블명;
	
- 테이블 구조 확인하는 방법
	- DESCRIBE 테이블이름;


### 스키마, 테이블 생성 및 외래키 조인

- 테이블 생성
		
	- User
		CREATE TABLE `user` ( 
		`id` INT NOT NULL AUTO_INCREMENT, 
		`username` VARCHAR(15) NOT NULL UNIQUE, 
		`title` VARCHAR(22) NOT NULL, 
		`content` VARCHAR(200) NOT NULL, PRIMARY KEY (`id`)
		);
		
	- Board
		CREATE TABLE board ( 
		id INT AUTO_INCREMENT PRIMARY KEY, 
		title VARCHAR(255) NOT NULL, 
		content TEXT NOT NULL, 
		writerId INT DEFAULT NULL, 
		entry_date DATETIME DEFAULT NOW(), 
		modify_date DATETIME DEFAULT NOW() ON UPDATE NOW(), 
		FOREIGN KEY (writerId) REFERENCES `user` (id) 
		ON UPDATE CASCADE ON DELETE CASCADE
		);
		
	- Reply
		CREATE TABLE `board`.`reply` (
		`id` INT NOT NULL AUTO_INCREMENT, 
		`writer_id` INT NOT NULL, 
		`board_id` INT NOT NULL, 
		`content` TEXT NOT NULL, 
		`entry_date` DATETIME NULL DEFAULT NOW(), 
		`modify_date` DATETIME NULL DEFAULT NOW(), 
		PRIMARY KEY (`id`), 
		INDEX `reply_board_fkey_idx` (`board_id` ASC) VISIBLE, 
		INDEX `reply_user_fkey_idx` (`writer_id` ASC) VISIBLE, 
		CONSTRAINT `reply_board_fkey` 
		FOREIGN KEY (`board_id`) 
		REFERENCES `board`.`board` (`id`) 
		ON DELETE CASCADE 
		ON UPDATE CASCADE, 
		CONSTRAINT `reply_user_fkey` 
		FOREIGN KEY (`writer_id`) 
		REFERENCES `board`.`user` (`id`) 
		ON DELETE CASCADE 
		ON UPDATE CASCADE
		);

