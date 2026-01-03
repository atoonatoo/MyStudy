---
title: learning
type: document
director: dataview
created: 2025-11-10
tags:
---

```dataview
TABLE without id
    file.link as "제목",
    dateformat(file.cday, "yy/MM/dd") as "작성일", 
    tags as "태그", 
    coment as "설명"
FROM "6. learning"
```


