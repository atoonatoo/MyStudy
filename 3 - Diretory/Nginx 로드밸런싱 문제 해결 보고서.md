---
created:
---
---
- [[0 Home]]
---

- **Nginx 로드밸런싱 문제 해결 보고서**

-  문제 요약
	- `localhost` 접속 시 **"Welcome to nginx!"** 화면만 출력됨
	- 의도한 Spring Boot 서버 (8080, 8081) 로드밸런싱이 작동하지 않음
---
- 원인 분석

| 항목                            | 설명                                              |
| ----------------------------- | ----------------------------------------------- |
| ✅ `nginx.conf` 문법 확인 (`-t`)   | 정상 (`syntax is ok`, `test is successful`)       |
| ❌ 실행 시 `-c` 옵션 누락             | 커스텀 conf가 아닌 **기본 conf**(`conf/nginx.conf`) 사용됨 |
| ⛔ 기본 conf는 `proxy_pass` 설정 없음 | HTML root만 서빙 → "Welcome to nginx!" 화면 출력       |

---

- 해결 방법
```bash
# PowerShell로 실행

# 1. 기존 프로세스 종료
taskkill /F /IM nginx.exe

# 2. 정확한 conf로 다시 실행 (※ 공백 주의)
cd C:\nginx-1.28.0
.\nginx.exe -c "C:\Users\kkk96\workspace\2 project\team\techie\back-end\nginx\nginx.conf"


# -c : -c가 없으면 기본 경로로 찾고, -c가 있어야 지정 경로로 찾는다.
```

---