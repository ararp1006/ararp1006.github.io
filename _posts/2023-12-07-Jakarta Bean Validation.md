---
title: Jakarta Bean Validation
date: 2023-12-07 23:00:00 +0900
categories: [🌼Spring,Annotation]
tags: [Annotation ]
math: true
mermaid: true

---


**Jakarta Bean Validation**이라는 유효성 검증을 위한 표준 스펙에서 지원하는 내장 애너테이션들임

**Jakarta Bean Validation**은 여러분들이 라이브러리처럼 사용할 수 있는 API가 아닌

스펙(사양, Specification) 자체

즉, 이러이러한 애너테이션들을 이런 식으로 구현해서 사용하라는 일종의 기능 명세를 의미합니다.

따라서 **Jakarta Bean Validation** 스펙을 구현한 구현체가 존재

이 **Jakarta Bean Validation** 스펙을 구현한 구현체가 바로 **Hibernate Validator임**

Java Bean 스펙을 준수하는 Java 클래스라면 

**Jakarta Bean Validation**의 애너테이션을 사용해서 유효성 검증을 할 수 있음
