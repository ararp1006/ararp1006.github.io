---
title: 지연로딩(Lazy Loading)
date: 2024-02-26 23:00:00 +0900
categories: [JPA, QueryDSL]
tags: [JAVA]
math: true
mermaid: true

---

## **즉시로딩(Eager Loading)이란?**

![image](https://github.com/ararp1006/mainProject/assets/130068083/d1abc089-e630-4d9b-9afa-0a0261e57a57)


특정 엔티티를 조회할 때 연관된 모든 엔티티를 같이 로딩하는 것을 **즉시 로딩(Eager Loading)**이라고 합니다.

이와 같은 즉시 로딩은 **연관된 엔티티를 모두 가져온다는 장점**이 있지만,

실무에서 엔티티간의 관계가 복잡해질수록 조인으로 인한 **성능 저하를 피할 수 없게 됩니다**.




## **지연로딩(Lazy Loading)이란?**


**JPA**는 성능 최적화를 위해, 연관된 엔티티는 **가짜 객체(프록시,Proxy)**로 만들어 

실제 엔티티 객체 생성을 지연시킵니다. 이를 **지연 로딩(Lazy Loading)**이라 부른다. 


만약  B엔티티가 A엔티티와 밀접한 연관이 있다면 지연로딩을 구사할 이유가 없습니다. 

바로 실제 엔티티를 로드해야합니다. 이를 위해, JPA는 **즉시로딩(Eager Loading)**도 가능합니다.

하지만 즉시로딩은 추천하지 않습니다.


![image](https://github.com/ararp1006/mainProject/assets/130068083/97cf18e3-0786-4dbc-a1b6-6cd97af8a024)

즉, 지연로딩은 실제로 Member를 통해 Team에 대한 정보를 읽어와야할 때까지 DB에서 조회를 미루게 됩니다.

Member를 조회 할때 Team객체에 프록시 객체를 넣어오고, getTeam 처럼 실제로 team을 호출해야할 때 초기화가 이루어집니다.


---------------------------------------------

각 연관관계의 default 속성은 다음과 같습니다.

@ManyToOne : EAGER

@OneToOne : EAGER

@ManyToMany : LAZY

@OneToMany : LAZY

============================================================================

## **즉시 로딩(Eager Loading)과 지연 로딩(Lazy Loading)의 장단점**

**즉시 로딩(Earge Loading) 장점**

>지연된 초기화와 관련해서 성능적인 영향이 없음

**즉시 로딩(Earge Loading) 단점**

>지연 로딩보다 긴 초기의 로딩 시간이 필요함

>불필요한 데이터를 많이 로딩하면 성능에 영향을 줄 수 있음
 

**지연 로딩(Lazy Loading) 장점**

>다른 접근 방식보다 훨씬 적은 초기의 로딩 시간

>다른 접근 방식에 비해 메모리 소비량 감소

**지연 로딩(Lazy Loading) 단점**

>초기화가 지연되면 원하지 않는 순간 성능에 영향을 줄 수 있음