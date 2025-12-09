---
title: <% tp.file.title.split("_")[0].slice(0, 30) %>
type: info
director: employ
site: <% tp.system.suggester(["사람인", "원티드", "로켓펀치"], ["사람인", "원티드", "로켓펀치"]) %>
rate: <% tp.system.suggester(["C", "B", "A"], ["C", "B", "A"]) %>
status: <% tp.system.suggester(["지원 완료", "미지원", "서류 탈락", "1차 면접 불합격", "최종 면접 불합격", "서류 합격", "1차 면접 합격", "최종 합격"], ["지원 완료", "미지원", "서류 탈락", "1차 면접 불합격", "최종 면접 불합격", "서류 합격", "1차 면접 합격", "최종 합격"]) %>
date: <% tp.date.now("YYYY-MM-DD") %>
deadline:
url:
tags:
  - employment
website:
---
