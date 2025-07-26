---
created:
---
---
- [[0 Home]]
---

1. VSCode powershell에서 관리자 모드로 변경해주는 명령어
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

- filebeat 실행방법
```
cd C:\workspace\filebeat
.\filebeat.exe -e -c filebeat.yml
```

- elasticsearch 실행방법
```
cd C:\workspace\elasticsearch-9.0.3\bin
.\elasticsearch.bat
```

- elasticsearch 정상 동작 확인 하는 방법 및 팁
```
https://localhost:9200
  - 첫 접속 시 로그인 창 → `elastic` 계정 로그인 필요
  - 비밀번호 없을 경우 아래 명령어로 재설정

- elastic 사용자 비밀번호 재설정
.\elasticsearch-reset-password.bat -u elastic --url https://localhost:9200
  - `y` 입력하여 진행
  - 콘솔에 `New value: ...` 출력 → 해당 비밀번호 사용
```

- kibana 실행 방법
```
cd C:\workspace\kibana-9.0.3\bin
.\kibana.bat
---