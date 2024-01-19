---
layout: single
title: "Start Spring IO"
categories: Spring
tag: [Dev, Spring, Java]
author_profile: false
---

## 프로젝트 생성

[스프링 부트 스타터](https://start.spring.io/).  

사이트에서 스프링 부트 프로젝트를 생성할 수 있다.  

스프링 버전이 2.x라면 자바 11, 스프링 버전이 3.x라면 자바 17을 사용해야 오류가 발생하지 않는다.   

또한 스프링 부트의 버전의 경우 뒤에 SNAPSHOT이나 M2가 붙은 버전은 아직 안정적인 버전이 아니므로 안정적인 버전 중에 가장 최신 버전을 이용하면 된다.  

![spring_initializer.png](/images/2024-01-17-스프링_이니셜라이져/spring_initializer.png)

## 설정

인텔리제이에서 settings에 들어간 후, 검색창에 Gradle이라 검색하면 `Build and run using`과 `Run tests using`이 Gradle로 되어 있다. 이것을 모두 IntelliJ IDEA로 바꾸면 인텔리제이에서 빌드와 실행을 하는데 속도가 향상된다.