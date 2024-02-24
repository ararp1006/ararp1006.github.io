---
title: String,StringBuilder,StringBuffer
date: 2024-02-17 23:00:00 +0900
categories: [JAVA, Java의 특징]
tags: [JAVA]
math: true
mermaid: true

---
## **String과 StringBuilder,StringBuffer의 차이점**

Java에서 String 객체는 한번 값이 할당되면 그 공간은 변하지 않습니다. 

할당된 공간이 변하지 않는 특성을 불변(Immutable)성이라고 하고,

할당된 공간이 변하는 특성을 가변(mutable)성이라고 합니다.

**String**

불변성을 갖는다. → Immutable 하다.

**StringBuilder, StringBuffer**

가변성을 갖는다. → mutable 하다.

따라서 값이 달라지면 String의 **객체주소가 다르고**,

StringBuilder, StringBuffer의 **객체주소는 같습니다**.

## ** StringBuilder VS StringBuffer**

두 클래스의 기능은 같지만 **동기화(Synchronization)**에서의 차이점이 있습니다.

**StringBuilder**는 동기화를 지원하지 않는 반면,

**StringBuffer**는 동기화를 지원하여 멀티 스레드 환경에서도 안전하게 동작할 수 있습니다.

왜냐하면 StringBuffer는 메서드에서 **synchronized 키워드**를 사용하기 때문입니다.

java에서 **synchronized** 키워드는 여러개의 스레드가 한 개의 자원에 접근할려고 할 때, 

현재 데이터를 사용하고 있는 스레드를 제외하고 **나머지 스레드들이 데이터에 접근할 수 없도록 막는 역할을 수행**합니다.


===================================================

String은 불변성을 갖기 때문에 

변하지 않는 문자열을 자주 사용할 경우 String 타입을 사용하는 것이 성능면에서 유리합니다.

StringBuilder는 동기화를 지원하지 않는 반면, 속도면에선 StringBuffer 보다 성능이 좋기 때문에,

단일 스레드 환경 과 문자열의 추가, 수정, 삭제 등이 빈번히 발생하는 경우 StringBuilder를 사용하는 것이 성능면에서 유리합니다.

StringBuffer는 동기화를 지원하여 멀티 스레드 환경에서도 안전하게 동작할 수 있기 때문에,

멀티 스레드 환경에서 사용하는 것이 성능면에서 유리합니다.

