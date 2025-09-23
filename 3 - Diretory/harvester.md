---
created:
---

---
- [[Home]]
---

- Harvester
	- 로그 파일을 읽고 전송하는 실행 단위
	- Filebeat가 지정한 경로의 로그파일에 그 파일에 새로운 로그 이벤트(줄 단위 추가)가 발생하면 해당 변경을 감지해서 읽기 -> output(Elasticsearch, Logstash 등)으로 전송한다.
	- filebeat가 로그 경로를 보고 파일을 찾으면, 그 파일마다, 하나의 하베스터가 만들어진다. 그 하베스터는 해당 파일을 실시간으로 tail 하면서 로그를 읽어들이고 output(Elasticsearch, Logstash)으로 전송한다.

---