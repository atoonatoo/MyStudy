---
title: resume info
type: link
director: dataview
created: 2025-10-14
tags:
---
```dataview
TABLE without id
    ("[" + file.name + "](" + url + ")") as "제목",
    dateformat(file.cday, "yy/MM/dd") as "작성일", 
    tags as "태그", 
    coment as "설명"
FROM "5. link/resume"

```