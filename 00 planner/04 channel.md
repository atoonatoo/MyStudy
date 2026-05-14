---
title: undefined
type: channel
director: dataview
created: 2025-10-31
tags:
  - dataview
  - link
---

---
### List

- channel
```
```
- chat gpt
```
```
- gemini
```
```
- company
```
```
- learning
```
```
- prompt
```
```
- utility
```
```
- youtube
```
```
---
### Dataview
```dataview
TABLE without id
    ("[" + file.name + "](" + url + ")") as "제목",
    dateformat(file.cday, "yy/MM/dd") as "작성일", 
    tags as "태그", 
    coment as "설명"
FROM "4. link/youtube"
WHERE contains(tags, "channel")
```

---

