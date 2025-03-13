---
created:
---
---
- **PowerShell**
	- VSCode powershell에서 관리자 모드로 변경해주는 명령어
		
		Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
---
- **Git**
- main과 develop과 커밋이 일치하지않을 경우 main에 develop을 덮어 버리기
	git fetch origin develop:develop 
	git checkout main git merge -s ours develop --allow-unrelated-histories 
	git checkout develop -- . 
	git commit -m "[1.0.0] 1차 배포 진행" 
	git push
---
- **MarkDown**
	
	- **기본 문법**
		`- **굵게**`
		`- *기울임*`
		`- 리스트`
		`- [ ]` `체크박스`
		- `# 제목`
		- `## 제목`
		- `### 제목`
		- `#### 제목`
		- `##### 제목`
		- `###### 제목`
		-  `---` `구분선`
	
	- **Link**
		- 링크 기본 사용법
			- [[Stream]] 
			- 해당 링크로 이동하게 된다.
			- 해당 링크를 연결하면 그래프 뷰로 연결 리스트가 활성화된다.
			  
		- 링크는 유지하고 타이틀만 변경
			- [[Stream |링크 타이틀만 변경]] 
				- 글자 뒤에 | 를 추가하여 이름 변경해도 링크 위치는 유지된다.
				  
		- 해당 웹피이지로 이동하는 링크
			- [구글](https://google.com)
				- 웹페이지로 이동하는 링크 
				  
		- 로컬 이미지 삽입
			- 옵시디언 내에 이미지 드래그하고 놓기
			- ![[]] 내부에 링크 이미지 주소 입력
			- 이미지 관리를 위해 폴더 단위에 관리하기
			- 설정 - 파일 및 링크 - 새 첨부 파일을 만들 위치 - 아래에 지정된 폴더 - files 폴더 설정
	
	- **명령어 팔레트 즐겨찾기**
		- ctrl + p = 커멘드 실행 즐겨찾기 추가하는 법
		- 설정 - 명령어 팔레트 -
	 
	- **이모티콘**
		- `:memo:` → 📝 (메모)
		- `:book:` → 📚 (책)
		- `:notebook:` → 📓 (노트북)
		- `:page_with_curl:` → 📃 (페이지)
		- `:writing_hand:` → ✍️ (글쓰기 손)
		- `:clipboard:` → 📋 (클립보드)
		- `:bookmark:` → 🔖 (책갈피)
		- `:spiral_notepad:` → 🗒️ (소형 노트)
		- `:pen:` → 🖊️ (펜)
	
	- **테이블**
		
		| 헤더1 | 헤더2 | 헤더3 |
		|-------|-------|-------|
		| 내용1 | 내용2 | 내용3 |
		| 내용4 | 내용5 | 내용6 |
	
	-  **콜아웃**

	
-  PlugIn
	- 1. 코드 직접 실행 기능 (Execute Code)
		
		- 기본 사용법
			- 읽기 모드로 변경 후 Run
			- 에러가 날 경우 - 언어 별 Path 경로를 찾아야 한다.
			- 언어 별 Path 경로 설정 및 찾기
				- cmd which node - Javascript
				- cmd which python - Python
		- 주된 사용 목적
			- 나중에 사용하기 위한 코드
			- 이해를 돕기 위한 학습에 활용
			- 알고리즘 테스트 등
		
	-  2. 코드 블록 스타일 (Code Styler)
		
		###### 코드 블록 - 라인 번호 표시
		코드 블록 - 하이라이트
		- 언어 뒤에 한칸 띄어쓰고  hl:4
		- hl:4
			- 4번째 줄 하이라이트
		- hl:2-5
			- 2번째에서 5번쨰 줄 하이라이트
		- print 
			- print까지 포함하여 하이라이트
		- 여러가지 색상 하이라이트 사용법
			- CodeStyler 설정
			- Choose Settings Page -> code block stylering 변경
			- Choose Codeblock Settings -> CodeBlockBody -> CodeBlockhighlighting 변경
			- add alternative Highlight -> add 버튼
		- error:5
			- 5번째줄에 추가로 만든 error 하이라이트
		``` java hl:4 error:5
		
		import java.util.ArrayList; // 필요한 클래스를 임포트
		
		public class MainClass {
		    public static void main(String[] args) {
		        // ArrayList 인스턴스 생성
		        ArrayList<String> list = new ArrayList<>();
		
		        // 리스트에 항목 추가
		        list.add("Hello");
		        list.add("World");
		
		        // 리스트 항목 출력
		        for (String item : list) {
		            System.out.println(item);
		        }
		    }
		}
		
		
		
		```
		
		###### 코드 블록 - 제목, 링크 추가
		
		``` java title:"코드 블록 - 제목 추가하는 법"
		
		import java.util.ArrayList; // 필요한 클래스를 임포트
		
		public class MainClass {
		    public static void main(String[] args) {
		        // ArrayList 인스턴스 생성
		        ArrayList<String> list = new ArrayList<>();
		
		        // 리스트에 항목 추가
		        list.add("Hello");
		        list.add("World");
		
		        // 리스트 항목 출력
		        for (String item : list) {
		            System.out.println(item);
		        }
		    }
		}
		
		
		```
		
		- 참고할 노트 입력
			- reference의 ref:[[]] 입력
			- 뒤에 title:"" 추가하면 제목은 title이 되지만 링크는 유지된다.
		``` java ref:[[1 CS 목록 - 0%]] title:"타이틀 설정하는 법"
		
		import java.util.ArrayList; // 필요한 클래스를 임포트
		
		public class MainClass {
		    public static void main(String[] args) {
		        // ArrayList 인스턴스 생성
		        ArrayList<String> list = new ArrayList<>();
		
		        // 리스트에 항목 추가
		        list.add("Hello");
		        list.add("World");
		
		        // 리스트 항목 출력
		        for (String item : list) {
		            System.out.println(item);
		        }
		    }
		}
		
		
		
		```
		###### 코드 블록 - 아이콘, 태그 추가, 헤더 스타일 추가
		
		- **아이콘 포함 기능**
			- Choose Codeblock settings
				- Codeblock header 변경
				- Language Tag, Icon -> Always 변경
		``` python 
		
		import java.util.ArrayList; // 필요한 클래스를 임포트
		
		public class MainClass {
		    public static void main(String[] args) {
		        // ArrayList 인스턴스 생성
		        ArrayList<String> list = new ArrayList<>();
		
		        // 리스트에 항목 추가
		        list.add("Hello");
		        list.add("World");
		
		        // 리스트 항목 출력
		        for (String item : list) {
		            System.out.println(item);
		        }
		    }
		}
		
		
		```
		
		- **인라인 코드 - 스타일링**
			- `console.log("hello world")`
			- 앞에 중괄호 추가하고 안에 언어
			- {js}
			- `{js}console.log("hello world")`
			- `{java}System.out.print("hello world");`
			
			- `{js icon title:" 인라인 블록 타이틀 추가 테스트"}console.log("hello world")`
		
		- **인라인 코드 - CSS 스니펫**
			- 
		
	- 3. 소스 코드 파일 - VScode Editor 
		- VScode처럼 코드를 실행 및 편집할 수 있다.
		- Ctrl + P = 명령어창 열기
		- vscode 입력
		- create new code file
		- 새로운 제목 입력
		- 확장자 선택
		- create 선택
		
	- 4. 불필요한 파일 정리 (File cleaner redux)
		
	- 5. 노트별 뷰 모드 개별 설정 (Force note view mode)
		
	- 6. 슬래시(/)로 명령어 입력 (Slash commander)
		
	- 7. 태그 관리 플러그인 (Tag wrangler)
		
	- 8. 리본, 탭바 등 아이콘 생성 (Commander)
		
	- 9. 리본 원클릭 노트 열기 (Pinned note)
		
	-  10. 웹페이지 스크랩 (Slurp)
		
	- 11. 노트 마지막 커서 위치 기억 (Remember cursor position)



---


