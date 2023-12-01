---
title: Controller

date: 2023-12-02 01:00:00 +0900
categories: [Study, Spring MVC]
tags: [Study, Controller]
math: true
mermaid: true

---

Controller란?


Controller은 MVC에서 C에 해당 하며 주로 사용자의 요청을 처리 한 후 지정된 뷰에 모델 객체를 넘겨주는 역할

즉 사용자의 요청이 진입하는 지점이며 요청에 따라 어떤 처리를 할지 결정을 Service에 넘겨줌

[REST API](https://www.notion.so/RestAPI-233260dba97242e6a9d35dc72aeeb35a?pvs=21) 기반의 애플리케이션에서는 

컨트롤러를  애플리케이션이 제공해야 될 기능을 **리소스(Resource, 자원)**로 분류

## Controller가 필요한 이유

1. **사용자 요청 처리:** 
    
    웹 애플리케이션은 클라이언트로부터의 다양한 HTTP 요청을 받습니다. 이러한 요청을 처리하고 응답을 생성하는 것이 컨트롤러의 주된 역할입니다. 컨트롤러는 요청을 받아들이고 해당 요청에 따라 비즈니스 로직을 호출하거나 다른 작업을 수행하여 클라이언트에게 적절한 응답을 제공합니다.
    
2. **라우팅 및 URL 매핑:** 
    
    웹 애플리케이션에서는 URL을 통해 사용자 요청을 식별해야 합니다. 컨트롤러는 URL과 요청 핸들러 메서드 간의 매핑을 관리하고, 어떤 요청이 어떤 메서드로 라우팅되어야 하는지 결정합니다.
    
3. **비즈니스 로직 분리:** 
    
    컨트롤러는 비즈니스 로직을 분리하여 관리하는 데 도움을 줍니다. 비즈니스 로직은 주로 서비스 레이어에서 처리되며, 컨트롤러는 요청을 받아 비즈니스 로직을 호출하고 그 결과를 응답으로 반환합니다. 이로써 코드를 모듈화하고 유지 보수성을 향상시킵니다.
    
4. **뷰와 데이터 전송:** 
    
    컨트롤러는 데이터를 모델로 뷰로 전달하는 역할을 합니다. 모델은 사용자에게 보여줄 데이터를 나타내며, 뷰는 이 데이터를 템플릿과 함께 렌더링하여 클라이언트에게 응답으로 보냅니다. 컨트롤러는 모델을 채우고 적절한 뷰를 선택하여 뷰와 데이터를 결합합니다.
    
5. **HTTP 요청 및 응답 관리:** 
    
    컨트롤러는 HTTP 요청 및 응답을 처리하고 관리하는 역할을 합니다. 이는 사용자 인증, 세션 관리, 쿠키 처리 등과 관련된 작업을 수행할 수 있습니다.
    
6. **애플리케이션 계층 분리:**
    
     컨트롤러는 웹 애플리케이션을 다른 계층으로부터 분리하는 데 중요한 역할을 합니다. 일반적으로 웹 계층, 비즈니스 로직 계층, 데이터 액세스 계층으로 애플리케이션을 나누고, 컨트롤러는 웹 계층에서 요청을 받아서 비즈니스 로직 계층으로 전달하고 결과를 다시 웹 계층으로 반환합니다.
    
7. **테스트 용이성:** 
    
    컨트롤러는 테스트하기 쉬운 단위입니다. 단위 테스트 및 통합 테스트를 통해 컨트롤러의 동작을 검증하고 애플리케이션의 안정성을 확보하는 데 도움이 됩니다.


## ****Controller 구조****

[HandlerMethod](https://ararp1006.github.io/posts/HandlerMethod/)

### **컨트롤러 정의**

[@Controller vs @RestController](https://ararp1006.github.io/posts/2023-12-01-@Controller-vs-@RestController/)

### **메서드 매핑**

> [@RequestMapping]

> [@PostMapping]

> [@GetMapping]

> [@PutMapping]

> [@DeleteMapping]

### **매개변수**

[@RequestParam](https://www.notion.so/RequestParam-370ef7285ca742318843939083f4bd8d?pvs=21)

[@**PathVariable**](https://www.notion.so/PathVariable-86e5cfc437d5401993f8db03f37998f7?pvs=21)

[**@RequestBody**](https://www.notion.so/RequestBody-938c2ed1e94646d5862206c9dc94ef2e?pvs=21)

### **비즈니스 로직 처리**

### 반환

