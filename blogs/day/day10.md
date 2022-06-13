---
title: Java方法Ⅰ
date: 2022-6-9
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Java方法 1
### 何谓方法？
* System.out.println()就是一个方法，System是一个类，out是对象，println是方法
* Java方法是语句的集合，它们在一起执行一个功能
  * 方法是解决一类问题的步骤的有序组合
  * 方法包含于类或对象中
  * 方法在程序中被创建，在其他地方被引用
* 设计方法的原则：方法的本意是功能块，就是实现某个功能的语句块的集合，我们设计方法的时候，最好保持方法的原子性，就是一个方法只完成一个功能，这样有利于我们后期的发展
* 方法的命名规则：首字母大写+驼峰结构
```java
	public static void main(String[] args){}
	//public,static是一个修饰词,加入static变成类变量
	//void是返回的类型，void即不返回
	//加法
	public int add(int a,int b){
		return //返回
	}
	//不加static需要通过new.add()来调用
```
### 方法的定义
* Java的方法类似于其它语言的函数，是一种用来完成特定功能的代码片段，一般情况下，定义一个方法包含以下语法：
* 方法包含一个方法头和一个方法体。下面是一个方法的所有部分：
  * 修饰符：修饰符，这是可选的，告诉编译器如何调用该方法，定义了该方法的访问类型。
  * 返回值类型：方法可能会返回值。returnValueType是方法返回值的数据类型，有些方法执行所需的操作，但没有返回值，在这种情况下，returnValueType是关键字void
  * 方法名：是方法的实际名称，当方法被调用时，传递值给参数，这个值被称为实参或变量，参数列表是指方法的参数形式、顺序和参数的个数，参数是可选的，方法可以不包含任何参数。
    * 形式参数：在方法被调用时用于接收外界输入的数据
    * 实参：调用方法时实际传给方法的数据
  * 方法体：方法体包含具体的语句，定义该方法的功能
```java
修饰符 返回值类型 方法名(参数类型 参数名){
...
方法体
...
return 返回值;
}
```
此外return还可以终止方法！ 

### 方法调用
* 调用方法：对象名.方法名(实参列表)
* Java支持两种调用方法的方式，根据方法是否返回值来选择
* 当方法返回一个值的时候，方法调用通常被当做一个值，eg：
```java
	int larger = max(30,40);
```
* 如果方法返回值是void，方法调用一定是一条语句
```java
	System.out.println("")
```
* 值传递(Java)和引用传递
实例1：
```java
package Method;
public class Demo01 {
    //main方法
    public static void main(String[] args) {
        int c = add(3,4);
        System.out.println(c);
    }
    //加法方法，加入static修饰词可以变成类方法可以直接使用
    public static int add(int a,int b){
        return a + b;
    }
}
```
运行：
```java
7
```

实例2：
```java
package Method;
public class Demo02 {
    //main方法
    public static void main(String[] args) {
        Demo02 demo02 = new Demo02();
        int c = demo02.add(3,4);
        System.out.println(c);
    }
    //加法方法，实例方法，不能直接引用
    public int add(int a,int b){
        return a + b;
    }
}
```
运行：
```java
7
```

实例3：
```java
package Method;
public class Demo03 {
    //main方法
    public static void main(String[] args) {
    add(3,4);
    }
    //加法方法，void返回空值，即要输出
    public static void add(int a,int b){
        System.out.println((a+b));
    }
}
```
运行：
```java
7
```