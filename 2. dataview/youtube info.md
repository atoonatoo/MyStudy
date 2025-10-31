---
title: youtube info
type: link
director: dataview
created: 2025-09-30
tags:
  - dataview
---

```dataview
TABLE without id
    ("[" + file.name + "](" + url + ")") as "제목",
    dateformat(file.cday, "yy/MM/dd") as "작성일", 
    tags as "태그", 
    coment as "설명"
FROM "5. link/youtube"

```
