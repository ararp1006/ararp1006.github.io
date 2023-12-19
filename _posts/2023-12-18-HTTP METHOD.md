---
title: HTTP METHOD

date: 2023-12-18 19:00:00 +0900
categories: [Study,Programming/Web]
tags: [Programming/Web]
math: true
mermaid: true

---



**HTTP (Hypertext Transfer Protocol)**는 웹에서 데이터를 전송하는 데 사용되는 프로토콜로,

**클라이언트와 서버 간의 통신**을 담당합니다. 

HTTP 메서드는 **클라이언트가 서버에게 요청을 어떻게 처리해야 하는지**를 나타내는데,

각각의 메서드는 특정한 동작을 수행합니다. 

<hr>

**GET**

<span style = 'background-color: #E6E6FA'>서버에서 특정 리소스(웹 페이지, 이미지, 텍스트 등)를 가져오도록 요청합니다.</span>

요청한 리소스는 URL에 포함되어 전송됩니다.

서버에 전달하고 싶은 데이터는 쿼리스트링를 통해서 전달

예) 정적데이터 조회 `GET/members/100?username=1`

  동적 데이터 조회 `https://www.google.co.kr/?hl=ko`

조회할 때 POST도 사용할 수 있지만, GET 메서드는 캐싱이 가능하기에 GET을 사용하는 것이 유리합니다.


**POST**

<span style = 'background-color: #E6E6FA'>서버에 데이터를 제출하고, 전달된 데이터로 주로 신규 리소스 등록, 프로세스 처리에 사용</span>

주로 폼 데이터를 서버로 제출할 때 사용되며, 데이터는 HTTP 요청 본문에 포함됩니다.

만일 데이터를 GET 하는데 있어, JSON으로 조회 데이터를 넘겨야 하는 애매한 경우 POST를 사용합니다.

예시) 

``` json

POST /submit-form HTTP/1.1
Content-Type: application/x-www-form-urlencoded

username=johndoe&password=secretpassword
```


**PUT**

<span style = 'background-color: #E6E6FA'>서버에 새로운 리소스를 생성하거나 기존 리소스를 업데이트하도록 요청합니다.</span>

요청 본문에 업데이트하려는 데이터를 포함합니다.

요청 메세지에 리소스가 있으면 덮어쓰고, 없으면 새로 생성합니다.

데이터를 대체해야 하니, 클라이언트가 리소스의 구체적인 전체 경로를 지정해 보내주어야 합니다.

예시) 

``` json
PUT /update-user/123 HTTP/1.1
Content-Type: application/json

{
  "username": "newusername",
  "password": "newpassword"
}
```


**PATCH**

<span style = 'background-color: #E6E6FA'>리소스의 일부를 업데이트하도록 요청합니다. </span>

일부 업데이트는 전체 리소스를 업데이트하는 것보다 효율적일 때 사용됩니다.

PATCH를 지원하지 않는 서버에서는 대신에 POST를 사용할 수 있습니다.

예시) 

``` json
PATCH /update-user/123 HTTP/1.1
Content-Type: application/json

{
  "username": "newusername",
}
```
**DELETE**

서버에서 특정 리소스를 삭제하도록 요청합니다.

요청 본문에 삭제 대상이 되는 리소스에 대한 정보를 포함할 수 있습니다.

예시) 

``` json
DELETE /update-user/123 HTTP/1.1
HOST: excample.com
Content-Type: application/json
```

<hr>

**HEAD**

GET 메서드와 유사하지만, 실제 데이터를 반환하지 않고 헤더만을 반환합니다.

응답의 상태 코드만 확인할때와 같이 Resource를 받지 않고 오직 찾기만 원할때 사용가능합니다.

(일종의 검사 용도)

서버의 응답 헤더를 봄으로써 Resource가 수정 되었는지 확인 가능

주로 리소스의 메타데이터를 확인할 때 사용됩니다.

**OPTIONS**

서버에서 지원되는 메서드나 리소스에 대한 옵션을 확인하기 위해 사용됩니다.

서버의 지원 가능한 HTTP 메서드와 출처를 응답 받아 CORS 정책을 검사하기 위한 요청입니다.

**TRACE**

클라이언트가 보낸 요청 메시지를 서버까지 추적하도록 요청합니다. 

주로 디버깅 목적으로 사용되며, 보안 이슈로 인해 일반적으로 비활성화되어 있습니다

