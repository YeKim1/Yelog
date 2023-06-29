---
title: "[Django] Swagger로 API 문서를 만들어 봅시다"
date: 2023-06-30 03:00:00
update: 2023-06-30 03:00:00
tags:
  - Django
series: "멋쟁이사자처럼 해커톤 가이드"
---

**글 내용에 질문이 있으면 언제든지 연락 주세요 (저 심심해요)**

## 개요

API를 개발하면 프론트엔드와 JSON으로 소통하게 됩니다

이 때.. 무슨 기능은 어떤 URL인지, Request에 어떤 key가 들어가는지, Response로는 무슨 key-value를 줄 것인지 프론트엔드에게 알려주어야 합니다

![](1.png)
(tmi)저는 작년 해커톤 때 엑셀에 작성해서 수기로 줬는데 일단 제가 수동으로 수정해야 하기 때문에 매우매우 귀찮았습니다.........

![Alt text](image-2.png)
Swagger를 사용하면 API 문서를 자동으로 동기화할 수 있고 사이트 내에서 테스트도 가능합니다!


## 라이브러리 설치 및 세팅
```bash
pip install drf-yasg
```

./{project_name}/settings.py
```python
INSTALLED_APPS = [
    ...
    'drf_yasg',
    ...
]
```
Swagger 관련 라이브러리를 설치하고 settings.py의 INSTALLED_APPS에 추가합니다

## Swagger 페이지 url 설정
./{project_name}/urls.py
```
# Swagger 설정
from rest_framework.permissions import AllowAny
from drf_yasg.views import get_schema_view
from drf_yasg import openapi
```

```
schema_view = get_schema_view(
    openapi.Info(
        title = "Swagger 타이틀 작성",
        default_version = "v1",
        description = "Swagger를 사용한 API 문서입니다",
    ),
    public=True,
    permission_classes=(AllowAny,),
)
```
```
urlpatterns = [
    ...

    # Swagger url
    url(r'^swagger(?P<format>\.json|\.yaml)$', schema_view.without_ui(cache_timeout=0), name='schema-json'),
    url(r'^swagger/$', schema_view.with_ui('swagger', cache_timeout=0), name='schema-swagger-ui'),
    url(r'^redoc/$', schema_view.with_ui('redoc', cache_timeout=0), name='schema-redoc'),
]
```



