---
title: <% tp.file.title.split("_") [1] %>
type: <% tp.file.title.split("_") [0] %>
director: dataview
created: <% tp.date.now("YYYY-MM-DD") %>
tags:
  - dataview
  - link
---
```dataview
TABLE without id
    ("[" + file.name + "](" + url + ")") as "제목",
    dateformat(file.cday, "yy/MM/dd") as "작성일", 
    tags as "태그", 
    coment as "설명"
FROM "5. link/youtube"
WHERE contains(tags, "channel")
```
