---
created:
---
---
- [[0 Home]]
---
- [](#)
- [](#)
- [](#)
---

# SQL

- 플레이리스트 GET DETAILS
```SQL
SELECT p.id AS playlist_id, p.name AS playlist_name, v.video_id, v.title FROM playlists p JOIN playlist_video pv ON p.id = pv.playlist_id JOIN video v ON pv.video_id = v.video_id WHERE p.id = 1;
```

