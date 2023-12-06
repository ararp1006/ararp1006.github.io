---
title: '@Controller vs@RestController'

date: 2023-12-01 23:00:00 +0900
categories: [Study, Spring MVC]
tags: [Study, Controller]
math: true
mermaid: true

---
##  **@Controller vs @RestController**

@Controller와 @RestController는 Spring Framework에서 사용되는 두 가지 주요 애노테이션이다.

이 두 애노테이션은 웹 애플리케이션에서 엔드포인트를 정의하는 데 사용되며, 각각의 목적과 특징이 다르다.

### **@Controller**

@Controller는 HTML 뷰를 반환하는 데 주로 사용된다.

주로 브라우저와 같은 웹 클라이언트에게 데이터를 보내는 용도로 사용됨

예를 들어, 사용자에게 HTML 페이지를 제공하거나, 뷰와 모델을 결합하여 HTML을 생성하는 등의 작업에 사용된다

기본적으로는 @ResponseBody가 없는 메서드는 View Resolver를 통해 뷰로의 렌더링을 시도한다고 한다.

```java
@Controller
public class MyController {

    @RequestMapping("/hello")
    public String hello() {
        return "hello"; // View 이름으로 인식하여 뷰를 렌더링
    }
}
```
### **@RestController**

@RestController는 주로 RESTful 웹 서비스를 제공하는 데 사용된다.

@RestController가 적용된 클래스의 모든 메서드는 @ResponseBody가 적용된 것으로 간주됨

주로 JSON 또는 XML 형식의 데이터를 반환한다.

데이터를 직렬화하여 클라이언트에게 전달하고, 주로 AJAX 요청에 대한 응답으로 사용된다.

```java
@RestController
public class MyRestController {

    @RequestMapping("/api/hello")
    public String hello() {
        return "Hello, REST!"; // 문자열 그 자체가 응답으로 전송됨
    }
}
```

따라서, RESTful API를 제공해야 한다면 @RestController를 사용하는 것이 좋다!

