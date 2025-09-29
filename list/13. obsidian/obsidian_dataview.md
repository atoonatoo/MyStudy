---
title: dataview
type: obsidian
director: guide
date: 2025-09-29
tags:
  - programing
  - markdown
  - plugin
  - guide
  - obsidian
url: https://www.youtube.com/watch?v=Iv7wCJArqPI&list=PL-KPFbwFiAWA3bR3QSK3w6r_XM0KRzEFl&index=9
---

```dataview
TABLE without id
    ("![!100](" + cover_url + ")") as "썸네일", 
    "[[" + file.name + "|" + substring(file.name, 15) + "]]" as "제목",
    file.cday as "작성일", 
    file.mday as "수정일", 
    tags[0] as "태그", 
    url as "링크"
    
FROM "list/obsidian" AND #markdown OR "list/Code"

WHERE contains(type, "Guide")

SORT title desc

LIMIT 5

GROUP BY dataformat(finish_read_date, "yyyy")

```

```dataview
TABLE without id
    rows.file.link as "제목",
    rows.tags[0] as "태그", 
    rows.url as "링크"
    
FROM "list/obsidian" AND #markdown OR "list/Code"

WHERE contains(type, "Guide")

SORT title desc

LIMIT 5

GROUP BY dateformat(finish_read_date, "yyyy")


```

```dataview
TABLE without id
    "[[" + file.name + "|" + substring(file.name, 15) + "]]" as "제목",
    file.cday as "작성일", 
    file.mday as "수정일", 
    tags[0] as "태그", 
    url as "링크"
    
FROM "list/obsidian" AND #markdown OR "list/Code"

WHERE contains(type, "Guide")

SORT title desc

FLATTEN tags
```

```dataview
LIST
    tags
FROM "list/obsidian" AND #markdown OR "list/Code"

```

