---
title: RedisTemplate
date: 2024-03-16  23:00:00 +0900
categories: [DataBase,Redis ]
tags: [DataBase, Redis ]
math: true
mermaid: true

---

![image](https://github.com/ararp1006/Algorithm/assets/130068083/ba52b341-2c70-4bf8-85bd-b9e5c186b1ff)

## **RedisTemplate?**

Spring 프레임워크에서 Redis와 상호 작용하기 위한 클래스입니다.

ReedisTemplate을 사용하여 Redis의 다양한 데이터 구조를 다루는 데 사용됩니다.

Redis는 문자열, 리스트, 해시, 집합, 정렬된 집합 등의 다양한 데이터 구조를 지원합니다


##  **구성 요소**


``RedisConnectionFactory``: **Redis 서버와의 연결을 설정하고 관리**하는 객체입니다. 

```RedisSerializer```: RedisTemplate은 데이터를 **직렬화하여** Redis 서버로 보냅니다. 

 **Java 객체를 Redis 데이터 형식으로 변환**하고, **Redis 데이터를 Java 객체로 역직렬화**하는 데 사용됩니다. 

```RedisOperations```:Redis의 다양한 데이터 구조를 다루는 데 사용됩니다. 

예를 들어, 문자열 값을 다루기 위해서는 RedisOperations<String, String>을 사용할 수 있습니다.





## **RedisTemplate 메서드**

```opsForValue()```: **문자열 값**을 다루는 RedisOperations 객체를 반환합니다.

이 객체를 사용하여 문자열 데이터를 저장, 조회, 수정, 삭제할 수 있습니다.

```
redisTemplate.opsForValue().set("key1", "value1");
String value = redisTemplate.opsForValue().get("key1");
System.out.println("String value: " + value);

//결과 : String value: value1
```

```opsForList()```: **리스트 값**을 다루는 RedisOperations 객체를 반환합니다. 

이 객체를 사용하여 리스트 데이터를 다루는 메서드를 호출할 수 있습니다.

```
redisTemplate.opsForList().leftPush("listKey", "value2");
redisTemplate.opsForList().leftPush("listKey", "value3");
List<String> listValues = redisTemplate.opsForList().range("listKey", 0, -1);
System.out.println("List values: " + listValues);

//결과 :List values: ["value3", "value2"]

```


```opsForHash()```: **해시 값**을 다루는 RedisOperations 객체를 반환합니다. 

이 객체를 사용하여 해시 데이터를 다루는 메서드를 호출할 수 있습니다.

```
redisTemplate.opsForHash().put("hashKey", "field1", "value4");
redisTemplate.opsForHash().put("hashKey", "field2", "value5");
String hashValue1 = (String) redisTemplate.opsForHash().get("hashKey", "field1");
String hashValue2 = (String) redisTemplate.opsForHash().get("hashKey", "field2");
System.out.println("Hash value 1: " + hashValue1);
System.out.println("Hash value 2: " + hashValue2);

//결과 : Hash value 1:value4
        Hash value 2: value5

```

```opsForSet()```: **집합 값**을 다루는 RedisOperations 객체를 반환합니다. 

이 객체를 사용하여 집합 데이터를 다루는 메서드를 호출할 수 있습니다.

```
redisTemplate.opsForSet().add("setKey", "value6");
redisTemplate.opsForSet().add("setKey", "value7");
Set<String> setValues = redisTemplate.opsForSet().members("setKey");
System.out.println("Set values: " + setValues);

// 결과 : Set values: [value6, value7]

```


```opsForZSet()```: **순서가 있는 집합 값**을 다루는 RedisOperations 객체를 반환합니다. 

이 객체를 사용하여 정렬된 집합 데이터를 다루는 메서드를 호출할 수 있습니다.

```
redisTemplate.opsForZSet().add("zsetKey", "value8", 1);
redisTemplate.opsForZSet().add("zsetKey", "value9", 2);
Set<String> zsetValues = redisTemplate.opsForZSet().range("zsetKey", 0, -1);
System.out.println("Sorted set values: " + zsetValues);

//결과 Sorted set values: [value8, value9]

```


