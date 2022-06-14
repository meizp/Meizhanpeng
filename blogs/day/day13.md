---
title: Java数组Ⅱ
date: 2022-6-12
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Java数组 2
### 数组的四个基本特点
* 其长度是确定的，数组一旦被创建，它的大小就是不可以改变的
* 其元素必须是相同类型，不允许出现混合类型
* 数组中的元素可以是任何数据类型，包括基本类型和引用类型
* 数组变量属引用类型，数组也可以看成是对象，数组中的元素相当于该对象的成员变量，数组本身就是对象，Java中对象是在堆中的，因此数组无论保存原始类型还是其他对象类型，数组对象本身是在堆中的

### 数组边界
* 下标的合法区间：[0,length-1]，如果越界就会报错；
```java
	public static void main(String[] args){
	int[] a = new int[2]
	System.out.println(a[0])
	}
```
* ArraylndexOutOfBoundsException：数组下标越界异常！
* 小结：
  * 数组是相同数据类型（数据类型可以为任意类型）的有序集合
  * 数组也是对象，数组元素相当于对象的成员变量
  * 数组长度是确定的，不可变的，如果越界，则报：ArraylndexOutOfBoundsException
  实例1：
```java
package com.mei.Array;
public class Error01 {
    public static void main(String[] args) {
        int[] a = new int[2];
        //此时a数组 = [0,0]，只有a[0]，和a[1]
        System.out.println(a[2]);
    }
}
```

运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/数组索引超标报错.png" style="zoom:80%;" />


### 数组使用
* 普通的for循环
* For-Each循环：增强型的for循环，但取不到下标
  * For-Each的语句格式：
```java
for(元素类型t 元素变量x : 遍历对象obj){
引用了x的java语句;
}
```
* 数组作方法入参
* 数组作返回值

实例2（for循环和增强for循环）：
```java
package com.mei.Array;
public class Demo02 {
    public static void main(String[] args) {
        int[] a = {1,2,3,4,5};
        //普通的for循环
        for(int i=0;i<a.length;i++){
            System.out.print(a[i]+"\t");
        }
        System.out.println();
        System.out.println("============");
        //for each循环
        for (int i:a) {
            System.out.print(i+"\t");
        }
    }
}
```
运行：

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/数组for和增强for.png" style="zoom:50%;" />

实例2（数组作为参数入参，数组作为返回值）：
```java
package com.mei.Array;
public class Demo03 {
    public static void main(String[] args) {
        int[] a = {1,2,3,4,5};
        System.out.println(add(a));
        System.out.println("==========");
        int[] b = reverse(a);
        for (int i:b
             ) {
            System.out.println(i);
        }
    }
    //数组作为参数入参
    public static int add(int[] a){
        int sum = 0;
        for(int i:a){
            sum += i;
        }
        return sum;
    }
    //反转数组，数组作为返回值
    public static int[] reverse(int[] a){
        int[] result = new int[a.length];
        for(int i=0;i<a.length;i++){
            result[a.length - i - 1] = a[i];
        }
        return result;
    }
}
```
运行:

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/数组入参和返回.png" style="zoom:50%;" />
