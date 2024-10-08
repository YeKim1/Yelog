---
title: "왜 Spring이어야 할까?"
date: 2024-08-07 20:00:00
update: 2024-08-07 20:00:00
tags:
  - Spring
  - DI
  - AOP
---

## 서론

내 백엔드 첫 입문 언어는 Python의 Django 프레임워크였다.

그러나 백엔드 개발자로 취업 준비를 하며, Spring으로 프로젝트를 하며 공부를 진행했고 주력 프레임워크로 사용하게 되었다.

애정하는 언어인 C++로 코딩테스트를 준비하다가 Spring을 위해 Java로 언어를 바꾸기도 했다.

하지만 나는 **왜 Spring을 사용할까?** 라는 질문에, 그냥 한국의 대다수 기업이 사용하기 때문이라는 대답밖에 할 수 없었다. 

내 주력 프레임워크의 장단점조차 모른다는 점은 정말 치명적인 부분이다.

이번엔 한번 기초로 돌아가 Spring 자체를 공부하는 시간을 가져보자

## Spring이란?

![[공식 사이트](https://spring.io/)](image.png)

쉽게 말해 Java의 웹 프레임워크로, Java 언어를 사용해 어플리케이션을 쉽게 개발할 수 있도록 돕는 도구이다.

공식 사이트에서의 설명에 따르면 스프링은 더 빠르고 쉽게, 안전하게 자바 프로그래밍을 할 수 있도록 도우며 세계에서 가장 인기있는 자바 프레임워크라고 한다.

스프링의 주요 기능에 대해 알아보자

### IOC (Inversion of Control)

제어 역전이다. 이는 객체를 개발자가 직접 생성하는 것이 아닌, ```외부의 스프링 컨테이너에게 위임하는``` 것이다.

객체의 생성부터 소멸까지 생성주기 관리의 제어권은 스프링에게 있다.

객체 관리는 프레임워크인 스프링에게 맡기고 개발자는 온전히 로직에 집중하여 개발의 효율성을 높일 수 있는 방법이다.

이렇게 스프링이 관리하게 된 객체를 ```Bean```이라고 칭한다. 객체가 의존관계를 정의하는 과정에서 개발자의 역할은 없고 스프링이 컨테이너에서 해당하는 Bean을 찾아 의존성을 만든다. 

### DI (Dependency Injection)

의존성 주입이라고도 하는 DI. 위의 IOC를 구현하는 패턴 중 하나이다.

> 💡 **Dependency(의존성)**은 객체 지향 프로그래밍에서 클래스나 모듈 간의 관계를 의미한다. <br>
컴퓨터 객체를 하나 생성한다고 가정하자. new Computer()를 하면 Computer 객체를 만드는 과정에서 new CPU()가 실행될 것이다. 이러한 관계를 Computer가 CPU에 의존한다고 한다.

따라서 의존성 주입이란 ```의존하는 객체를 내부에서 직접 생성하는게 아니라 외부에서 주입받는 것```을 의미한다.

위의 예시에서 Computer 클래스 안에 CPU를 생성하고 변경하는 코드가 있는 것이 아니라, CPU라는 외부의 클래스에서 생성한 것을 사용하는 것이다.

**왜 그래야 할까?**

```결합도```가 낮아진다. 결합도란 모듈 간 상호 의존하는 정도나 모듈 사이의 연관 관계를 의미한다.

결합도가 낮을 수록 모듈의 독립성이 높아지며 유연성과 재사용성이 높아진다.

Computer는 CPU라는 부품에 대한 것을 CPU 클래스에게 위임하며 하나의 기능에 집중할 수 있게 된다.

또, CPU라는 부품에 변동사항이 생겼을 경우, Computer는 그러한 변동사항에 영향을 받지 않고 그저 정해진 메서드를 호출하여 본래의 기능을 그대로 작동할 수 있게 된다.

주로 생성자를 통해 의존성을 주입해주는 방식이 사용된다.

### AOP (Aspect Object Programming)

관점 지향 프로그래밍이라고 한다.

이는 여러 모듈에서 공통적으로 사용하는 기능을 분리하여 ```재사용성```을 높이는 방법이다.

게시판을 구현할 때, 게시글 조회나 업로드, 검색 등 여러 기능에서 사전에 로그인 여부를 확인해야 한다고 가정하자.

모든 기능 코드의 초입에 로그인 여부를 확인하는 코드를 넣을 것인가?

이런 방식으로 구현하면 중복 코드가 발생하여, 추후 로그인 여부를 확인하는 코드가 수정되면 하나하나 찾아서 수정해야 하는 대참사가 발생할 수 있다.

스프링에서는 클래스에 ```@Aspect```라는 애노테이션을 추가해 Aspect를 정의함으로써 이러한 중복코드를 제거할 수 있다.

### POJO (Plain Old Java Object)

특정 기술에 종속되지 않은, 객체 지향적 원리에 충실한 순수한 자바 객체를 의미한다.

이때 종속된다는 것은 어느 다른 프레임워크를 의존하거나 상속받는 것을 의미한다.

종속되지 않은 객체는 테스트가 용이하며 재활용하기 쉽다는 장점을 가지게 된다.

**이러한 네 가지의 핵심적인 특징 외에도, Spring 자체는 경량화된 프레임워크지만 아주 다양한 라이브러리를 지원하기 때문에 필요에 따라 추가/제거하며 개발해 나갈 수 있다는 장점이 있다.**

## 단점

1. **학습이 어렵다.** Django를 먼저 사용하고 Spring을 공부한 필자의 경험에 따르면, 사전 지식을 탑재해야 장점을 온전히 누릴 수 있다. 사전 지식이 없다면 그저 다른 프레임워크로 할 수 있는 작업을 굳이 어렵게 구현하는 것에 불과하게 된다.

2. **너무 방대하고 복잡하다.** 스프링 공식 사이트에도 명시되어 있듯이 스프링은 자바 최대 규모의 프레임워크다. 레퍼런스가 다양한 만큼, 그 라이브러리도 매우 방대하기 때문에 전부를 익히기 어렵다.

마찬가지로 이러한 기능을 사용하며 구현하기는 당연히 복잡하다.

**그러나 이러한 단점은 SpringBoot를 사용하면 어느정도 극복할 수 있다.**

## Spring과 SpringBoot의 차이점

지금까지 스프링에 대해 알아봤는데, 그러면 스프링부트는 뭘까?

스프링부트는 **스프링을 사용할 때 필요한 설정을 간편히 처리해주는 별도의 프레임워크**다.

1. 복잡한 초기 설정을 대신 해준다. 기존의 스프링은 XML을 통해 여러 기능을 설정해주어야 한다. 그러나 스프링부트를 사용하면 이러한 초기 설정을 자동으로 대신 해준다.

2. 버전 관리를 자동으로 해준다. build.gradle 파일의 dependency를 보면, 버전 입력없이 라이브러리만 명시하고 있다는 점을 알 수 있다. 이는 스프링부트가 자동으로 최신 버전으로 업그레이드하기 때문이다.

3. 웹 서버가 내장되어 있다. 스프링은 실행하기 위해 Tomcat 같은 외장 웹 서버를 설치하여 배포하는 과정을 거쳐야했다. 그러나 스프링부트에는 그러한 웹 서버가 내장되어 있기 때문에 빠르게 서버를 실행할 수 있다.

그 외에도 개발자가 개발에만 집중할 수 있도록 다양한 기능을 제공해준다!

## 번외. Django와의 차이점

Django는 파이썬 기반의 웹 프레임워크다.

내가 직접 쓰면서 느낀 장고의 장점은, 
**매우 빠르게 하나의 서버를 뚝딱 만들 수 있다**. Spring에 비해 복잡하지 않고 Python 문법이 더 익히기 쉽기 때문이다. 

또, **자체적으로 로그인과 RSS 기능, ORM**을 제공한다.

여담이지만 Spring으로 처음 넘어간 후 제일 당황했던 것이 로그인 구현이다.. 장고는 자체적으로 로그인과 유저 관리와 관련된 다양한 기능을 제공하지만 Spring은 오만바가지 코드를 작성해야 한다.

그러나 **이미 만들어져 있는 기능이 많아 커스텀마이징이 어렵다.** 또, 기능을 빨리 구현할 수 있는 만큼 **성능 이슈**가 존재한다고 한다.

최근 해외에서는 Django가 정말 인기가 많지만, 국내에서는 아직 Spring의 파이가 크기 때문에 Spring을 학습하는 개발자가 많은 것 같다.

## 후기

우선 공부하면서 작성한 글이기에 글에 유입되어 읽게 된 분이 계시다면 잘못된 부분을 보충해주시면 감사하겠습니다..

프로젝트를 할 때, 그냥 강의를 보면서 다짜고짜 코드를 작성하는 방식으로 스프링을 공부했다.

그래서 본능적으로 이건 아니다 싶은 로직 부분도 있었고 이해가 조금 부족했다.

그러나 본 글을 작성하면서 그 로직 부분도 어떻게 수정해야 할지 알겠고 내가 왜 그렇게 코드를 작성했는지 이해가 됐다.

이것이 아는 것의 중요함인가 보다.. 학습을 멈추지 말자!