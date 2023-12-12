---
title: SpringMVC

date: 2023-12-01 23:00:00 +0900
categories: [Spring, Spring MVC]
tags: [Study, Spring MVC]
math: true
mermaid: true

---
## **Spring MVC**

![image](https://github.com/ararp1006/Algorithm/assets/130068083/75517c72-8b81-4b75-927d-b77ab02f2a8f)

### Spring MVC란?

- **Model**
    
    어플리케이션이 무엇을 할 것인지 정의하는 부분입니다. 
    
    즉 DB와 연동하여 사용자가 입력한 데이터나 사용자에게 출력할 **데이터**를 다룸
    
- **View**
    
     사용자에게 시각적으로 보여주는 부분입니다. **(UI)**
    
- **Controller**
    
    Model이 데이터를 어떻게 처리할지 알려주는 역할을 합니다. 
    
    사용자에 의해 클라이언트가 보낸 데이터가 있으면 모델을 호출하기전에 적절히 가공을 하고 모델을 호출
    
    그런다음 모델이 업무 수행을 완료하면 그결과를 가지고 View에게 전달하는 역할을 합니다.
    

### MVC 패턴을 사용하는 이유

사용자가 보는 페이지, 데이터처리, 그리고 이 2가지를 중간에서 제어하는 컨트롤,

이 3가지로 구성되는 하나의 애플리케이션을 만들면 각각 맡은바에만 집중을 할 수 있게 됨

즉 서로 분리되어 각자의 역할에 집중할 수 있게끔하여 개발을 하고

그렇게 애플리케이션을 만든다면, 유지보수성, 애플리케이션의 확장성, 그리고 유연성이 증가하고, 

중복코딩이라는 문제점 또한 사라지는 효과를 가질수 있기 때문에 MVC 패턴을 사용합니다

![image](https://github.com/ararp1006/Algorithm/assets/130068083/a916d91a-c0aa-459c-acf7-078cd421021d)


> [Controller](https://ararp1006.github.io/posts/Controller/)

[^fn-nth-2]: The 2nd footnote source