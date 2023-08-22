---
title: "Google Search Console Sitemap 가져올 수 없음 문제 해결"
date: 2023-07-25 23:00:00
update: 2023-07-25 23:00:00
tags:
  - Netlify
  - Gatsby
  - SEO
---

## 문제 상황

![](image.png)

Gatsby 블로그를 구글 서치 콘솔에 등록하는 과정에서, 위 사진처럼 Sitemap이 정상적으로 등록되지 않았다

서치해서 여러 자료를 찾아보고 모두 적용해보았으나 해결이 되지 않았다 ㅜㅜ

따라해 본 방법들은 아래와 같다(=**삽질 과정**)

1. /sitemap.xml을 삭제하고 //sitemap.xml 또는 /sitemap.xml/로 재동륵하기

: //sitemap.xml은 /sitemap.xml과 동일하게 변경되어 등록되어 의미 없는 것 같았으며 /sitemap.xml/은 올바른 xml 링크가 아니었다

2. /sitemap.xml 링크 색인 생성 요청

![](image-1.png)

: sitemap.xml 자체가 링크에 검색될 뿐 안의 내용이 sitemap으로 등록되는 로직은 아닌 것 같았으며 등록한 이후로 제출된 사이트맵에 변동이 없었다

3. 기다리기

: sitemap 처리가 오래 걸리고 길게는 세 달이 걸려서 성공된 사례도 있다고 보았다





