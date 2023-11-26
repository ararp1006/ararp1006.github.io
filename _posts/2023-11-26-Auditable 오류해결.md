---
title: Auditable 오류 해결

date: 2023-11-23 19:00:00 +0900
categories: [Blogging, Demo]
tags: [Project]
math: true
mermaid: true

---

멘토님에게 작성날짜, 수정날짜칼럼이 모든 테이블에 들어 가도록 만들면 좋겠다는 피드백을 받았다.

이미 DB설계를 마친 상황에서 모든 테이블에 하나씩 추가를 하는 것은 비효울적이라고 생각이 들어서

BaseEntity를 만들고 다른 Entity에서 상속 받는 것으로 문제를 해결하는 의견을 내었다.

다행히 팀원분들이 동의를 해주어서 검색을 해가며 

<details>
<summary>Auditable❓</summary>
<div markdown="1">
Audit은 사전적 의미로 **감사하다, 심사하다** 등의 의미를 가지고 있다.

Spring Data JPA에서는 Auditing이라는 기능을 제공한다.

이를 사용하여 엔티티가 생성되고, 변경되는 그 시점을 감지하여

 생성시각, 수정시각, 생성한 사람, 수정한 사람을 기록할 수 있다.

특히 서비스를 운영할 때 데이터가 생성되고, 수정한 일자를 기록하고 트래킹하는 것은 중요하다.
</div>
</details>
을 만들었는데 문제가 발생했다.

```java
@Getter
@Setter
@MappedSuperclass
@EntityListeners(AuditingEntityListener.class)
public abstract class Auditable {
    @CreatedDate
    @Column(name = "created_at", updatable = false)
    private LocalDateTime createdAt;

    @LastModifiedDate
    @Column(name = "Last_modified_at")
    private LocalDateTime modifiedAt;
}
```

## 문제발생

 created_at이랑 updated_at에 null값이 들어갔다

![image](https://github.com/ararp1006/Algorithm/assets/130068083/0d8dbc57-6fc3-49e8-9d01-b52eb229a54d)

## 문제해결

다른 사람들은 baseEntity를  어떻게 했는지 검색해보고 찾아봤는데 내 코드랑 똑같은 것 같았다.

그러다가  사람마다  Auditable이라 쓰기도 하고  baseEntity 라고 쓰기도 하는 것을 볼 수 있었다.

왜 명칭이 다른가??라고 궁금해서 검색을 하다 보니

JPA에서 제공하는 **Auditing**이라는 기능을 제공해주는 것을 알게되었다.

간단하게  사용한 JPA Auditing 애노테이션에 대해서 설명해보자면 (자세한건 JPA에서)

| @MappedSuperclass | JPA Entity 클래스들이 해당 추상 클래스를 상속할 경우 createDate, modifiedDate를 컬럼으로 인식 |
| --- | --- |
| @EntityListeners(AuditingEntityListener.class | 해당 클래스에 Auditing 기능을 포함 |
| @EnableJpaAuditing | 스프링 부트의 Entry 포인트인 실행 클래스에 어노테이션을 적용하여 JPA Auditing을 활성화 |

```java
@SpringBootApplication
@EnableJpaAuditing
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

이렇게 수정을 하였더니 null값이 아니라 잘 들어가게 되었다.

## 깨달은점

그냥 구글링해서 따라 친 코드를 아무 생각 없이 사용하다보니 이런 오류가 발생했다고 생각이 들었다.

하나의 어노테이션이 어떤 기능을 하는지 이게 왜 사용되는지 생각을 하면서 사용을 하고

구글링 보다 공식문서를 참조하는 것이 기능을 더 정확히 이해할 수 있을 것 같다.

기능을 구현하려면 기능이 어떤 구조로 어떻게 구현되는지 이해하는게 중요하다고 생각이 들었다.





