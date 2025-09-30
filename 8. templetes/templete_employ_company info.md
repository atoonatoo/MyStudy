---
title: <% tp.file.title.split("_") [2] %>
type: info
director: employ
site: <% tp.system.suggester(["사람인", "원티드", "로켓펀치"], ["사람인", "원티드", "로켓펀치"]) %>
rate: <% tp.system.suggester(["A", "B", "C"], ["A", "B", "C" ]) %>
status: <% tp.system.suggester(["미지원", "지원 완료", "서류 탈락", "1차 면접 불합격", "최종 면접 불합격", "서류 합격", "1차 면접 합격", "최종 합격"], ["미지원", "지원 완료", "서류 탈락", "1차 면접 불합격", "최종 면접 불합격", "서류 합격", "1차 면접 합격", "최종 합격"]) %>
support date: <% tp.date.now("YYYY-MM-DD") %>
deadline:
url:
website:
tags:
  - employment
---






