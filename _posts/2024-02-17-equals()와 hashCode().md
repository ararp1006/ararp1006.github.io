---
title: equals(),hashCode(),==
date: 2024-02-17 23:00:00 +0900
categories: [JAVA, Java의 특징]
tags: [JAVA]
math: true
mermaid: true

---
## **== 연산자**

피연산자가 primitive type(int, double, boolean, ...)일 때는 값이 같은지 비교하고,

피연산자가 그 외 객체, reference type일 때 가리키는 주소가 같은지를 검사합니다.

'==' 연산자는 두 객체가 같은 것을 가리킬 때만 true입니다.

```java

String str1 = "hello";
String str2 = "hello";
System.out.println(str1 == str2);//true

String str3 = new String("hello");
String str4 = new String("hello");
System.out.println(str3 == str4);//false
```

## **equals()**

두 객체의 내용이 같은지 검사하는 메서드 입니다.

primitive type은 내용이 같은지 검사하고, reference type은 객체의 주소가 같은지 검사합니다.

'==' 연산자와 다른 점은 완전히 같은 객체를 가리키지 않아도 개발자가 true로 만들 수 있습니다.

```java
String str1 = "hello";
String str2 = "hello";
System.out.println(str1.equals(str2));//true

String str3 = new String("hello");
String str4 = new String("hello");
System.out.println(str3.equals(str4));//true

```
str1과 str2는<span style="color: #ffd33d"> 같은 주소를 가리키고 있을 뿐만아니라 내용(값)도 같으므로</span> equals메서드의 결과 true를 리턴합니다.

str3과 str4는 <span style="color: #ffd33d">가리키는 주소는 달라도 내용(값)이 같으므로</span> equals메서드의 결과 true를 리턴합니다.

하지만 <span style="color: #ffd33d">String클래스는 내부적으로 equals메서드를 오버라이드해서</span> 이런 결과가 나타납니다.

String클래스가 아닌 클래스의 객체는 자바가 내용이 같은지 판단하기 어렵습니다.

따라서 equals() 메서드를 오버라이드(재정의)해서 두 객체의 내용이 같은지를 정의해줘야 올바르게 작동합니다.

```java

class Person {
    long id; 

    public boolean equals(Object obj) {
        if (!(obj instanceof Person))
            return false;
        
        Person p = (Person)obj;
        
        return id == p.id;
        
    }

    Person(long id) {
        this.id = id;
    }
}

public class equalsOverriding {
    public static void main(String[] args) {
        Person p1 = new Person(8011081111222L);
        Person p2 = new Person(8011081111222L);

        if(p1.equals(p2))
            System.out.println("p1과 p2는 같다");
        else
            System.out.println("p1과 p2는 다르다");
    }
}

p1과 p2는 같다

```
![image](https://github.com/ararp1006/Algorithm/assets/130068083/44bbaa08-271b-4dcc-b952-8d26dfe6d87c)


## **hashCode()**

객체의 해쉬코드(hash code)를 반환하는 메서드입니다.

 <span style="color: #ffd33d">equals()를 오버라이딩하면, hashCode()도 오버라이딩해야합니다.</span>

 <span style="color: #ffd33d">equals()의 결과가 true인 두 객체의 해시코드는 같아야 하기 때문입니다.</span>

```java
String str1 = new String("abc");
String str2 = new String("abc");
System.out.println(str1.equals(str2)); // true
System.out.println(str1.hashCode()); // 96354
System.out.println(str2.hashCode()); // 96354
```
```java 

public class Person {
    long id;

    public boolean equals(Object obj) {
        if (this == obj) {
            return true;
        }

        if (!(obj instanceof Person)) {
            return false;
        }

        Person p = (Person) obj;
        return id == p.id;
    }

    public int hashCode() {
        return Long.hashCode(id);
    }

    Person(long id) {
        this.id = id;
    }
}

public class EqualsOverriding {
    public static void main(String[] args) {
        Person p1 = new Person(8011081111222L);
        Person p2 = new Person(8011081111222L);

        if (p1.equals(p2)) {
            System.out.println("p1과 p2는 같다");
        } else {
            System.out.println("p1과 p2는 다르다");
        }

        System.out.println("p1의 해시코드: " + p1.hashCode());
        System.out.println("p2의 해시코드: " + p2.hashCode());
    }
}
p1과 p2는 같다

p1의 해시코드와 ㅔ2의 해시코드가 같다.
```



