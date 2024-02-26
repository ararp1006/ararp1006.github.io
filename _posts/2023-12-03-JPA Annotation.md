---
title: 'JPA Annotation'

date: 2023-12-03 23:00:00 +0900
categories: [JPA, JPA Basic]
tags: [JPA, Annotation]
math: true
mermaid: true

---
<hr>-----------------------------------------------

**<span style = 'background-color: #E6E6FA'>1.객체-테이블 매핑</span>**

- [`@Entity`](https://ararp1006.github.io/posts/@Entity/): 클래스를 엔티티(테이블)로 매핑합니다.(필수)
- `@Table`: 엔티티와 매핑될 테이블의 정보를 설정합니다.
- `@Column`: 필드를 열(컬럼)로 매핑하며, 열의 속성을 설정합니다.
- `@Id`: 엔티티의 기본 키(primary key) 필드를 지정합니다.(필수)
- `@GeneratedValue`: 기본 키의 값을 자동으로 생성하는 전략을 설정합니다.

**<span style = 'background-color: #E6E6FA'>2.객체-테이블 관계 매핑</span>**

- `@OneToOne`: 일대일 관계를 매핑합니다.
- `@OneToMany`: 일대다 관계를 매핑합니다.
- `@ManyToOne`: 다대일 관계를 매핑합니다.
- `@ManyToMany`: 다대다 관계를 매핑합니다.

**<span style = 'background-color: #E6E6FA'>3.객체-테이블 관계 매핑</span>**

- `@JoinColumn`: 조인 컬럼을 설정하고, 조인 컬럼의 속성을 설정합니다.
- `@JoinTable`: 다대다 관계에서 중간 테이블을 매핑하고, 조인 테이블의 속성을 설정합니다.
- `@MappedSuperclass`: 부모 클래스를 상속하는 자식 클래스의 매핑 정보를 공유합니다.

**<span style = 'background-color: #E6E6FA'>4.상속 관계 매핑</span>**

- `@Inheritance`: 상속 관계를 매핑합니다.
- `@DiscriminatorColumn`: 구분 컬럼을 설정하고, 구분 컬럼의 속성을 설정합니다.
- `@DiscriminatorValue`: 엔티티를 식별하는 값을 설정합니다.

**<span style = 'background-color: #E6E6FA'>5.열거형 매핑</span>**

- `@Enumerated`: 열(컬럼)에 대한 Enum 타입의 매핑을 설정합니다.


**<span style = 'background-color: #E6E6FA'>6.기타 매핑 매핑</span>**
- `@Transient`: 필드를 데이터베이스에 매핑하지 않음을 표시합니다.
- `@Temporal`: 날짜 및 시간 필드의 타입을 설정합니다.
- `@Lob`: 큰 데이터 객체(BLOB, CLOB)를 매핑합니다.
- `@Version`: 엔티티의 버전 관리를 위한 필드를 설정합니다.



