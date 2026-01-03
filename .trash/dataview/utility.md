---
title: utility
type: link
director: dataview
created: 2025-11-10
tags:
---

```dataview
TABLE without id
    ("[" + file.name + "](" + url + ")") as "제목",
    dateformat(file.cday, "yy/MM/dd") as "작성일", 
    tags as "태그", 
    coment as "설명"
FROM "5. link/programing info"
WHERE contains(string(tags), "programing_utility")
```


