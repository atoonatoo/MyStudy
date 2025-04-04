## 📂 tp.file – 현재 파일 정보

<% tp.file.title %>             <!-- 현재 파일 이름 (확장자 제외) -->
<% tp.file.path() %>            <!-- 파일 전체 경로 -->
<% tp.file.folder() %>          <!-- 파일이 속한 폴더 경로 -->
<% tp.file.creation_date("YYYY-MM-DD") %>       <!-- 파일 생성일 -->
<% tp.file.last_modified_date("YYYY-MM-DD HH:mm") %>  <!-- 마지막 수정일 -->

---

## 🗓️ tp.date – 날짜와 시간

<% tp.date.now("YYYY-MM-DD") %>        <!-- 현재 날짜 -->
<% tp.date.now("HH:mm") %>             <!-- 현재 시간 -->
<% tp.date.today("dddd, MMMM Do YYYY") %>    <!-- 오늘 날짜 (요일 포함) -->
<% tp.date.yesterday("YYYY-MM-DD") %>  <!-- 어제 날짜 -->
<% tp.date.tomorrow("YYYY-MM-DD") %>   <!-- 내일 날짜 -->

---

## 🖥️ tp.system – 사용자 입력 & 시스템 기능

<% tp.system.prompt("오늘의 기분은?", "") %>          <!-- 사용자 입력 프롬프트 -->
<% tp.system.suggester(["😊", "😢"], ["기쁨", "슬픔"]) %> <!-- 선택지 제공 후 값 반환 -->
<% tp.system.clipboard() %>                            <!-- 클립보드 내용 삽입 -->

---

## 🧠 tp.user – 사용자 정의 함수

<% tp.user.myFunction() %>           <!-- 사용자 작성 JS 함수 실행 -->

---

## ⚙️ tp.config – 템플레이터 설정

<% tp.config.templates_folder %>       <!-- 템플릿 폴더 경로 -->
<% tp.config.user_scripts_folder %>    <!-- 사용자 스크립트 폴더 경로 -->
