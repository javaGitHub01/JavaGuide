<!-- MarkdownTOC -->

- [ArrayList简介](#arraylist简介)
- [ArrayList源码分析](#arraylist源码分析)
    - [System.arraycopy\(\)和Arrays.copyOf\(\)方法](#systemarraycopy和arrayscopyof方法)
        - [两者联系与区别](#两者联系与区别)
    - [ArrayList核心扩容技术](#arraylist核心扩容技术)
    - [内部类](#内部类)

<!-- /MarkdownTOC -->

### ArrayList简介
　　ArrayList 的底层是数组队列，相当于动态数组。与 Java 中的数组相比，它的容量能动态增长。在添加大量元素前，应用程序可以使用`ensureCapacity`操作来增加 ArrayList 实例的容量。这可以减少递增式再分配的数量。
    
   它继承于 **AbstractList**，实现了 **List**, **RandomAccess**, **Cloneable**, **java.io.Serializable** 这些接口。
### ArrayList核心源码

```java
java代码
```
### <font face="楷体" id="1" id="5">ArrayList源码分析</font>
####  System.arraycopy()和Arrays.copyOf()方法
　　通过上面源码我们发现这两个实现数组复制的方法被广泛使用而且很多地方都特别巧妙。比如下面<font color="red">add(int index, E element)</font>方法就很巧妙的用到了<font color="red">arraycopy()方法</font>让数组自己复制自己实现让index开始之后的所有成员后移一个位置:

##### 两者联系与区别
**联系：**
看两者源代码可以发现`copyOf()`内部调用了`System.arraycopy()`方法
**区别：**
