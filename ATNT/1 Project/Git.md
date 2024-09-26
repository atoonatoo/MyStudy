

---


GIT이란?
만든 사람 : 리누스 토발즈
리누스 토발즈 -> 리눅스의 아버지
리눅스? 오픈소스 운영체제
오픈소스? 모든 소스가 공개되어있는 무료 프로그램
모든 소스가 공개 되어있으므로 내가 입맛에 맞추어서 개선해서
나만의 버전을 만들 수 있다.
그러면 리누스 토발즈 아저씨는 왜 깃을 만들었을까?
  
- 1강 Git이란?
	- 버전 관리 시스템의 분류에 속하는 구체적인 프로그램 중 하나이다.
	  
	- 버전 관리란 무엇인가?
		- 우리는 이미 버전 관리를 해보았다.
		- 대학 리포트 과제를 했을 당시 
			- report.xml
			- report-final.xml
			- report-real-final.xml
			  
	- Version Control System
		- 파일의 이름을 더럽히지 않는 버전 관리를 할 수 있다.
		  
	- Version Control System의 목적
		- Backup
		- Recovery
		- Collaboration
		  
	- Version Control System의 대표적인 종류
		- CVS
		- SVN
		- GIT
		  
	- Git은 학습 난이도가 높다.
		- Git을 처음 사용하는 사용자들의 고충..
		- 더 난이도가 낮은 버전관리 시스템도 있다.
			- Dropbox
				- 사업계획서 : 개발자들이 사용하는 서브 버전이나, git과 같은 것을 일반인도 사용할 수 있게 하겠다.
			- Google Drive
			  
	- 그럼에도 불구하고 Git을 사용하는 사람이 왜 이렇게 많은가?
		- 우리의 현실은 Git보다 훨씬 지옥같다.
		- 현업에서의 Git이 주는 이점
			- 버전 관리
			- 협업 및 동시 작업
			- 브랜치 관리
			- 이력 추적
			- 롤백 및 병합
			- 원격 저장소
			- CI/CD 통합
			- 분산 개발
	
- Git 강의
	- 생활 코딩
		- https://www.youtube.com/watch?v=hFJZwOfme6w&list=PLuHgQVnccGMA8iwZwrGyNXCGy2LAAsTXk
	
- Git 명령어
	-  log
		- git의 로그를 보여주는 명령어
		  
	- commit
		- 소스 코드나 프로젝트의 변경 내용을 저장하는 작업을 의미
		- commit은 해당 시점의 프로젝트 상태를 나타내며 기능 추가, 버그 수정, 파일 추가 또는 삭제 등 같은 변경 사항을 포함할 수 있음
		- 각 commit은 고유한 해시값을 가지며, 이를 통해 프로젝트의 버전 관리가 가능
		- commit은 메세지를 통해 변경 내용에 대한 설명을 기록되어 협업자나 프로젝트 개발자의 이해를 도움
		- 이러한 버전 관리 시스템은 프로젝트의 안정성이나 협업 효율성을 향상시키는 데 도움
		
	- branch
		- branch는 commit의 단순한 참조일 뿐이다.
		- 각 branch는 특정 commit을 가리키는 포인터 역할을 한다.
		- branch는 기본적으로 코드의 분기를 나타낸다.
		- 새로운 기능 추가, 버그를 수정하는 작업을 별도 진행할 때 사용
		- 즉, 동일한 소스 코드 기반에서 여러 버전의 작업을 동시에 수행할 수 있도록 해준다.
		  
	- checkout
		- 현재 작업 중인 branch를 변경하거나, 특정 커밋이나 브랜치로 이동하는 데 사용 된다.
		- checkout은 작업 디렉토리를 변경하고 HEAD를 이동 시키는 등의 작업을 수행하기 때문에 주의가 필요하다.
		  
		- 브랜치 변경 
			git checkout [branch name]
		- 커밋 이동
			git checkout [commit_hash]
		- 새 브랜치 생성 및 이동
			git checkout -b [new_branch_name]
		- 파일 복원
			git checkout -- [file_path]
		  
	- merge
		- 현재 내가 작업 중인 브랜치와 내가 선택할 브랜치와 통합을 시키고 싶을 떄 사용하는 명령어
		- 주의 사항
			- 충돌 해결
			- 커밋 메시지 작성
			- 병합 전에 변경사항 커밋
			- 브랜치 스토리 유지
			  
		- 브랜치 병합
			git merge [병합할_브랜치]
		
	- HEAD
		- 상대 참조
			- 캐럿 연산자 | ^
				- git checkout HEAD^
				- 한번에 한 커밋 위로 움직이는 명령어
				- main^은 main의 부모와 같은 의미
				- main^^은 main의 조부모와 같은 의미
				  
			- ~ 연산자 | ~
				- git checkout HEAD~4
				- 한번에 여러 커밋 위로 올라가는 명령어
				- ~[num]
				- git branch -f main HEAD~3 
					- -f 를 넣음으로써 강제로 브랜치를 세번 뒤로 옮긴다.
		
		
	- reset
		- 
		  
	- rebase
		  
	-  init
	- pull
	- push
	- base
	- squash
	- reset
	- revert
	
- 실제 수행 명령어 
	- 브랜치를 새로 생성하고 이름을 부여하는 명령어
		- 브랜치를 생성하고 'develop'이라는 이름을 부여한다.
		- $ git checkout -b develop
	
- Git 용어
	- Fork
		- 다른 사용자의 원격 저장소를 자신의 계정으로 복제하는 것을 의미 
		- 기본적으로 다른 사람의 프로젝트를 가져와 자신만의 버전을 만들고자 할 때 사용
		- Fork는 주로 오픈 소스 프로젝트에서 사용된다. 다른 개발자들의 프로젝트를 자신의 계정으로 가져와 수정하고 개선한 뒤, 이를 다시 제안하는 프로젝트에 기여하는 것이 일반적인 사용 방식이다.
		- Fork를 사용하면 다음과 같은 일을 수행할 수 있다.
			1. 독립적인 작업
			2. 변경사항 제안
			3. 자신만의 버전 유지
			4. 개선 및 수정
	
	- 
	
- Git 로컬 저장소를 원격 저장소와 연동하기 | 초기 세팅
	- echo "#LodgingCommander" >> README.md
		- git 리포지토리에 "git_practcie"라는 README.md 파일을 생성한다.
		  
	- git init 
		- git을 현재 디렉토리로 초기화한다.
		  
	- git add .
		- 아직 commit은 되지 않지만 변경사항에 대한 기록을 README.md에 기록한다.
		  
	- git commit -m "first commit"
		- 커밋을 수행한다. 
		- -m : 커밋 메세지를 적는다.
		  
	- git branch -M main
		- 브랜치 이름을 변경한다.
		- -M : 브랜치 이름 변경한다.
		  
	- git remote add origin https://github.com/atoonatoo/Lodging-Commander.git
		- 현재 로컬 저장소와 원격 저장소와 연동한다.
		  
	- git push -u origin main 
		- (안될경우 밑의 강제적으로 푸쉬를 한다.)
		- 현재 로컬 저장소의 변경 사항을 원격저장소로 푸쉬한다.
		- 로컬 브랜치와 원격 저장소의 특정 브랜치와 연결한다.
		- 로컬 브랜치에서 변경 사항을 푸쉬할 때마다 Git이 자동으로 해당 원격 저장소의 트래킹 브랜치로 push할 수 있도록 한다.
		- -u : git push와 함께 사용되며, 주로 첫번쨰 푸쉬를 할 때 사용한다.
		- -u를 사용하면 이후 간단히 'git push' 명령어 만으로도 연결된 원격 저장소로 변경 사항을 push를 할 수 있다.
		- -u를 사용하지 않으면 직접 브랜치를 명시하여 push해야 하지만, '-u' 옵션을 사용하면 이를 생략할 수 있다.
		  
	- git push -f origin main
		- -f : 강제 push를 수행하도록 하는 옵션
			1. 강제 push를 사용하면 원격 저장소의 이력이 손실 될 수 있다.
			2. 다른 개발자들과의 협업에 충돌이 발생 할 수 있다.
			3. 일반적으로 강제 push는 잘못된 commit이나 충돌을 해결하기 위한 긴급한 조치
		- 강제 push를 하는 이유
			- 로컬 저장소와 원격 저장소와 이력이 일치하지 않을 때
			- 원격 저장소의 변경 내용을 무시하고 강제로 push를 하고 싶을 때
	
- Git Pull Request 보내는 방법
	- Fork
	- clone, remote 설정
		- 
##### Git 정리 목록

- pws
	- 프로젝트 폴더를 저장하는 위치
  
- Git base


- Git Revert & Reset 

- Git force & push

- DB의 Reation은 칼럼간의 참조를 나타내는 용어일 뿐이다.

- Git Rebase

- Git Merge


https://velog.io/@janeljs/git-1

https://learngitbranching.js.org/?locale=ko

https://bantree.tistory.com/437#--%--learngitbranching%--%EC%--%AC%EC%-D%B-%ED%-A%B-





### Git
- Git 그리고 GitHub
    
    ```java
    - Git이란? : 분산형 버전 관리 시스템(Version Control System) 
      * Git : 로컬저장소를 생성 및 관리
      * GitHub : 원격저장소를 생성 및 관리
    - Git의 특징 : 
      * 빠른 속도의 수행에 중점을 둔다.
      * 데이터에서 수정된 부분만 저장한다.
      * 초기 상태에는 공간이 비어있기에 프로그램 자체를 집어넣는 행위도 일부 수정된
        저장에 해당한다.
      
    - 커밋(commit) : git에 수정된 내용을 저장하며 원 저장소를 통해 다른 사용자에 
    	공유하는 행위
      
    - 스테이징(Staging) : 
    	* 디테일한 커밋관리, 개인적인 테스트 및 디버깅, 커밋 단위 관리
    	* 원격저장소로 커밋을 하기 이전에 중간점검 및 디테일한 커밋을 위한 과정
    	* 합동프로젝트의 경우 개인컴퓨터로만 디버깅이나 테스트를 하고싶을 떄
    		이러한 변경사항만 로컬저장소로 보내지않아서 혼선을 주지않기 위함 등 다양한
    		유용한 목적에 이용 할 수 있다.
    	* 디테일한 커밋 관리, 개인적인 테스트 및 디버깅, 커밋 단위 관리
    
    - 변경 내용(Changes) : 
    	* 수정내용 검토, 실수방지, 코드검토
    	* 현재 관리 중인 프로그램과 원격저장소에 저장된 프로그램과 비교하여 
    		어떠한 부분이 변경되었는지 높은 가독성으로 파악할 수 있도록 실시간으로
    		도움을 주는 기능
      
    - Push : 
    	* 커밋한 내용을 원격저장소로 보내는 행위 
    	* 프로그램의 백업과 다른 개발자와의 코드 공유 프로젝트 동기화 등 목적을 
    		가지고 있다.
      
    - Pull : 
    	* 원격저장소에 저장돤 데이터를 가져와 내 로컬저장소의 데이터와 병합하는 행위
    	* 병합된 데이터를 내 로컬저장소에서 관리하여 수정된 데이터를 나도 원격저장소로
    		보내 push한다.
    
    - Brench : 
    	* 기존 원격저장소에 저장된 코드를 바탕으로 작업을 하지만 원격저장소에 저장된
    	  코드는 간섭하지 않고 독자적인 공간에서 코드 추가, 수정, 관리를 하거나 
    		버그 수정 혹은 버전관리나, 작업 병합 등에 사용할 수 있는 유용한 기능
    ```
    
- 원격 저장소 / 로컬저장소
    
    ```java
    - 원격저장소 : 원격서버에 위치한 git 저장소
      (GitHub, GitLab, Bitbucket)
    
    - 로컬저장소 : 내컴퓨터에 위치한 git 저장소


