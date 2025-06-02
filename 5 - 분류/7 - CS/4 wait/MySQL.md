-- SQL 명령어 정리 및 실무 예제 모음

-- 📁 DATABASE (SCHEMA)
-- 스키마 조회
SHOW DATABASES;

-- 스키마 접속
USE database_name;

-- 스키마 생성
CREATE SCHEMA database_name;

-- 스키마 삭제
DROP SCHEMA schema_name;

-- 스키마 권한 변경 (특정 DBMS 전용)
ALTER AUTHORIZATION ON SCHEMA::schema_name TO new_owner;


-- 📁 TABLE
-- 테이블 목록 조회
SHOW TABLES;

-- 테이블 구조 확인
DESC table_name;
DESCRIBE table_name;

-- 테이블 삭제
DROP TABLE IF EXISTS table_name;

-- 특정 데이터베이스 내 테이블 조회
SELECT * FROM database_name.table_name;


-- 📁 실무 예제 테이블 생성
-- 사용자 테이블
CREATE TABLE user (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    nickname VARCHAR(255) NOT NULL UNIQUE,
    level ENUM('user', 'expert', 'admin') NOT NULL DEFAULT 'user'
);

-- 게시판 테이블
CREATE TABLE board (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    writerId INT DEFAULT NULL,
    entry_date DATETIME DEFAULT NOW(),
    modify_date DATETIME DEFAULT NOW() ON UPDATE NOW(),
    FOREIGN KEY (writerId) REFERENCES user(id)
    ON UPDATE CASCADE ON DELETE CASCADE
);

-- 댓글 테이블
CREATE TABLE reply (
    id INT NOT NULL AUTO_INCREMENT,
    writer_id INT NOT NULL,
    board_id INT NOT NULL,
    content TEXT NOT NULL,
    entry_date DATETIME DEFAULT NOW(),
    modify_date DATETIME DEFAULT NOW(),
    PRIMARY KEY (id),
    INDEX reply_board_idx (board_id),
    INDEX reply_user_idx (writer_id),
    FOREIGN KEY (board_id) REFERENCES board(id) ON DELETE CASCADE ON UPDATE CASCADE,
    FOREIGN KEY (writer_id) REFERENCES user(id) ON DELETE CASCADE ON UPDATE CASCADE
);

-- 영화 테이블
CREATE TABLE movie (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL UNIQUE,
    story TEXT NOT NULL,
    rating VARCHAR(20) NOT NULL
);

-- CGV 테이블
CREATE TABLE cgv (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL UNIQUE,
    location VARCHAR(255) NOT NULL,
    contact INT NOT NULL
);

-- 사용자-영화 관계 테이블
CREATE TABLE user_movie (
    id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    movie_id INT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES user(id) ON DELETE CASCADE,
    FOREIGN KEY (movie_id) REFERENCES movie(id) ON DELETE CASCADE
);

-- 영화-CGV 관계 테이블
CREATE TABLE movie_cgv (
    id INT PRIMARY KEY AUTO_INCREMENT,
    movie_id INT NOT NULL,
    cgv_id INT NOT NULL,
    FOREIGN KEY (movie_id) REFERENCES movie(id) ON DELETE CASCADE,
    FOREIGN KEY (cgv_id) REFERENCES cgv(id) ON DELETE CASCADE
);
