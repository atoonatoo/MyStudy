---
title: 로아
type: lostark ingame info site
director: project
date: 2025-10-14
tags:
  - programing
  - project
---
---
# 1. 필요 기술 스택

## 0) 권장 기본 스택 (서버리스, 비용≈0원)

- **프런트엔드**: Next.js(App Router) + TypeScript, Tailwind CSS, shadcn/ui, React Hook Form, Zod, TanStack Query(SWR 대체)
    
- **호스팅/SSR**: Vercel (ISR/Edge Functions, Cron)
    
- **DB & 인증**: Supabase(Postgres, RLS, Auth, Storage)
    
- **캐시/레이트리미트**: Upstash Redis + `@upstash/ratelimit`
    
- **분석/로그**: Umami(또는 Plausible) + Sentry(오류)
    
- **SEO**: `next-seo`, `next-sitemap`, OG 이미지 자동 생성(Route Handler)
    
- **컨텐츠 관리**: MDX + Contentlayer(가이드 문서) 또는 Sanity/Notion API(경량 CMS)
    
- **알림/메일**: Resend 또는 Postmark(비번 재설정/공지)
    
- **푸시/스케줄**: Web Push(서비스워커) 또는 Vercel Cron + Discord Webhook
    
- **이미지/CDN**: Next/Image + Vercel 이미지 최적화
    
- **광고/수익**: Google AdSense(웹), 쿠팡파트너스(제휴), 후원(BuyMeACoffee/토스)
    
- **보안 헤더**: Next Middleware로 CSP/Frame-Ancestors/HSTS 설정
    
- **테스트/품질**: Playwright(E2E), Vitest/RTL(Unit), ESLint, Prettier
    
- **CI/CD**: GitHub → Vercel 자동 배포(프리뷰/프로덕션)
    

---

## 1) 프런트엔드

- **프레임워크**: Next.js(App Router, Server Actions), React 18
    
- **언어/품질**: TypeScript, ESLint, Prettier, Husky+lint-staged
    
- **스타일/UI**: Tailwind CSS, shadcn/ui, Radix UI, Framer Motion(선택)
    
- **상태/데이터**: TanStack Query, Zustand(경량 전역상태), Zod(런타임 검증)
    
- **폼/유효성**: React Hook Form + Zod
    
- **국제화(i18n)**: `next-intl` 또는 `@lingui/core`
    
- **접근성**: Headless UI/Radix A11y 패턴, Axe DevTools
    

## 2) 백엔드/서버리스

- **BaaS(권장)**: Supabase(Postgres, Auth, Storage, Edge Functions)
    
- **서버리스 함수**: Vercel Functions/Edge Functions (API, Webhook)
    
- **스케줄러**: Vercel Cron(주간 일정·타이머 JSON 자동 갱신)
    
- **캐시**: Upstash Redis(일정/랭킹/빈번 조회 캐시)
    
- **검색(선택)**: Typesense/Algolia(콘텐츠 검색)
    

## 3) 데이터/콘텐츠

- **DB**: Postgres(Supabase) – RLS로 “내 데이터만 접근”
    
- **마이그레이션**: Supabase SQL Migrations / Prisma(선택)
    
- **콘텐츠 소스**: MDX + Contentlayer(가이드), Sanity/Notion CMS(운영 편의)
    

## 4) 인증/보안

- **인증**: Supabase Auth(이메일/소셜), WebAuthn(선택)
    
- **세션**: HttpOnly+Secure+SameSite 쿠키, 세션 재발급
    
- **정책**: RLS(SELECT 공개/개인 테이블 분리), 관리자 역할 분리
    
- **레이트리미트/봇**: Upstash RateLimit + Turnstile(reCAPTCHA 대체)
    
- **보안 헤더**: CSP, X-Frame-Options/`frame-ancestors`, HSTS, Referrer-Policy
    
- **비밀 관리**: Vercel/Supabase Secrets, `.env` 깃 커밋 금지
    

## 5) 관측/운영

- **로깅**: Vercel Logs + Sentry(PII 마스킹)
    
- **모니터링**: Uptime Kuma/Better Stack(헬스체크)
    
- **분석**: Umami/Plausible(쿠키 최소), GA4(선택)
    
- **성능**: Lighthouse CI, Web Vitals 보고(Next 내장)
    

## 6) 알림/커뮤니티

- **메일**: Resend/Postmark(템플릿 기반)
    
- **푸시**: Web Push(서비스워커) 또는 OneSignal(간편)
    
- **웹훅**: Discord/Slack(패치 공지 릴레이)
    

## 7) 배포/인프라

- **배포**: Vercel(프리뷰/프로덕션), 도메인 연결, HTTPS 자동
    
- **이미지/CDN**: Vercel Image Optimization
    
- **대안(자가호스팅)**: Docker + Nginx + Certbot(무료 SSL) on Naver Cloud/AWS Lightsail
    

## 8) 테스트/QA

- **E2E**: Playwright(주요 유저 플로우)
    
- **Unit/컴포넌트**: Vitest + React Testing Library
    
- **스키마/타입 안전**: Zod(입출력), Drizzle/Prisma(선택)
    

## 9) SEO/성장

- **메타/OG**: `next-seo` + 동적 OG 이미지 라우트
    
- **사이트맵/로봇**: `next-sitemap`, `robots.txt`
    
- **내부 링크/연관글**: PV↑ 유도 컴포넌트
    
- **피드**: RSS/Atom(업데이트 구독)
    

## 10) 수익/정책

- **광고**: Google AdSense(반응형 광고 2~3개), 배치 A/B
    
- **제휴**: 쿠팡파트너스/네이버쇼핑
    
- **후원**: 토스/부트페이/BuyMeACoffee
    
- **정책문서**: 개인정보처리방침/이용약관/면책(팬사이트 고지)
    

---

## 대안: Spring Boot 기반 전통 스택(원하시면)

- **백엔드**: Spring Boot 3 + Java 21, Spring Security, JPA/Hibernate, QueryDSL
    
- **DB**: MySQL/PostgreSQL, Redis(캐시)
    
- **빌드/배포**: Gradle, Docker, Nginx, GitHub Actions, Naver Cloud/AWS Lightsail
    
- **프런트**: Next.js(동일) 또는 Thymeleaf(SSR)
    
- **모니터링**: Prometheus + Grafana, ELK/EFK
    
- **장점**: 세밀한 제어/확장 용이
    
- **단점**: 인프라/보안/운영 비용·시간 증가(1인에게 비추천)
    

---

## 최소 구성 체크리스트(실전)

-  Next.js + TypeScript + Tailwind + shadcn/ui
    
-  Supabase(Postgres/Auth/Storage) + RLS 정책 적용
    
-  Vercel(SSR/ISR) + Cron(주간 일정 자동화)
    
-  Upstash Redis(캐시/레이트리미트)
    
-  Sentry(오류) + Umami(분석)
    
-  CSP/보안 헤더 + HttpOnly 쿠키 세션
    
-  `next-sitemap`+`next-seo`(SEO) / AdSense 연결
    
-  MDX+Contentlayer(가이드 관리) 또는 Sanity/Notion CMS

---

# 2. 디렉터리 구조

lostark-info/
├─ app/
│  ├─ (public)/            # SEO용 공개 페이지 섹션(예: /about, /policy)
│  ├─ (features)/          # 기능 섹션(타이머, 체크리스트, 빌더 등)
│  │  ├─ schedule/         # 모험섬/카오스/유령선 일정
│  │  ├─ checklist/        # 주간 체크/개인화
│  │  └─ engravings/       # 각인/스탯 계산기
│  ├─ api/                 # Route Handlers(Serverless API)
│  │  ├─ cron/refresh     # Vercel Cron이 때리는 엔드포인트
│  │  └─ auth/            # 로그인(콜백 등) 필요한 경우
│  ├─ layout.tsx
│  └─ page.tsx
├─ components/
│  ├─ ui/                  # shadcn/ui 래핑
│  ├─ charts/              # 통계/차트 컴포넌트(선택)
│  └─ common/              # 헤더/푸터/광고슬롯/SEO 등
├─ lib/
│  ├─ supabase/server.ts   # 서버용 클라이언트(서비스키 X)
│  ├─ supabase/client.ts   # 클라이언트 anon
│  ├─ redis.ts             # Upstash Redis 연결
│  ├─ auth.ts              # 세션/쿠키 헬퍼
│  ├─ rate-limit.ts        # 레이트리미트 미들웨어
│  ├─ csp.ts               # CSP/보안 헤더 생성
│  └─ seo.ts               # next-seo/OG 생성 유틸
├─ content/                # MDX 가이드(섬의 마음 등)
│  └─ guides/…             # MDX 파일 모음
├─ styles/ (globals.css, tailwind.css)
├─ public/ (favicon, og.png, robots.txt, ads.txt, sitemap.xml)
├─ scripts/                # 배치/마이그/데이터 변환
├─ prisma/ or migrations/  # (선택) DB 스키마 관리
├─ .env.example
├─ next.config.mjs
├─ package.json
└─ vercel.json

---





