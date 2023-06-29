---
title: "[Django] Swagger로 API 문서를 만들어 봅시다"
date: 2023-06-30 02:00:00
tags:
  - Django
series: "멋쟁이사자처럼 해커톤 가이드"
---

**글 내용에 질문이 있으면 언제든지 연락 주세요 (저 심심해요)**

## 개요

API를 개발하면 프론트엔드와 JSON으로 소통하게 됩니다

이 때.. 무슨 기능은 어떤 URL인지, Request에 어떤 key가 들어가는지, Response로는 무슨 key-value를 줄 것인지 프론트엔드에게 알려주어야 합니다

![](1.png)
(tmi)저는 사진처럼 엑셀에 작성해서 수기로 