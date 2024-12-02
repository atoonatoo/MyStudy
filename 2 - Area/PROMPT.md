---
created:
---
---
# **README**


- VSCode powershell에서 관리자 모드로 변경해주는 명령어
	  
	Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

- main과 develop과 커밋이 일치하지않을 경우 main에 develop을 덮어 버리기
	git fetch origin develop:develop 
	git checkout main git merge -s ours develop --allow-unrelated-histories 
	git checkout develop -- . 
	git commit -m "[1.0.0] 1차 배포 진행" 
	git push