

----
##### 연결 문서

- 
- 
- 
---

##### 버전 정보
- 스프링 버전
	- Spring 5
- 자바 버전
	- JDK 17
- Gradle 버전
	- 7.3
- DB
	- MySQL
- ERD




##### 기능 요구 사항에 대한 우선순위 지정
- 메인 기능
	- 스터디 목록 노출
	- 스터디 지원 기능
	- 스터디장 등록 (권한 관리)
	- 스터디 등록
		- 위 기능들이 핵심
		- CRUD API
	
- 부가 기능
	- 블랙리스트 기능
	- 스터디 지원자의 이력을 확인 할 수 있는 정보들 
		- 블랙리스트 차단 횟수
		- 지역
		- 모임장 경험
		- 참여한 모임들
	- 키워드 알림을 등록(개발)해서 휴대폰 문자나 이메일로 알림을 제공해주기 -1
	- 지역별 스터디 카페 정보 제공
	- 카테고리를 나눠서 등록할 수 있게 하기
	- 프로젝트와 모각코를 분리
	- 스터디 멤버끼리 웹페이지 안에서 활동할 수 있는 커뮤니티 기능 제공, 과제 제출(파일 업로드 기능), 초대 - 2
	- 채팅 기능 - 3
	
- SRS 문서 작성 방법
	1. 제품의 목적과 범위를 정의한다.
	2. 사용자 요구 사항 및 종속성을 포함하여 무엇을 구축할 것인지 설명한다.
	3. 구체적인 기능적 요구사항과 비기능적 요구사항을 자세히 설명한다.
	4. 중요성과 영향을 기준으로 요구사항의 우선순위를 지정한다. 
	5. 승인 및 피드백을 위해 문서를 전달한다.
	
- ERD Optionality
	- P = 기본키, F = 외래키, C = 후보키
	
	- 사이트 회원가입 기능
		- 회원 ID - P
		- 회원 비밀번호
		- 회원 닉네임
		- 지역
		- 연락처
		- 이메일
		  
	- 사이트 로그인 기능
		- 회원 ID - P
		- 회원 비밀번호
		
	
	- 사이트 회원정보 수정
		- 회원 ID - P
		- 회원 비밀번호
		- 지역
		- 연락처
		- 이메일
		  
	- 사이트 회원 탈퇴
		- 회원 ID - P
		- 회원 비밀번호
	
	- 아이디 찾기 / 비밀번호 찾기
		- 회원 ID - P
		- 회원 이메일 - C
		- 회원 연락처 - C
	
	- 스터디 등록
		- 스터디 등록 게시물 ID - P
		- 회원 닉네임 - C
		- 회원 ID - F
		- 스터디 등록 게시물 제목
		- 스터디 등록 게시물 글
	
	- 스터디 목록 노출
		- 스터디 등록 게시물 ID - P
		- 회원 ID - F
		- 스터디 등록 게시물 제목
		- 스터디 등록 게시물 글
	
	- 스터디 지원 기능
		- 스터디 등록 게시물 ID - P
		- 회원 ID - C
		- 스터디 지원자의 이력을 확인할 수 있는 정보들 - F
		- 회원 닉네임
		- 스터디 지원 소개 글
	
	- 스터디장 등록 (권한 관리)
		- 회원 ID - P
		- 회원 닉네임
	
	- 카테고리를 나눠서 등록할 수 있게 하기
		- 스터디 등록 게시물 ID - P
		- 스터디 테이블(?) - F
		- 모각코 테이블(?) - F
		- 프로젝트 테이블(?) - F
	
	- 스터디 멤버끼리 웹페이지 안에서 활동할 수 있는 커뮤니티 기능제공, 과제 제출 (파일 업로드 기능), 초대
		- 스터디 등록 게시물 ID - P
		- 회원 ID - C
		- 과제 게시물 ID - C
		- 과제 게시물 제목
		- 과제 게시물 글
		- 과제 제출 
		- 스터디원 초대
		- 스터디원 추방
		- 스터디원 블랙리스트
		- 스터디원 차단
	
	- 채팅 기능
		- 채팅 ID - P
		- 회원 ID - F
		- 스터디 지원자의 채팅 참여 닉네임
		- 메시지 ID
		- 보낸 사람 ID
		- 메시지 내용 ID
		- 메시지 전송시간
	
	- 블랙리스트 기능
		- 회원 ID - P
		- 참여자 닉네임 - C
		- 블랙리스트 등록 / 해제
	
	- 스터디 지원자의 이력을 확인할 수 있는 정보들
		- 회원 ID - P
		- 회원 닉네임
		- 회원 지역 정보
		- 블랙리스트 횟수
		- 스터디장 횟수
		- 지역 정보
		- 차단한 회원인지 식별
		- 진행중인 스터디 개수
		- 총 진행했던 스터디 개수
	
	- 지역별 스터디 카페 정보 제공
		- 회원 ID - P
		- 지역 ID - F
		- 스터디 카페 ID - C
		- 스터디 카페 이용 정보
		- 스터디 카페 예약 신청


#### ERD 
##### 1. 요구사항 분석
- 회원가입 페이지
	- 회원가입 버튼을 클릭
	- 회원 ID, 비밀번호, 비밀번호 확인을 입력
	- 회원 ID은 최소 4자 알파벳 대소문자(A~Z, a~z), 숫자(0~9)을 구성
	- 비밀번호는 최소 4자 이상으로 회원 ID과 중복된 값이 포함 될 경우 회원가입 실패로 만들기
	- 비밀번호 확인은 비밀번호와 정확하게 일치하기
	- 데이터베이스에 존재하는 회원 ID을 입력한 채 회원가입 버튼을 누를 경우 "중복되는 회원 ID입니다."라는 에러메세지를 프론트엔드에서 보여주기
	- 회원가입 버튼을 누르고 에러 메세지가 발생하지 않는다면 '로그인 페이지'로 이동시키기
	  
- 로그인 페이지
	- 로그인, 회원가입 버튼 만들기
	- 회원 ID 비밀번호 입력란 만들기
	- 로그인 버튼을 누를 경우 회원 ID과 비밀번호가 데이터베이스에 등록 되었는지 확인한 뒤, 하나라도 맞지 않는 정보가 있다면, "회원 ID 또는 패스워드를 입력해주세요"라는 메세지를 프론트엔드에서 보여주기
	- 로그인 버튼을 눌러서 에러 메세지가 나타지 않는다면 '전체 게시글 목록 조회 페이지'로 이동
	  
- 로그인 검사
	- '아래 페이지를 제외하고' 모든 페이지를 로그인한 경우만 볼 수 있도록 하기.
		- 회원가입 페이지
		- 로그인 페이지
		- 게시물 목록 조회 페이지
		- 게시물 조회 페이지
	- 로그인을 하지 않거나 올바르지 않은 경로로 접속한 사용자가 로그인이 필요한 경로에 접속을 시도할 경우 "로그인이 필요합니다"라는 메세지를 프론트엔드에서 띄어주고, "로그인 페이지"로 이동시키기
	- 로그인 한 사용자가 로그인 페이지 또는 회원가입 페이지에 접속한 경우 "이미 로그인 되어있습니다."라는 메세지를 띄우고 '게시글 목록 조회 페이지'로 이동시키기
	
- 게시물 목록 조회 페이지
	- 비로그인 회원일 경우 우측 상단에 회원가입 / 로그인 버튼을 보여준다.
	- 로그인한 회원일 경우 우측 상단에 내정보 / 스터디활동 / 로그아웃 버튼을 보여준다.
	- 카테고리에는 '스터디', '모각코', '프로젝트' 버튼을 만들고 해당 버튼을 누를 경우 그에 맞는 전용 게시판 페이지로 이동한다.
	  (편의상 아래의 설명들의 카테고리를 '스터디'로 통일한다.)
	- 게시물 목록 조회 페이지는 '게시물 번호', '게시물 제목', '작성자 ID'가 보이도록 한다.
		- 블랙리스트 또는 차단한 회원이라면?
			- 게시물 글 색깔을 빨간색으로 보이게 한다.
			- 게시물을 아예 안보이자 않도록 한다.
	- 게시물 제목, 작성자를 검색하여 조회할 수 있는 검색 조회 입력 버튼을 보여주고, 입력한 내용이 일부라도 일치하는 게시물들만 조회한다. 
		- 최소 문자는 2자 이상만, 숫자는 4자 이상만 입력되도록 하고 조건을 만족하지 못할 경우 "최소 문자 2자 이상, 숫자 4자 이상을 입력해주세요"라는 에러메세지를 프론트엔드에서 띄워준다.
		- 입력한 내용의 결과가 없을 경우 게시물 목록에 "검색한 결과가 없습니다."라는 문구를 프론트엔드에서 보여준다.
	- 비로그인의 회원 경우
		- 글쓰기 버튼이 출력이 되지 않는다. 
	- 각 해당 게시물을 클릭 할 경우 게시물 번호가 데이터베이스와 일치하는 '게시물 페이지'로 이동한다.
	  
- 게시물 조회 페이지
	- 글 제목, 작성자, 글 내용, 작성자의 정보(지역, 스터디 횟수, 스터디장 횟수 등)를 보여주도록 한다.
	- 게시물 작성자일 경우 글 삭제, 글 수정 버튼이 보이도록 한다.
	
- 게시물 작성 페이지
	- 제목, 내용을 입력하는 상자가 나오도록 한다.
	- 게시물 작성 버튼, 취소 버튼, 임시저장 버튼을 만든다.
	
- 게시물 조회 페이지 / 지원하기
	- 지원하기 버튼을 만들면 추가 정보를 입력하는 상자가 나오도록 하고, 지원자의 메세지, 지원자 정보(작성자 정보와 동일)를 게시물 작성자에게 보여주도록 한다.
	- 블랙리스트 혹은 차단한 회원이 지원할 경우 아이디 옆에 "블랙리스트", "차단한 회원"이라는 문구를 프론트엔드에서 보여준다.
	- 글 작성자만 볼 수 있는 지원자 목록 버튼을 만들어준다.
	- 지원자 목록 버튼을 누르면 지원자의 아이디를 조회한다. 그리고 아이디를 누르면 지원자 정보와 지원자 메세지를 보여준다. 그 밑에 지원자 수락 버튼을 만든다.
	- 지원자 수락을 누르면 "스터디 활동 게시물 페이지"에 지원자만 접근할 수있도록 권한을 부여하며 지원자의 활동 스터디에 추가된다.
	  
- 스터디 활동 게시물 페이지
	- 스터디 지원 게시물 작성자가 게시물을 생성할 경우 자동으로 같이 생성한다.
	- 우측 상단에 스터디 활동 버튼을 클릭하면 활동 중인 스터디 활동 게시판 목록이 조회된다.
	- 스터디 활동 게시물 목록에는 스터디 활동 게시물 글번호, 글 제목, 스터디 인원을 보여준다.
	- 스터디 활동 게시물 중 하나를 클릭하면 해당 글번호와 데이터베이스에 일치하는 게시물로 이동한다.
	- (대체 제가 무슨 짓을 저지른거죠)
	- 스터디 활동 게시물에 '스터디 일정 버튼', '스터디 탈퇴 버튼'을 만든다.
	- 스터디 활동 게시물에 스터디장만 볼 수 있는 '스터디 일정 추가 버튼'을 만든다.
	
- 스터디 활동 게시물 페이지 > 스터디 일정 페이지
	- '스터디 일정 추가 버튼'을 누르면 '스터디 일정 추가 게시물 페이지'로 이동한다.
	- 스터디장, 스터디원은 '스터디 일정 버튼'을 클릭하면 '스터디 일정 조회 페이지'로 이동한다.
	
- 스터디 활동 게시물 페이지 > 스터디 일정 추가 페이지
	- 스터디 일정 제목, 날짜, 장소, 내용을 입력할 수 있는 입력 버튼을 만든다.
	- 일정 기한을 추가하여 기한이 지나면 자동으로 일정에 더 이상 조회, 수정, 버튼을 비활성화하고 글자 색을 회색으로 변경되도록 한다.
	  
- 스터디 활동 게시물 페이지 > 스터디 일정 조회 페이지
	- 스터디장과 스터디원은 조회하여 나오는 스터디 일정을 클릭 하여 열람할 수 있다.
	- 조회 페이지에는 제목, 날짜, 기한만 보여주도록 한다.
	- 제목을 클릭하면 내용, 장소 정보도 같이 보여주도록하고, 참석, 불참 버튼을 보여준다.
	- 참석, 불참을 클릭한 스터디원의 닉네임을 아래에 조회되도록 보여준다.
	  
- 스터디 활동 게시물 페이지 > 스터디원 목록 조회 페이지
	- 스터디활동 게시물에 참여하고 있는 모든 회원 ID를 보여준다.
	- 스터디원을 클릭할 경우 해당 스터디원의 정보를 조회할 수 있는 작은 상자를 보여주고, '스터디장 위임 버튼', '스터디원 추방 버튼'을 보여준다.
	- 스터디장 위임 버튼을 클릭할 경우 "정말 스터디장 위임을 하시겠습니까?"라는 문구를 프론트엔드에서 출력하며 예/아니오 버튼을 보여주고 예 버튼을 누를 경우 스터디장을 위임하여 현 스터디장은 스터디원으로 변경되고 위임된 스터디원은 스터디장으로 변경한다. 아니오 버튼을 누를 경우 스터디원 작은 상자를 닫고 아무런 변경을 하지 않는다.
	- 스터디원 추방 버튼을 누를 경우 해당 스터디원을 스터디 활동 게시물에 접근할 수 없도록 변경한다. 
	- 스터디장 위임, 스터디원 추방을 할 경우 해당 모든 스터디원에게 이메일 또는 전화 번호로 문자가 자동으로 메세지로 보내도록 한다.
	
- 스터디 활동 게시물 페이지 > 탈퇴
	- 스터디원이 탈퇴 버튼을 누르면 스터디 게시물로부터 접근이 불가능해진다.
	- 스터디장이 탈퇴 버튼을 누르면 "스터디장을 위임한 후 탈퇴가 가능합니다"라는 메세지를 프론트엔드에서 띄어준다.
	  
	  
	  
- 내가 느끼는 문제점
	- 요구사항이 난잡해보인다.
	- 추가 또는 추가 안해도 될 내용이 있을 것 같은 예감이 든다.
	- 

#### 2. Entity와 Attribute 추출

 - 회원 - Member
    
	- 회원 아이디 - memberId
	- 회원 비밀번호 - memberPassword
	- 회원 비밀번호 확인 - memberPasswordChecking
	- 차단한 회원 - blockedMember
	- 블랙리스트 - blackList
	- 지역 - memberRegion
	- 이메일 - memberEmail
	- 전화번호- memberPhoneNumber
	- 스터디 횟수 - studyParticipationCount
	- 스터디장 횟수 - studyLeadershipCount
	
- 모집 게시물 - RecruitmentTable
	
	- 모집 게시물 번호 - recruitmentTableNumber
	- 모집 게시물 제목 - recruitmentTableTitle
	- 모집 게시물 내용 - recruitmentTableContent
	- 모집 게시물 날짜 - recruitmentTableDate
	- 스터디 신청 메세지 - studyApplicationMessage
	
- 스터디 활동 게시물 - StudyTable
	
	- 스터디 게시물 번호 - studyTableNumber
	- 스터디 게시물 제목 - studyTableTitle
	- 스터디 게시물 개설일 - studyTableDate
	- 스터디 인원 - studyParticipants
	- 일정 게시물 번호 - scheduleTableNumber
	- 일정 게시물 제목 - scheduleTableTitle
	- 일정 게시물 내용 - scheduleTableContent
	- 일정 게시물 날짜 - scheduleTableDate
	- 과제 제출 업로드 - assignmentSubmissionUpload
	
- 스터디 카페 정보 제공 - Study_Cafe_Info
	
- 채팅방 - Chat
	   

#### 3. Entity간의 관계 추출

- 회원 - 모집 게시물
	- 관계 : 보유
	- 관계 참여하는 개체
		- 회원은 여러개 모집 게시물을 가질 수 있다.
		- 모집 게시물은 1개의 회원을 가진다.
	- 관계 유형 : 1:N
	  
- 회원 - 스터디 활동 게시물
	- 관계 :  보유
	- 관계 참여하는 개체
		- 회원은 여러개의 스터디 활동 게시물을 가질 수 있다.
		- 스터디 활동 게시물은 여러개의 회원을 가질 수 있다.
	- 관계 유형 : N:N
	
- 모집 게시물 - 스터디 활동 게시물
	- 관계 : 
	- 관계 참여하는 개체
		- 모집 게시물은 스터디 활동 게시물은 한개만 가진다.
		- 스터디 활동 게시물은 모집 게시물을 한개망 가진다.
	- 관계 유형 : 1:1


#### 4. ERD 작성

#### 타임라인 
- 1주차 ERD 설계, Git 올바른 사용법 및 명령어 연습 
- 2주차 ERD 설계 피드백
- 3주차 ERD 설계 피드백 승인
- 4주차 개발 환경 세팅, JPA Entity 세팅
- 5주
