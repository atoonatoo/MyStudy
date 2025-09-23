---
created:
---
---
- [[Home]]
---

- git 리포지토리 클론 
```
cd C:\workspace\obsidian
git clone https://github.com/atoonatoo/MyStudy.git
cd MyStudy
git status
```

- git 리포지토리 연동 해제
```git
git remote remove origin

- 로컬 Git 저장소에서 원격 저장소 연결을 해제하는 명령어 
- 주로 원격 저장소를 변경하거나 삭제할 때 사용
```

- main과 develop과 커밋이 일치하지않을 경우 main에 develop을 덮어 버리는 방법
```git
git fetch origin develop:develop 
git checkout main git merge -s ours develop --allow-unrelated-histories 
git checkout develop -- . 
git commit -m "[1.0.0] 1차 배포 진행" 
git push
```

---