---
title: JDBC,SQLMapper,ORM
date: 2023-12-06 23:00:00 +0900
categories: [Study, DataBase]
tags: [DataBase]
math: true
mermaid: true

---
![image](https://github.com/ararp1006/mainProject/assets/130068083/13cdb420-3dca-4871-b2ae-f46d8be2d41e)


## **JDBC API**

![image](https://github.com/ararp1006/mainProject/assets/130068083/fbb165aa-11ee-49b6-9009-63f95ab88c4e)

인터넷 보급, DB 산업 성장을 하면서 등장했습니다.

Java 어플리케이션은 다양한 관계형 데이터베이스 시스템과 상호 작용할 수 있습니다.

**단점**

>  중복 코드가 많습니다.
>  Connection 관리를 계속 해줘야 합니다.


## **SQLMapper**

### **Spring JDBC**

![image](https://github.com/ararp1006/mainProject/assets/130068083/029b82f9-eece-4af9-8146-fd0b1448a76d)

 위치 기반이 아닌 이름 기반의 파라미터 사용을 허용합니다.

 JDBC 코드를 직접 작성하는 대신에 DAO 인터페이스를 정의하고 
 
 해당 인터페이스를 구현하여 데이터베이스 액세스를 추상화할 수 있습니다.

 Spring JDBC는 여러 가지 템플릿 클래스를 제공합니다.(JdbcTemplate)

 예외처리의 편의성, 트랜잭션관리과 편리합니다.

**단점**

> **SQL에 대한 의존성**:SQL 쿼리를 직접 작성하여 사용합니다. 이로 인해 데이터베이스 종속성이 생길 수 있으며,

> **데이터베이스 커넥션 관리**:데이터베이스 연결을 관리하기 위한 코드를 수동으로 작성해야 합니다. 

### **MyBatis**

![image](https://github.com/ararp1006/mainProject/assets/130068083/19620374-2d70-4729-b84e-b0ffdc16626e)

MyBatis는 SQL 쿼리와 자바 객체 간의 매핑을 XML 또는 어노테이션을 통해 설정합니다.

간단하고 직관적인 XML 파일을 사용하여 데이터베이스와 자바 객체 간의 매핑을 정의합니다.

동적 SQL을 지원하여 동적으로 SQL 쿼리를 생성할 수 있습니다.

**단점**

> **유지보수**: SQL이 분산되어있기 때문에 변경사항 발생 시 모든 SQL을 찾아 수정해야합니다.

> **자동화부족**: 객체와 데이터베이스 간의 매핑을 위해 XML 파일이나 어노테이션을 사용하기 때문에
    이는 자동화된 방식이 아니므로 개발자가 매핑을 직접 작성해야 합니다. 


## **ORM (Object-Relational Mapping)**

객체지향적으로 구현되어 있는 구조에서 관계형데이터베이스와 연결하는 것을 간편하게 하기 위해 등장한 기술입니다.

객체지향적인 코드로 인해 더 직관적이고 로직에 집중할 수 있도록 도와줍니다.

DBMS에 대한 종속성이 줄어듭니다.

재사용 및 유지보수의 편리성이 증가합니다.

**단점**

> **성능문제** : 대량의 데이터를 처리하기에는 적합하지 않습니다.

> **복잡성**: 객체 지향 모델을 지원하므로, 복잡한 SQL 쿼리를 작성하거나 성능을 최적화하는 작업이 어려울 수 있습니다. 


**JPA/Hibernate**

> ***JPA(Java Persistence API)***는 자바의 ORM 기술 표준으로 ***인터페이스의 모음***입니다.

> 이러한 JPA 표준 명세를 구현한 ***구현체가 바로 Hibernate***입니다.