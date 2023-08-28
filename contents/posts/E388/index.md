---
title: "[vim] E388: Couldn't find definition 에러 해결"
date: 2023-08-23 15:00:00
update: 2023-08-23 15:00:00
tags:
  - vim
  - ubuntu
  - error
---

## 문제 상황

![](image.png)

```
E388: Couldn't find definition
```

vim insert 모드에서 방향키를 누르면 위와 같은 에러가 발생하면서 키보드 커서가 움직이지 않았다

## 해결 방법

```
vim ~/.vimrc
```

vim 설정 파일을 열어준다

```
:set term=builtin_ansi
```

이걸 추가하고 저장 후 닫아주면 정상적으로 커서가 작동한다