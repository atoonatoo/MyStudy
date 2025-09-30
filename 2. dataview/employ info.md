---
title: employ info
type: employ
director: dataview
created: 2025-09-29
tags:
  - dataview
  - employment
  - info
---

---

```dataview
TABLE without id
    ("[" + file.name + "](" + url + ")") as "제목",
    site as "지원 사이트",
    rate as "등급", 
    status as "지원 상태",
    dateformat(date, "yy/MM/dd") as "지원일",
    choice(deadline, dateformat(deadline, "yy/MM/dd"), "") as "마감일",
    website as "회사 사이트"
FROM "7. employ/company info"

```

---