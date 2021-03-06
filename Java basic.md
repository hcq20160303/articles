﻿# Java基础

---

### 1. [Java的内存管理模型](http://blog.csdn.net/wike163/article/details/6635321)
java内存管理是在进程内部发生的，主要分为五个区域：堆、栈、程序计数器、方法区以及常量池，各个区域的功能如下：

- [x] 堆：被进程当中的所有线程共享，存放用户`new`的对象以及数组。
- [x] 栈：每个线程都有一个对应的栈，分为**Java虚拟机栈**和**本地方法栈**，这两个栈的区别是后者为[本地方法](http://blog.csdn.net/wike163/article/details/6635321)服务，前者为Java自身的方法服务；存储的数据主要是方法当中的局部变量。
- [x] 程序计数器：每个线程都有一个，用于存储当前执行指令的地址。
- [x] 方法区：进程内的所有线程共享，存储对象类型信息，比如说对象类型、对象所拥有的方法、属性等。
- [x] 常量池：方法区的一部分，为所有线程共享，用于存储编译期间产生的字面常量以及符号引用。

### 2. Java引用和指针的区别
这一点在**Java的内存管理模型**参考文章介绍了。对于如下一行代码：
```java
Object object = new Object();
```
变量`object`为一个引用变量，保存在Java虚拟机栈中，通过`new Object()`创建出的对象实例是保存在Java堆中，如何通过栈中的`object`变量得到`new Object()`创建出的对象实例？这就牵涉到Java引用和指针。
一般来说，通过引用变量得到实例对象有两种实现方式，一种是句柄，另外一种是指针。这两种的区别是句柄将指针封装了一层：首先引用变量存放句柄在Java堆中的地址，之后句柄存放实例对象在堆中的地址。

### 3. [深拷贝和浅拷贝](http://www.cnblogs.com/shuaiwhu/archive/2010/12/14/2065088.html)
再讲深拷贝之前应该先谈谈浅拷贝，浅拷贝指的是在拷贝对象时，仅仅将对象的引用拷贝一份，而并没有重新生成另外一个一模一样的新对象；而深拷贝则生成了另外一个一模一样的新对象。
深拷贝和浅拷贝在对象复制时需要特别注意，最好重写`clone()`方法。

### 4. Map、Set、List的异同
- [x] Set和List都是继承自Collection接口，而Map是一个独立的接口。
- [x] Map、Set、List的元素都可以为`null`，但是Map的`key`和Set都不允许重复，当添加多个`null`元素时，只会有一个成功添加，程序并不报错；与之不同的是，List可以允许重复，能够成功添加多个`null`元素。
- [x] 
- [x] List接口主要有以下几个实现类：LinkedList、ArrayList、Vector、Stack。LinkedList由链表实现，非线程安全；ArrayList由数组实现，非线程安全；Vector也是由数组实现，它和ArrayList不同的地方主要有：
 - [ ] Vector线程安全，ArrayList线程不安全；
 - [ ] Vector在容量不够时，扩容机制是翻倍扩容；ArrayList扩充0.5倍的原始容量；
 - [ ] Stack继承自Vector，实现了栈的功能；
- [x] 
- [x] 
### ？ 字面常量和符号引用（`TODO`）




