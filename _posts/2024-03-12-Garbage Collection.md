---
title: Garbage Collection
date: 2024-03-12 23:00:00 +0900
categories: [JAVA, Java의 특징]
tags: [JAVA]
math: true
mermaid: true

---


## **Garbage Collection(가비지 컬렉션)이란?**

![image](https://github.com/ararp1006/mainProject/assets/130068083/03046fc2-7920-4ee3-84a2-2c78d92ceb0c)

자바의 메모리 관리 방법 중의 하나로 JVM(자바 가상 머신)의 Heap 영역에서 

동적으로 할당했던 메모리 중 필요 없게 된 메모리 객체(garbage)를 모아 

주기적으로 제거하는 프로세스를 말합니다.

> 장점

Java(파이썬, 자바스크립트 등등)에서는 가비지 컬렉터가 메모리 관리를 대행해주기 때문에 Java 프로세스가 한정된 메모리를 효율적으로 사용할수 있게 하고, 
 
개발자 입장에서 메모리 관리, 메모리 누수(Memory Leak) 문제에서 대해 관리하지 않아도 되어 오롯이 개발에만 집중할 수 있다는 장점이 있습니다.


> 단점

자동으로 처리해준다 해도 메모리가 언제 해제되는지 정확하게 알 수 없어 제어하기 힘들며, 

가비지 컬렉션(GC)이 동작하는 동안에는 다른 동작을 멈추기 때문에 오버헤드가 발생되는 문제점이 있습니다.

이를 전문적인 용어로 Stop-The-World 라고 합니다.



===
###  **Stop-The-World**

STW (Stop The World)GC를 수행하기 위해 JVM이 프로그램 실행을 멈추는 현상을 의미합니다.

GC가 작동하는 동안 GC 관련 Thread를 제외한 모든 Thread는 멈추게 되어 서비스 이용에 차질이 생길 수 있습니다.

===

### **가비지 컬렉션 대상**

![image](https://github.com/ararp1006/mainProject/assets/130068083/45b7d85e-e7e8-4065-97e6-b0934dd0a910)


> Reachable : 객체가 참조되고 있는 상태입니다.

> Unreachable  : 객체가 참조되고 있지 않은 상태입니다. (GC의 대상이 됨) 

> 한 객체들은 다른 객체를 참조하고 참조된 다른 객체들도 또 다른 객체들을 참조할 수 있으므로 객체들은 **참조사슬**을 이룹니다.

> root set : 유효한 최초의 참조를 뜻합니다.

===




### **Mark and Sweep**

> Mark
 
GC가 스택의 모든 변수 혹은 Reachable 객체를 스캔하면서 **각각 어떤 객체를 참조하고 있는지 참조하는 과정입니다.**

이 과정에서 stop-the-world가 발생합니다.

> Sweep

Mark되어있지 않은 객체들을 **힙에서 제거하는 과정입니다.**

## **Garbage Collection(가비지 컬렉션) 알고리즘**


### **Serial GC**

![image](https://github.com/ararp1006/mainProject/assets/130068083/579940a4-42e9-43f8-9cc2-e5588c6c0ef5)

>  Mark and Sweep(Mark Compact Algorithm)방법으로 GC가 진행됩니다.

### **Parallel GC**

![image](https://github.com/ararp1006/mainProject/assets/130068083/97cdca0d-d5cf-4fc5-8dab-2b2134471680)

> Multi Thread에서 GC를 실행합니다.

> 병렬적인 처리 덕분에 Serial GC보다 처리 속도가 빠릅니다.

> 자바8의 기본 GC입니다.


### **CMS(Concurrent Mark Sweep) GC**

![image](https://github.com/ararp1006/mainProject/assets/130068083/df0db4d1-8878-41b0-a70a-707c635bfe7a)

> Concurrent(공존하는, 동시에 발생하는) Mark Sweep의 줄임말입니다.


**Initial Mark (초기 표시)**:

가장 먼저 GC Root가 직접 참조하는 객체들을 식별하고 표시하는 단계입니다.

 이 과정에서는 Stop-the-World가 발생하며 모든 애플리케이션 스레드가 일시 중지됩니다.


**Concurrent Mark (병행 표시)**:

Initial Mark 이후, GC는 나머지 객체들을 찾아서 표시하는 작업을 병행하여 수행합니다. 

이 과정에서는 Stop-the-World가 발생하지 않으며, 애플리케이션 스레드가 계속 실행됩니다.


**Remark (재표시)**:

Concurrent Mark 중에 변경된 사항이 없는지 확인하고, 변경된 사항이 있다면 추가로 마킹하는 과정입니다.

이 과정에서는 Stop-the-World가 발생하며, 애플리케이션 스레드가 일시 중지됩니다.


**Concurrent Sweep (병행 삭제)**:

접근할 수 없는(Unreachable) 객체들을 삭제하고, 이 과정은 병행하여 수행됩니다.

Stop-the-World가 발생하지 않으며, 애플리케이션 스레드가 계속 실행됩니다.


> 모든 애플리케이션의 응답 속도가 매우 중요할 때 주로 사용합니다.


### **G1 GC**

![image](https://github.com/ararp1006/mainProject/assets/130068083/3c67191c-de83-4a73-a4df-7152aa0ee09f)

> Garbage First의 약자입니다.

> Heap에 전역적으로 Marking 하고, 가장 많은 공간이 있는 곳부터 메모리 회수를 진행하기 때문에 Garbage First라는 이름이 붙었습니다.

> 대용량 메모리에 적합한 GC입니다.

> 자바9의 기본 GC입니다.
