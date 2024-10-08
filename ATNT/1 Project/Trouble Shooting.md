---
created: 2024-04-18
updated: 2024-09-16
---


----
##### 연결 문서

- 
- 
- 
---

##### Ch 1
- 서버는 구동 되었지만 jpa가 테이블을 찾을 수 없는 경우
	- 해결 : application.yml은 트리 구조 형식이다. jpa 코드가 spring 범위 내 있어야 했는데 spring과 같이 최상위에 존재하였다. 그래서 spring 범위 내에 jpa 코드를 옮겼고 문제가 해결 되었다.
	   
- 스프링 레거시를 사용하여 자동 로그인을 할경우 웹 F12에 쿠키가 정상적으로 등록이 되었지만
	데이터베이스에는 셀렉트하여도 등록되지 않았었다. (다른 사람들은 정상 작동) 
	- 원인
		- 기존에 머물렀던 탭에서 재대로 재배포가 되지않아서 업데이트가 정상적으로 되지 않았었다. 
	- 해결
		- 새탭에서 새로 로컬호스트 서버로 접속하니 정상적으로 셀렉트가 되었다.
	
- 8080 서버 이미 실핼중이라 할 때 해결법
	1. 포트8080을 사용중인 프로세스 찾기
		netstat -ano | findstr :8080
	2. 프로세스 종료하기
		taskkill /PID 1234 /F
	
- 스프링 시큐리티 로그인시 403에러가 뜨는 경우 
	- 원인
		- crsf이 설정 되어있었기 때문이다.
	- 해결
		- crsf 해제를 해서 해결했다.
	
- 더미데이터를 데이터베이스에 넣는 방법
	- 원인
		- sql 쿼리문으로 해결하였다.
	- 해결
		1. use 데이터베이스명
		2. source 경로/파일명.파일타입
		3. source C:/workspace/1PROJE~1/4PROJE~1/dumysql/lodgingCommander_cart.sql;
	
- Obsidian Git 자동 커밋 푸쉬 오류
	- 설명
		- 이 오류는 Git이 `.git/index.lock` 파일을 생성했지만, 정상적으로 삭제되지 않아서 발생하는 문제입니다. 이 파일은 Git의 여러 프로세스가 동시에 실행되는 것을 방지하기 위한 잠금 파일입니다. 주로 Git 명령이 비정상적으로 종료되거나 두 개 이상의 Git 프로세스가 동시에 실행되었을 때 발생합니다.
	- 해결법
		- **Git 프로세스 확인 및 종료**:
		    - 먼저, Git과 관련된 프로세스가 실행 중인지 확인합니다.
		    - Windows에서 작업 관리자를 열고(Git Bash를 사용하는 경우에도 Git과 관련된 프로세스를 찾을 수 있습니다), "git"과 관련된 프로세스가 있으면 종료하세요.
		- **잠금 파일 삭제**:
		    - 문제가 계속 발생하면 `.git/index.lock` 파일을 수동으로 삭제해야 합니다.
		    - 파일 탐색기를 열고, 해당 리포지토리의 `.git` 폴더로 이동합니다. (`C:/workspace/Obsidian/.git/`)
		    - `index.lock` 파일을 찾아 삭제합니다.
		- **Git 명령 다시 시도**:
		    - 잠금 파일을 삭제한 후, 다시 Git 명령을 시도하세요. 예를 들어, `git commit`, `git pull` 등을 시도합니다.
		- **잠금 문제의 원인 파악**:
		    - 이 문제가 반복적으로 발생한다면, Git 명령을 실행할 때 다른 Git 프로세스가 동시에 실행되지 않도록 주의하세요.
		    - 필요하다면 Git을 최신 버전으로 업데이트하거나, 터미널/명령 프롬프트를 새로 고침하여 명령을 다시 실행하는 것도 방법입니다.
	
- N클라우드 가상서버를 이용하여 프로젝트 환경세팅 하는 방법
	
- Next.js 프로젝트에서 `/home` 경로로 리다이렉션할 때 404 오류 발생.
	  
	- 설명
		- Next.js 프로젝트를 개발 중에, 로그인 성공 시 `/home` 경로로 리다이렉션하도록 설정했으나 브라우저에서 404 오류가 발생.
		- Next.js 개발 서버에서 페이지를 찾지 못하고 "This page could not be found" 메시지가 표시됨.
		  
	- 원인 1: 캐시 문제
	  
		- **설명**: 
			- Next.js는 개발 서버에서 캐시를 사용하여 성능을 최적화하지만, 파일 구조 변경이나 라우트 업데이트가 반영되지 않는 경우 캐시된 상태로 프로젝트가 실행될 수 있음.
		- **해결법**:
		    - 서버를 재시작하여 캐시를 초기화하고 라우트를 다시 로드하기 위해 
			    `npm run dev` 명령어를 사용.
		    - 이 명령어는 프로젝트를 다시 빌드하고 파일 시스템을 새로 인식하게 하여 최신 상태를 반영하게 함.
		      
	- 원인 2: 파일 경로 문제
		
		- **설명**: 
			- Next.js는 페이지 라우트를 파일 경로 기반으로 자동 설정하는데, 파일 이름이나 경로에 문제가 있으면 페이지가 올바르게 인식되지 않을 수 있음. `pages/home.tsx` 파일이 존재하지 않거나 대소문자가 일치하지 않을 경우 404 오류가 발생.
		- **해결법**:
		    - `pages` 폴더 내에 `home.tsx` 파일이 존재하는지 확인하고, 라우트 경로(`/home`)와 대소문자가 일치하는지 점검.
		    - Next.js는 대소문자를 구분하므로, 경로와 파일 이름이 일치해야 함.
		
	- 원인 3: 개발 서버 재시작 미반영
		
		- **설명**: 
			- 코드나 파일 변경이 서버에 즉시 반영되지 않는 경우가 발생할 수 있음. 서버가 변경 사항을 제대로 인식하지 못할 때 404 오류가 발생할 수 있음.
		- **해결법**:
		    - 프로젝트의 변경 사항을 인식시키기 위해 `npm run dev`를 통해 개발 서버를 재시작하여 파일 구조와 라우트 설정을 새로 로드.
		    - 서버를 재시작함으로써 새로운 파일을 인식하고 라우팅 설정이 제대로 반영됨.