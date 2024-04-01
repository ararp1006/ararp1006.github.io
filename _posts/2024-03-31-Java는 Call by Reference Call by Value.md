---
title: Java는 Call by Reference? Call by Value?
date: 2024-03-31 23:00:00 +0900
categories: [JAVA, Java의 특징]
tags: [JAVA]
math: true
mermaid: true

---
![img](https://github.com/ararp1006/Algorithm/assets/130068083/621c5fd5-3e53-4bd0-99c6-502d122bde21)

## **Call by Value (값에 의한 호출)**

함수가 호출될 때, 메모리 공간 안에서는 함수를 위한 별도의 임시 공간이 생성됩니다.

함수 호출시 인자로 전달되는 변수의 값을 복사하여 함수의 인자로 전달합니다.

복사된 인자는 함수 안에서 지역적으로 사용되는 local value의 특성을 가집니다.

따라서 함수 안에서 인자의 값이 변경되어도, 외부의 변수의 값은 변경되지 않습니다.


## **Call by Reference (참조에 의한 호출)**

함수가 호출될 때, 메모리 공간 안에서는 함수를 위한 별도의 임시 공간이 생성됩니다.

함수 호출시 인자로 전달되는 변수의 레퍼런스를 전달합니다. (해당 변수를 가리킵니다.)

따라서 함수 안에서 인자의 값이 변경되면, 인자로 전달된 변수의 값도 함께 변경됩니다.


<HR>

## **Java는 항상 Call by Value 입니다.**

기본자료형의 경우 해당하는 변수의 값을 복사해서 전달합니다.

참조자료형의 경우 해당하는 변수가 가지는 값이 레퍼런스이므로 

인자로 넘길 때 Call by Value에 의해 변수가 가지고 있는 레퍼런스가 복사되어 전달됩니다.

<hr>

**레퍼런스**

객체를 가리키는 주소를 가리키는 주소

``` String str = "Hello";```

```str```은 문자열 "Hello"를 가리키는 레퍼런스입니다. 

"Hello"라는 문자열은 실제로 메모리의 어딘가에 저장되어 있고, 

```str```은 그 **문자열을 가리키는 주소**를 가지고 있습니다.


<HR>

## **착각하기 쉬운 오해**

**1. 특정 메서드 내에서 전달 받은 객체의 상태를 변경 할 수 있다.**

```java

public class Main {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Hello");

        // 메서드 호출
        modifyStringBuilder(sb);

        // 변경된 내용 출력
        System.out.println("StringBuilder 내용: " + sb);
        //Hello World
    }

    // StringBuilder를 수정하는 메서드
    public static void modifyStringBuilder(StringBuilder str) {
        str.append(" World");
    }
}

```
```modifyStringBuilder()``` 메서드를 통해 ```StringBuilder 객체```를 전달하고 해당 메서드에서는 해당 객체의 내용을 변경합니다. 

그런데도 불구하고, ```main() 메서드```에서``` StringBuilder 객체의 내용이 변경```된 것을 확인할 수 있습니다.


> "참조에 의한 전달"처럼 보일 수 있지만 실제로는 객체의 참조를 전달하는 것이 아니라,

> **참조에 해당하는 값(메모리 주소)를 복사하여 전달합니다**. 

> 즉, 메서드 내에서 객체의 상태를 변경하더라도 원본 객체의 참조는 변경되지 않습니다.


**2.  참조변수는 임의의 객체에 대한 레퍼런스를 저장하므로 메서드로 전달한 값이**

**레퍼런스(Call by Reference)이다.**

```java
public class Main {
    public static void main(String[] args) {
        // 참조 변수 선언 및 초기화
        StringBuilder sb1 = new StringBuilder("Hello");

        // 다른 객체의 레퍼런스를 저장
        StringBuilder sb2 = sb1;

        // 메서드 호출
        modifyStringBuilder(sb2);

        // 변경된 내용 출력
        System.out.println("StringBuilder 내용: " + sb1);
         //Hello World
    }

    // StringBuilder를 수정하는 메서드
    public static void modifyStringBuilder(StringBuilder str) {
        str.append(" World");
    }
}


```

```sb1```과 ```sb2```는 모두 동일한 ```StringBuilder```객체를 가리키고 있습니다. 

```sb2 = sb1```는 ```sb1```이 가리키는 객체의 레퍼런스를 ```sb2```에 복사하는 것이고,

새로운 객체를 생성하는 것이 아닙니다.

```modifyStringBuilder()``` 메서드를 호출할 때 ```sb2```가 가리키는 객체의 상태가 변경되면, ```sb1```이 가리키는 객체의 상태도 함께 변경됩니다

>" 참조에 의한 전달"로 해석될 수 있지만, 실제로는 메서드로 객체의 참조가 전달되는 것이 아니라 

> **참조에 해당하는 값(메모리 주소)가 복사되는 것입니다**