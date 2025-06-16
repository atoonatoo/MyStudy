---
created:
---
---
- [[0 Home]]
---

1. 현재 nginx 상태 확인
```bash
tasklist | findstr nginx
```

2. 현재 떠있는 nginx 전부 강제 종료
```bash
taskkill /f /im nginx.exe
```

4. nginx custom nginx.conf로 실행하는 명령어
```bash
# PowerShell 기준
# 1. 기존 nginx 프로세스 종료 (안 껐다면 충돌 날 수 있음)
# 2. nginx 실행 디렉토리로 이동
# 3. -c 옵션으로 커스텀 nginx.conf 지정하여 실행

taskkill /F /IM nginx.exe

cd C:\nginx-1.28.0
.\nginx.exe -c "C:\Users\kkk96\workspace\2 project\team\techie\back-end\nginx\nginx.conf"

```

---