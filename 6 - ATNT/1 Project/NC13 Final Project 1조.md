생성일 | {{2024-00-00}}
작성자 | 김동욱


---

# 1. README

#### 프로젝트 이름

## 1. 프로젝트 개요 📋
이 프로젝트는 당근마켓을 벤치마킹 하여 만든 중고 전자제품 등을 개인간의 직거래를 하기위한 사이트입니다. 당근마켓을 이용하며 개인적인 개선점들을 추가하여 보았습니다.

## 2. 프로젝트 팀원 👥
- **김동욱**: 풀스텍 개발 (주요 역할 설명)
- **김준수**: 풀스텍 개발 (주요 역할 설명)
- **이헌재**: 풀스텍 개발 (주요 역할 설명)

## 3. 프론트엔드 기술 스택 🌐

- 이미지로 표시

## 4. 백엔드 기술 스택 🛠

- 이미지로 표시

## 5. 인프라 기술 스택 ☁️

- 이미지로 표시


## 6. 프론트엔드 인프라 구조 📐

 - 이미지를 만들어서 표현

1. 사용자 -> 웹 브라우저
2. 웹 브라우저 -> Next.js (React) 프레임워크
3. Next.js -> 백엔드 API 호출 (Axios 사용)
4. 백엔드 응답 -> UI 업데이트

## 7. 백엔드 인프라 구조 🏗

 - 이미지를 만들어서 표현

1. 사용자 요청 -> Ncloud (Spring Boot API 서버)
2. API 서버 -> MariaDB (데이터베이스 쿼리)
3. MariaDB 응답 -> API 서버 -> 프론트엔드
4. Docker 컨테이너화된 백엔드 서비스

## 8. 프로젝트 규칙 📏

- **소통관련** : 상대의 의견에 피드백할 시 꼭 본인이 생각하는 더 좋은 대안을 이야기 합시다.
- **회의 방식** : 스크럼 회의 진행
- 
#### 8-1 프로젝트 네이밍 규칙 📂

1. **카멜 케이스 사용**
	   
    - 모든 변수명과 메서드명에 **카멜케이스**를 사용.
    - 첫 글자는 소문자로 시작하고, 이후 단어의 첫 글자는 대문자로 작성.
    - **예시**: `totalAmount`, `fetchUserData`
      
2. **메서드명은 동사형으로 작성**
	   
    - **예시**: `calculateTotal()`, `updateUserInfo()`, `sendEmail()`
      
3. **변수명은 명사형으로 작성**
    
    - **예시**: `userName`, `orderList`, `isLoggedIn` (불린형 변수는 `is`, `has` 등으로 시작)
      
4. **클래스명은 명사형 또는 명사구로 작성**
    
    - **예시**: `User`, `OrderManager`, `ProductCatalog`

- **코드 컨벤션**: ESLint 및 Prettier를 사용하여 코드 포맷 통일
- **커밋 메시지**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore` 태그 사용
- **코드 리뷰**: 모든 PR은 최소 1명의 리뷰어가 승인해야 함
- **테스트**: 주요 기능마다 단위 테스트 필수

#### 8-2. GitHub Repository 규칙 📂

- **Main Branch**: 배포용, 항상 안정적인 코드만 병합`
- **Develop Branch**: 개발용, 새로운 기능은 develop 브랜치에서 작업 후 Main으로 병합
- **Feature Branch**: 각 기능별로 브랜치를 따로 만들어서 작업 (`feature/기능명`)

## 10. 프로젝트 테이블 📊
- **사용자 테이블** (`user_table`)
  - `id`: int, Primary Key
  - `username`: varchar(255), Unique
  - `password`: varchar(255)
  - `email`: varchar(255)

## 11. API 명세서 🗂
| 메서드    | 엔드포인트             | 설명        | 요청 본문                | 응답 코드 |
| ------ | ----------------- | --------- | -------------------- | ----- |
| GET    | `/api/posts`      | 게시물 목록 조회 | N/A                  | 200   |
| POST   | `/api/posts`      | 새 게시물 작성  | `{ title, content }` | 201   |
| PUT    | `/api/posts/{id}` | 게시물 수정    | `{ title, content }` | 200   |
| DELETE | `/api/posts/{id}` | 게시물 삭제    | N/A                  | 204   |

## 12. 프로젝트 분기별 보고사항 📅
- **1분기**: 
	- 09/06 ~ 09/13
	- 
- **2분기**:
- **3분기**: 
- **4분기**: 




# 2. Project


# 3. Setting


### 주제
- 인프런 사이트 벤치마킹

### Info
- Naver Cloud
- Docker
- MySQL

### ERD
- Users
- Boards
- Address
- Payments
- Management
- OnlineLecture
- Study

### API 명세서

### Teck Stack

### Dead Line

### API Lifecycle

### Database

### Git 



