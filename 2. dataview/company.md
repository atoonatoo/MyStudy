---
title: company info
type: link
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
    ("[" + file.name + "](" + url + ")") as "회사명",
    site as "공고 사이트",
    rate as "등급", 
    status as "지원 현황",
    dateformat(date, "yy/MM/dd") as "지원일",
    choice(deadline, dateformat(deadline, "yy/MM/dd"), "") as "마감일",
    website as "면접 후기"
FROM "7. employ/company info"
FLATTEN date(date) as applyDate
WHERE applyDate >= date(2025-12-01)


```


---