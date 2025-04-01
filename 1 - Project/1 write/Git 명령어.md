### 중요

- 작업 전 저장소 상태를 확인한다.
- 커밋 메시지는 명확하고 간결하게 작성한다.
- 브랜치를 적절히 활용한다.
- 변경 내용을 커밋하기 전에 리뷰한다.
- 주기적으로 작업을 푸시(Push)한다.
- 원격 브랜치 병합(Merge)은 충돌 가능성을 점검한다.
- 병합 충돌 해결 시 신중하게 작업한다.
- 히스토리 조작 명령어는 신중히 사용한다.
- 불필요한 파일을 추적하지 않도록 .gitignore를 설정한다.
- 작업 복구 명령어를 숙지한다.
- 원격 저장소 변경 시 동료와 협업 규칙을 따른다.

---

### 1. 초기화 및 설정

```bash
git init
# 새 저장소를 초기화합니다.

git clone <URL>
# 원격 저장소를 복제합니다.

git config --global user.name "<이름>"
# Git 사용자 이름을 설정합니다.

git config --global user.email "<이메일>"
# Git 사용자 이메일을 설정합니다.

git config --list
# 현재 Git 설정 확인.

```

### 2. 상태 확인 및 변경 사항 추적
```
git status
# 현재 작업 디렉토리 상태 확인.

git diff
# 워킹 디렉토리와 스테이징된 변경 비교.

git diff <브랜치명>
# 현재 브랜치와 다른 브랜치와의 차이점 확인.

git show <커밋ID>
# 특정 커밋의 상세 변경 내역 확인.

git log --graph --oneline --all
# 브랜치와 커밋 히스토리를 그래프로 확인.
```

### 3. 파일 관리
```
git add <파일명>
# 특정 파일을 스테이징합니다.

git add .
# 모든 변경 파일을 스테이징합니다.

git rm <파일명>
# Git에서 파일을 삭제하고 워킹 디렉토리에서도 제거.

git mv <기존파일명> <새파일명>
# 파일 이름 변경 및 추적.

git checkout -- <파일명>
# 변경 사항을 되돌려 마지막 커밋 상태로 복구.

git restore <파일명>
# 파일을 원래 상태로 복구 (checkout 대체 명령어).
```

### 4. commit 관리
```
git commit -m "<메시지>"
# 변경 사항을 커밋합니다.

git commit --amend -m "<수정된 메시지>"
# 마지막 커밋 메시지를 수정.

git commit --no-edit --amend
# 마지막 커밋 내용을 수정하되, 메시지는 유지.

```

### 5. branch 관리

```
git branch
# 로컬 브랜치 목록 확인.

git branch <브랜치명>
# 새 브랜치 생성.

git branch -m <기존브랜치명> <새브랜치명>
# 브랜치 이름 변경.

git branch -d <브랜치명>
# 브랜치 삭제.

git branch -D <브랜치명>
# 브랜치 강제 삭제.

git merge <브랜치명>
# 현재 브랜치에 다른 브랜치를 병합.

git switch <브랜치명>
# 특정 브랜치로 전환.
```

### 6. 원격저장소
```
git remote add <이름> <URL>
# 원격 저장소를 추가합니다.

git remote remove <이름>
# 원격 저장소를 제거합니다.

git remote rename <기존이름> <새이름>
# 원격 저장소 이름 변경.

git remote set-url <이름> <URL>
# 원격 저장소 URL 변경.

git push <원격저장소> <브랜치명>
# 로컬 브랜치를 원격으로 푸시.

git push -u <원격저장소> <브랜치명>
# 원격 브랜치와 로컬 브랜치를 연결.

git fetch --prune
# 삭제된 원격 브랜치를 로컬에서 제거.

git pull --rebase
# 원격 변경 사항을 가져오면서 로컬 커밋 재정렬.
```

### 7. Stash(임시 저장)
```
git stash
# 변경 사항을 임시로 저장.

git stash save "<메시지>"
# Stash에 메시지를 함께 저장.

git stash list
# Stash에 저장된 항목 목록 확인.

git stash pop
# 마지막 Stash 항목을 적용하고 제거.

git stash apply stash@{<번호>}
# 특정 Stash 항목을 적용 (제거하지 않음).

git stash drop stash@{<번호>}
# 특정 Stash 항목을 삭제.

git stash clear
# 모든 Stash 항목을 제거.

```

### 8. 리셋 및 되돌리기
```
git reset <파일명>
# 파일의 스테이징 상태를 취소.

git reset --soft <커밋ID>
# 해당 커밋 이후 변경 사항을 스테이징 상태로 유지.

git reset --mixed <커밋ID>
# 해당 커밋 이후 변경 사항을 스테이징에서 제거.

git reset --hard <커밋ID>
# 해당 커밋 이후 변경 사항을 모두 삭제.

git revert <커밋ID>
# 특정 커밋을 취소하는 새 커밋 생성.

git checkout <커밋ID> <파일명>
# 특정 파일을 이전 커밋 상태로 복원.

```

### 9. 태그(Tag)
```
git tag <태그명>
# 현재 커밋에 태그 생성.

git tag -a <태그명> -m "<메시지>"
# 주석이 있는 태그 생성.

git show <태그명>
# 특정 태그 상세 정보 확인.

git push origin <태그명>
# 특정 태그를 원격 저장소로 푸시.

git push origin --tags
# 모든 태그를 원격 저장소로 푸시.

```

### 10. 기타 명령어
```
git blame <파일명>
# 파일의 각 라인 변경자 및 수정 내역 확인.

git shortlog
# 커밋 로그를 요약 (기여자별 확인 가능).

git cherry <브랜치1> <브랜치2>
# 두 브랜치 간의 차이를 확인.

git bisect start
# 이진 검색을 통해 문제의 원인이 되는 커밋을 찾음.

```