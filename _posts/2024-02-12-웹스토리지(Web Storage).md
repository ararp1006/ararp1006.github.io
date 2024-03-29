---
title: 웹 스토리지(Web Stroage)
date: 2024-02-02 23:00:00 +0900
categories: [Study,Programming/Web ]
tags: [Study, Programming/Web ]
math: true
mermaid: true

---

## **웹 스토리지(Web Stroage)**

웹 스토리지 (web storage)는 서버가 아닌, 클라이언트에 데이터를 저장할 수 있도록 지원하는 HTML5의 새로운 기능입니다.

웹스토리지와 쿠키의 기능 자체는 유사하지만 쿠키는 약 4KB까지 저장할 수 있지만,

웹 스토리지는 모바일은 최대 2.5KB, 웹 브라우저는 최대 5KB까지 저장할 수 있습니다.

또, 쿠키와 다르게 네트워크 요청 시 서버로 저장이 되지 않습니다.

따라서 중요성이 낮거나 유실되어도 무방한 데이터를 저장하는 것이 권장합니다.

웹 스토리지의 값(value)은 오직 문자열(String) 데이터만 지원합니다.

이외의 타입은 String 타입을 파싱 하여서 JSON 혹은 number 타입으로 전환하여 사용해야합니다. 

웹 스토리지는 로컬 스토리지와 세션 스토리지가 있습니다.



![image](https://github.com/ararp1006/Algorithm/assets/130068083/62330abd-ad8d-43fe-a095-2567b2320d9c)


## **로컬 스토리지 (Local Storage)**

로컬 스토리지는 브라우저에 반영구적으로 데이터를 저장하며, 브라우저를 종료해도 데이터가 유지됩니다.

직접 로컬 스토리지를 초기화(clear)하거나 제거(removeItem)하지 않는다면 계속 유지됩니다.

하지만 도메인(domain)이 다르면 로컬 스토리지에 접근할 수 없습니다.




## **세션 스토리지(Session Storage)**

세션 스토리지는 각 세션마다 데이터가 개별적으로 저장됩니다.
 
브라우저에서 여러개의 탭을 실행하면 탭마다 개별적으로 데이터가 저장됩니다.

세션스토리지는 세션을 종료하면 데이터가 자동으로 제거 됩니다.

같은 도메인이라도 세션이 다르면 데이터에 접근할 수 없습니다.



## **메서드**

> setItem(key, value) : 	키(key)와 값(value)을 기반으로 저장합니다.

> getItem(key) : 	키(key) 값을 기반으로 값(value)을 불러옵니다.

> key(index) : 	인덱스(index) 값을 기반으로 값(value)을 불러옵니다.

> removeItem(key) :	키(key) 값을 기반으로 해당 로컬,세션 스토리지를 제거합니다.

> clear() : 로컬,세션 스토리지들을 초기화 합니다.

> length :	로컬,세션 스토리지에 저장된 데이터 개수를 반환 받습니다.