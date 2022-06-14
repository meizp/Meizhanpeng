---
title: Java数组Ⅰ
date: 2022-6-11
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Java数组 1
### 数组的定义
* 数组是相同类型数据的有序集合
* 数组描述的是相同类型的若干数据，按照一定先后次序排列组合而成
* 其中，每一个数据称作一个数组元素，每个数组元素可以通过一个下标来访问它们
* 数组的标号是从0开始的
### 数组声明创建
* 首先必须声明数组变量，才能在程序中使用数组，（声明数组的时候数组并不真实存在，只有创建数组后才存在）语法：
```java
	dataType[] arrayRefVar;  //首选的方法
	或
	dataType arrayRefVar[];  //效果相同，但不是首选方法
```
* Java语言使用new操作符来创建数组，语法：
```java
dataType[] arrayRefVar;
arrayRefVar = new dataType[arraySize];
```
当然也可以声明创建结合在一起，语法：
```java
	dataType[] arrayRefvar = new dataType[arraySize];
```
* 数组的元素是通过索引访问的，数组索引从0开始
* 获取数组长度
```java
	arrays.length
```

### 内存分析
Java内存分析：
* 堆：
  * 存放new的对象和数组
  * 可以被所有的线程共享，不会存放别的对象引用
* 栈：
  * 存放基本变量类型（会包含这个基本类型的具体数值）
  * 引用对象的变量（会存放这个引用在堆里面的具体地址）
* 方法区：
  * 可以被所有的线程共享
  * 包含了所有的class和static变量

运行机制：
  <img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/类的运行机制.png" style="zoom: 50%;" />

### 三种初始化
* 静态初始化：创建+赋值
```java
	int[] a = {1,2,3};
	Man[] mans = {new Man(1,1),new Man(2,2)};
```
一旦定义之后a就不可改变了，静态初始化定义后长度不可改变
* 动态初始化：包含默认初始化
```java
	int[] a = new int[2];
	a[0] = 1;
	a[1] = 2;
```
* 数组的默认初始化
  * 数组是引用类型，它的元素相当于类的实例变量，因此数组一经分配空间，其中的每个元素也被按照实例变量同样的方式被隐式初始化。

实例1：
```java
package com.mei.Array;
public class Demo01 {
    public static void main(String[] args) {
        int[] a = {1,2,3,4,5};//创建＋赋值，静态初始化
        int[] c;//声明数组
        c = new int[5];//创建数组，动态初始化
        int[] d = new int[5];//声明+创建，动态初始化
    }
}
```
实例2（对象数组）：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/对象数组.png" style="zoom: 50%;" />
