<%*
const url = await tp.system.prompt("벨로그 URL을 입력하세요");
if (!url) return;

try {
    // 1. URL 정제 (끝에 붙은 # 이나 ? 등을 완전히 제거)
    const cleanUrl = url.split('#')[0].split('?')[0];
    const parts = cleanUrl.split('/');
    
    // URL에서 유저네임(@atoonatoo)과 슬러그(동시성...) 위치 찾기
    const userPart = parts.find(p => p.startsWith('@'));
    const slugPart = parts[parts.length - 1];

    if (!userPart || !slugPart) {
        throw new Error("URL 형식이 올바르지 않습니다. (@유저네임/글제목 확인)");
    }

    const username = userPart.replace('@', '');
    const slug = decodeURIComponent(slugPart);

    console.log(`[분석 완료] 유저: ${username}, 슬러그: ${slug}`);

    // 2. GraphQL 요청 설정
    const gqlBody = {
        query: `query ReadPost($username: String, $url_slug: String) {
            post(username: $username, url_slug: $url_slug) {
                title
                body
                released_at
                tags { name }
            }
        }`,
        variables: { username, url_slug: slug }
    };

    // 3. API 요청 (브라우저처럼 보이도록 헤더 보강)
    const response = await requestUrl({
        url: 'https://v3.velog.io/graphql',
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36',
            'Referer': 'https://velog.io/'
        },
        body: JSON.stringify(gqlBody)
    });

    // 4. 응답 본문 파싱 전 검사
    if (!response.text) throw new Error("서버 응답이 비어있습니다.");
    
    const result = JSON.parse(response.text);
    const post = result?.data?.post;

    if (!post) throw new Error("글을 찾지 못했습니다. 슬러그를 확인하세요.");

    // 5. 데이터 가공 및 파일 생성
    const { title, body, released_at, tags } = post;
    const date = released_at ? released_at.split('T')[0] : "";
    const tagString = tags?.map(t => t.name).join(", ");
    const safeTitle = title.replace(/[\\/:*?"<>|]/g, "").trim();

    await tp.file.rename(safeTitle);

    tR += `---
title: "${title}"
source: "${url}"
author: "${username}"
tags: [${tagString}]
created: ${date}
---

# ${title}

${body}`;

    new Notice("✅ 성공적으로 가져왔습니다!");

} catch (e) {
    new Notice(`❌ 오류: ${e.message}`);
    console.error("Velog Import Detail:", e);
}
%>