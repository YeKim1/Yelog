---
title: "[Docker+Nginx] Springboot 프로젝트 로드밸런싱 구현"
date: 2023-08-28 16:00:00
update: 2023-08-28 16:00:00
tags:
  - spring
  - docker
  - loadbalancer
series: "효율적인 LoadBalancing 구현 수난기"
---

## 개요

[Docker로 Spring Boot 배포하기](https://yelog.site/docker/jar) 

Docker로 jar 서버 하나를 배포하는 방법을 익혔으니, 이제 여러 서버를 배포해서 로드밸런싱을 구현해보자

## Docker Volume?

Container를 run한 이후에 쌓이는 데이터는 Container를 삭제하면 함께 삭제된다

이를 방지하기 위해, Container의 외부의 디렉토리(or 파일)를 컨테이너와 연결해서 그 장소에 추가 데이터를 매핑할 수 있다

그 외에도 **데이터를 여러 서버에서 공유하고 싶을 때** 사용할 수 있다

```docker volume create [이름]``` 으로 볼륨을 생성하고 

런할 때 ```docker run -v [볼륨 이름]:[경로]``` 처럼 -v 옵션을 덧붙여서 볼륨과 경로를 마운트(동기화)할 수 있다

nginx 컨테이너를 생성하고 그 컨테이너의 볼륨에 jar 파일을 업로드해서 구현해보자!

## Nginx Container 구현



