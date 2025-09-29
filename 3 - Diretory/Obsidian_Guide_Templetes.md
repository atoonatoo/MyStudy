---
title:
type:
director:
date: 2025-09-29
tags:
  - programing
  - obsidian_community_plugin
  - markdown
url: https://www.youtube.com/watch?v=17tThWhNNGw&list=PL-KPFbwFiAWA3bR3QSK3w6r_XM0KRzEFl&index=6&pp=iAQB
---

- **명령어**
    - Ctrl + R : Replace templates in the active file (활성 파일의 템플릿을 바꾸는 명령어)

- 노트 생성 날짜
<% tp.file.creation_date("YY년MM월DD일 hh:mm") %>

-  노트저장폴더
<% tp.file.folder() %>

- 노트의 PC 경로
<% tp.file.path() %>

- split
<% tp.file.title.split("_") [0] %>

- **tp_data**
<% tp.date.now("YYYY-MM-DD") %>
<% tp.date.tomorrow("YYYY-MM-DD") %>

- **tp_system**

- 클립보드
<% tp.system.clipboard() %>

- 드롭다운 메뉴
<% tp.system.suggester(["A급", "B급", "C급"], ["A", "B", "C"]) %>

- 텍스트 필드

<% tp.system.prompt("오늘의 기분은?", "") %>
