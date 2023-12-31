---
title: HandlerMethod

date: 2023-11-23 19:00:00 +0900
categories: [🌼Spring, Spring MVC]
tags: [ Controller, HandlerMethod]
math: true
mermaid: true

---
## **핸들러 메서드(Handler Method)는**

웹 애플리케이션에서 <span style = 'background-color: #E6E6FA'>클라이언트의 요청을 처리하고 응답을 생성하는 역할을 하는 메서드입니다</span>

스프링 프레임워크의 컨트롤러(Controller) 클래스 내에 정의되며, 

클라이언트의 요청을 해당 메서드가 처리하여 원하는 결과를 반환합니다.

핸들러 메서드는 <span style = 'background-color: #E6E6FA'>주로 HTTP 요청을 처리하는 데 사용되며, </span>

다양한 애노테이션을 이용하여 특정 요청 경로, HTTP 메소드, 요청 파라미터 등을 지정할 수 있음

 스프링 프레임워크에서는 여러 애노테이션을 사용하여 핸들러 메서드를 정의할 수 있습니다.


<hr>

### **@RequestMapping**

<span style = 'background-color: #E6E6FA'>요청 경로와 메소드에 대한 매핑을 지정합니다.</span> 주로 클래스 레벨과 메서드 레벨에서 사용됩니다.

### **@GetMapping, @PostMapping, @PutMapping, @DeleteMapping**

각각 <span style = 'background-color: #E6E6FA'>HTTP GET, POST, PUT, DELETE 메소드에 대한 매핑</span>을 간편하게 지정합니다.

### **@PathVariable**

<span style = 'background-color: #E6E6FA'> URL 경로의 일부를 변수로 받아들입니다.</span>

 예를 들어, **`/users/{id}`**와 같은 URL 경로에서 **`{id}`** 부분을 매개변수로 받을 수 있습니다.

### **@RequestParam**

<span style = 'background-color: #E6E6FA'>요청 파라미터를 매개변수로 받아들입니다. </span>

쿼리 스트링이나 폼 데이터로 전달된 파라미터를 처리할 수 있습니다.

### **@RequestBody**

요청 <span style = 'background-color: #E6E6FA'>본문의 내용을 매개변수로 받아들입니다.</span>

JSON이나 XML과 같은 형식으로 전달된 데이터를 객체로 변환할 수 있습니다.

### **@ResponseBody**

핸들러 메서드의 <span style = 'background-color: #E6E6FA'>반환 값을 HTTP 응답의 본문으로 사용합니다. </span>

객체를 JSON이나 XML 등으로 변환하여 클라이언트에게 반환할 수 있습니다.

위와 같은 애노테이션을 조합하여 핸들러 메서드를 작성하면, 

웹 애플리케이션에서 클라이언트의 요청을 처리하고 응답을 생성하는 로직을 구현할 수 있습니다. 

핸들러 메서드를 통해 비즈니스 로직을 실행하고, 

데이터를 조회하거나 수정하는 등의 작업을 수행할 수 있습니다.

