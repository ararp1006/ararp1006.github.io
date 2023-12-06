---
title: Spring Data JPA

date: 2023-12-03 23:00:00 +0900
categories: [Study, JPA]
tags: [Study, JPA]
math: true
mermaid: true

---

[JPA 공식문서](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)

![image](https://github.com/ararp1006/Algorithm/assets/130068083/69e2f433-6400-4d7d-9f2e-5225c1f86cbb)

- **JPA는 기술 명세**
    
    자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 **인터페이스**이다
    
- **Hibernate는 JPA의 구현체**
    
    JPA와 Hibernate는 마치 자바의 interface와 해당 interface를 구현한 class와 같은 관계이다
    
- **Spring Data JPA는 JPA를 쓰기 편하게 만들어놓은 모듈**
    
    Spring에서 제공하는 모듈 중 하나로,
    
    개발자가 JPA를 더 쉽고 편하게 사용할 수 있도록 도와준다. 
    
     **JPA를 한 단계 추상화시킨 `Repository`라는 인터페이스를 제공해준다.**
    

JPA(Java Persistence API)는 자바에서 데이터베이스와 상호 작용하는데 사용되는 자바 API임

**Java Persistence API**의 약자이지만 현재는 **Jakarta Persistence**라고도 불림

JPA는 객체 관계 매핑(ORM, Object-Relational Mapping) 기술의 일종으로, 

객체 지향 프로그래밍과 관계형 데이터베이스 간의 불일치를 해결하기 위해 설계됨

JPA를 사용하면 자바 객체를 데이터베이스 테이블에 매핑하고,

객체 간의 관계를 관리하며, 데이터베이스에서 데이터를 검색, 저장, 업데이트, 삭제할 수 있음

### **<span style = 'background-color: #E6E6FA'>영속성 컨텍스트(Persistence Context)</span>**

JPA에서는 테이블과 매핑되는 엔티티 객체 정보를 

**영속성 컨텍스트(Persistence Context)라는 곳에 보관**해서

애플리케이션 내에서 오래 지속되도록 함

이렇게 보관된 엔티티 정보는 데이터베이스 테이블에 데이터를 저장, 수정, 조회, 삭제하는 데 사용

### 의존성 추가

`implementation 'org.springframework.boot:spring-boot-starter-data-jpa'` 

### application.yml 추가
```java
 jpa:
    hibernate:
      ddl-auto: create  # (1) 스키마 자동 생성
    show-sql:true# (2) SQL 쿼리 출력

```



### **<span style = 'background-color: #E6E6FA'>엔티티(Entities)</span>**

JPA에서는 데이터베이스의 테이블과 매핑되는 자바 클래스를 엔티티라고 함

각 엔티티는 데이터베이스 레코드의 인스턴스와 대응 됨


> [@Entity]

> @Builder


### **<span style = 'background-color: #E6E6FA'>엔티티 매핑(Entity Mapping)</span>**

JPA에서는 어노테이션을 사용하여 자바 엔티티 클래스와 데이터베이스 스키마 간의 매핑을 정의

예를 들어, @Entity 어노테이션은 자바 클래스를 엔티티로 지정하고, 

@Table 어노테이션은 해당 엔티티가 매핑될 데이터베이스 테이블을 지정

> [Mapping이란?]


### **<span style = 'background-color: #E6E6FA'>관계 매핑(Relationship Mapping)</span>**

객체와 관계형 데이터베이스 테이블이 어떻게 매핑되는가

[Hibernate 문서](https://docs.jboss.org/hibernate/orm/5.6/userguide/html_single/Hibernate_User_Guide.html#associations)