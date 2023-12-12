---
title: Spring Security

date: 2023-11-28 13:00:00 +0900
categories: [🌼Spring, Spring Security]
tags: [Spring,Cloud]
math: true
mermaid: true

---

# **❓ Spring Security란?**


![image](https://github.com/ararp1006/Algorithm/assets/130068083/40de1af1-ba47-4e8f-9f4d-4f3be707481a)

Spring MVC 기반 애플리케이션의 인증(Authentication)과 인가(Authorization or 권한 부여) 기능을 지원하는 보안 프레임워크입니다.

### **Spring Security로 할 수 있는 보안 강화 기능**

- 다양한 유형(**폼 로그인 인증**, **토큰 기반 인증**, **OAuth 2 기반 인증**, LDAP 인증)의 사용자 인증 기능 적용
- **애플리케이션 사용자의 역할(Role)에 따른 권한 레벨 적용**
- **애플리케이션에서 제공하는 리소스에 대한 접근 제어**
- **민감한 정보에 대한 데이터 암호화**
- SSL 적용
- 일반적으로 알려진 웹 보안 공격 차단

이 외에도 SSO, 클라이언트 인증서 기반 인증, 메서드 보안, 접근 제어 목록(Access Control List) 같은 보안을 위한 기능들을 지원합니다.

- **Authentication(인증)**
    - `Authentication`은 애플리케이션을 사용하는 사용자가 본인이 맞음을 증명하는 절차를 의미합니다.
    - `Authentication`을 정상적으로 수행하기 위해서는 사용자를 식별하기 위한 정보가 필요한데 이를
        
        `Credential`(신원 증명 정보)이라고 합니다.
        

- **Authorization(인가 또는 권한 부여)**
    - `Authorization`은 Authentication이 정상적으로 수행된 사용자에게 하나 이상의 권한(authority)
        
        을 부여하여 특정 애플리케이션의 특정 리소스에 접근할 수 있게 허가하는 과정을 의미합니다.
        
    - `Authorization`은 반드시 Authentication 과정 이후 수행되어야 하며 권한은 일반적으로
        
        역할(Role) 형태로 부여됩니다.



<details>
<summary> <span style="font-weight:bold"> [💊 보안이 적용된 웹 요청의 일반적인 처리 흐름] </span> </summary>
<div markdown="1">

![image](https://github.com/ararp1006/Algorithm/assets/130068083/abdf0084-9333-4b8e-abf5-fc00541e0d4b)
</div>
</details>


<details>
<summary><span style="font-weight:bold">웹 요청에서의 서블릿 필터와 필터 체인의 역할 </span></summary>
<div markdown="1">

![image](https://github.com/ararp1006/Algorithm/assets/130068083/4d916a44-ec72-45c6-935c-57b127cdc5b0)

서블릿 기반 애플리케이션의 경우, 애플리케이션의 엔드포인트에 요청이 도달하기 전에 중간에서 

요청을 가로챈 후 어떤 처리를 할 수 있는 적절한 포인트를 제공하는데 이것이 **서블릿 필터(Servlet Filter)입니다**

서블릿 필터는 자바에서 제공하는 API이며, javax.servlet 패키지에 인터페이스 형태로 정의되어 있습니다.

`javax.servlet.Filter` 인터페이스를 구현한 서블릿 필터는 

웹 요청(request)을 가로채어 어떤 처리(**전처리**)를 할 수 있으며, 또한 엔드포인트에서 요청 처리가 끝난 후 

전달되는 응답(reponse)을 클라이언트에게 전달하기 전에 어떤 처리(**후처리**)를 할 수 있습니다.

서블릿 필터는 하나 이상의 필터들을 연결해 **필터 체인(Filter Chain)**을 구성할 수 있습니다.

</div>
</details>

<details>
<summary><span style="font-weight:bold">[Spring Security에서의 필터 역할] </span></summary>
<div markdown="1">

![image](https://github.com/ararp1006/Algorithm/assets/130068083/0e53d3f5-7c8a-4b8f-9491-53cb205cd09d)

⭐ **DelegatingFilterProxy**

`DelegatingFilterProxy`는 보안과 관련된 어떤 작업을 처리하는 것이 아니라 

**서블릿 컨테이너 영역의 필터와 ApplicationContext에 Bean으로 등록된 필터들을 연결해 주는 브리지 역할**

⭐ **FilterChainProxy**

**Spring Security의 Filter Chain**은  **보안을 위한 작업을 처리하는 필터의 모음**입니다.

이 **Spring Security의 Filter를 사용하기 위한 진입점이 바로 `FilterChainProxy`입니다.**

**FilterChainProxy부**터 Spring Security에서 제공하는 보안 필터들이 필요한 작업을 수행합니다.

Spring Security의 Filter Chain은 **URL 별로 여러 개 등록**할 수 있으며,

Filter Chain이 있을 때 **어떤 Filter Chain을 사용할지는 FilterChainProxy가 결정**하며, 

가장 먼저 매칭된 Filter Chain을 실행합니다

</div>
</details>

<details>
<summary><span style="font-weight:bold"> [DelegatingPasswordEncoder]</span></summary>
<div markdown="1">

Spring Security에서 지원하는 `PasswordEncoder` **구현 객체를 생성해 주는 컴포넌트**로써 

DelegatingPasswordEncoder를 통해 애플리케이션에서 사용할 PasswordEncoder를 결정하고,

결정된 PasswordEncoder로 사용자가 입력한 패스워드를 **단방향으로 암호화해줍니다.**

```java

PasswordEncoder passwordEncoder = PasswordEncoderFactories.createDelegatingPasswordEncoder();
```

```java
//Custom DelegatingPasswordEncoder
String idForEncode = "bcrypt";
Map encoders = new HashMap<>();
encoders.put(idForEncode, new BCryptPasswordEncoder());
encoders.put("noop", NoOpPasswordEncoder.getInstance());
encoders.put("pbkdf2", new Pbkdf2PasswordEncoder());
encoders.put("scrypt", new SCryptPasswordEncoder());
encoders.put("sha256", new StandardPasswordEncoder());

PasswordEncoder passwordEncoder = new DelegatingPasswordEncoder(idForEncode, encoders);
```

- **DelegatingPasswordEncoder의 장점**

    - 사용하고자 하는 암호화 알고리즘을 특별히 지정하지 않는다면 Spring Security에서 권장하는
        
        최신 암호화 알고리즘을 사용하여 패스워드를 암호화할 수 있도록 해줍니다.
        
    - 패스워드 검증에 있어서 레거시 방식의 암호화 알고리즘으로 암호화된 패스워드의 검증을 지원합니다
    - 암호화 방식을 변경하고 싶다면 언제든지 암호화 방식을 변경할 수 있습니다
        - 단 이 경우, 기존에 암호화되어 저장된 패스워드에 대한 마이그레이션 작업이 먼저 진행
<details>
<summary>DelegatingPasswordEncoder의 장점</summary>
<div markdown="1">

**해시(Hash) 알고리즘** 

해시 알고리즘은 단방향 암호화를 위한 핵심 알고리즘입니다. 

단방향 암호화라는 용어에서도 그 특성이 잘 드러나듯이 한번 암호화되면 복호화되기 어려운 특성을 가지고 있습니다.

데이터베이스에 암호화되어 저장되는 패스워드 자체는 사용자가 입력한 패스워드와 비교해 올바른 패스워드

를 입력했는지 검증하는 용도이기 때문에 다시 복호화될 필요가 없습니다.

**MD5(Message Digest 5)** 

MD5는 초창기에 사용하던 MD2, MD4 해시 알고리즘의 결함을 보완한 알고리즘입니다. 

하지만 MD5 역시 단방향 알고리즘인데도 불구하고 복호화가 된 사례가 종종 발견되어 지금은 거의 사용하지 않는 알고리즘입니다.

MD5에서 **다이제스트(Digest)**는 원본 메시지를 암호화한 메시지를 의미합니다

**SHA(Secure Hash Algorithm)** 

MD5의 결함을 보완하기 위해서 나온 대표적인 해시 알고리즘이 바로 SHA 알고리즘입니다. 

SHA 알고리즘은 해시된 문자열을 만들어내기 위해 비트 회전 연산이 추가된 방식입니다. 

쉽게 말해서 해시된 문자열의 비트 값을 회전하면서 반복적으로 해시 처리를 하는 것입니다.

그런데 SHA 알고리즘은 컴퓨터로는 알아낼 수 있습니다

해커 입장에서는 사용자가 패스워드로 사용할만한 문자열들을 미리 목록(**Rainbow Table**)으로 만들어 놓고,

이 목록에 있는 문자열을 동일한 알고리즘으로 암호화한 후, 탈취한 암호화된 문자열과 서로 비교하는 작업을 

통해 패스워드의 원본 문자열을 알 수 있게 되는데, 이러한 공격을 **Rainbow Attack**이라고 합니다.

자동화된 Rainbow Attack을 통해 비교할 수 있는 다이제스트(Digest)의 양이 초당 50억 개 이상입니다

그런데 Rainbow Attack을 백 퍼센트 무력화할 순 없겠지만 컴퓨터가 다이제스트(Digest)를 비교하는 작업

의 횟수를 줄일 가장 단순한 방법은 앞에서 살펴본 SHA 알고리즘처럼 해시된 다이제스트를 또 해시하고, 또 

해시된 다이제스트를 반복적으로 해시하는 것입니다 이를 **키 스트레칭**이라고 합니다.

해시 처리가 반복되면 될수록 다이제스트(Digest)를 비교하는 횟수도 현저히 줄어듭니다.

또 한 가지 방법은 **솔트(Salt)**를 이용하는 방법입니다. 

솔트란 패스워드로 입력하는 원본 메시지에 임의의 어떤 문자열을 추가해서 해시 처리하는 것을 의미합니다. 

솔트를 추가하면 Rainbow Table을 이용해 비교해야 하는 경우의 수가 늘어나기 때문에 완벽하지는 않지만 Rainbow Attack에 대응할 수 있습니다. 

**Work Factor를 추가한 Hash 알고리즘**

Work Factor는 **공격자가 해시된 메시지를 알아내는 데 더 느리게 더 비용이 많이 들게 해주는 특정 요소**를 의미합니다.

Work Factor를 추가한 Hash 알고리즘이 **PBKDF2**, **bcrypt**, **scrypt**입니다. 

**PBKDF2**나 **bcrypt**의 경우 Work Factor로 **솔트와 키 스트레칭**을 기본적으로 사용하지만 내부적으로 훨씬 

복잡한 알고리즘을 이용해서 공격자의 공격을 느리게 만듭니다.

**scrypt**는 기본적으로 다이제스트 생성 시, **메모리 오버헤드를 갖도록 설계**되어 있기 때문에 무차별 대입 공격

(Brute Force Attack)을 시도하기 위해 병렬화 처리가 매우 어려운 특징이 있습니다

</div>
</details>


</div>
</details>



[^fn-nth-2]: The 2nd footnote source