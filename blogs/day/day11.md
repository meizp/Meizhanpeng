---
title: Java方法Ⅱ
date: 2022-6-10
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Java方法 2
### 方法的重载
* 重载就是在一个类中，有相同的函数名称，但形参不同的函数。
* 方法的重载的规则：
  * 方法名称必须相同
  * 参数列表必须不同（个数不同、或类型不同、参数排列顺序不同等）
  * 方法的返回类型可以相同也可以不相同
  * 仅仅返回类型不同不足以成为方法的重载
* 实现理论：
  * 方法名称相同时，编译器会根据调用方法的参数个数、参数类型等去逐个匹配，以选择对应的方法，如果匹配失败，则编译器报错。
  实例1（求和方法）：
```java
package com.mei.Method;
public class Demo04 {
    public static void main(String[] args) {
        int[] b = {1, 2, 3, 4, 5};
        System.out.println(add(b));
        System.out.println(add(1, 2));
        System.out.println(add(1, 2,6));
        System.out.println(add(1.56, 23.4));
    }
    public static int add(int a, int b) {
        return a + b;//求和的方法
    }
    public static int add(int a,int b,int c){
        //重载，参数个数由2->3
        return a + b + c;
    }
    public static double add(double a, double b) {
        //重载，将int类型换为double类型，参数类型不同
        return a + b;
    }
    public static int add(int[] a) {
        //重载，参数类型不同，返回类型相同
        int i;
        int sum = 0;
        for (i = 0; i < a.length; i++) {
            sum += a[i];
        }
        return sum;
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/参数的重载.png" style="zoom:50%;" />

### 命令行传参
* 有时候你希望运行一个程序时候再传递给它消息
```java
	public class CommandLine{
		public static void main(String[] args){
			for (int i=0 ;i<args.length;i++){
				System.out.println("args["+i+"]:"+args[i]);
			}
		}
	}
```

### 可变参数
* JDK1.5开始，Java支持传递同类型的可变参数给一个方法
* 在方法声明中，在指定参数类型后加一个省略号(...)
* 一个方法中只能指定一个可变参数，它必须是方法的最后一个参数，任何普通的参数必须在它之前声明
* **可变参数可以兼容数组参数，但数组参数无法兼容可变参数**

实例2（求最大值方法）：
```java
package com.mei.Method;
public class Demo05 {
    public static void main(String[] args) {
        double[] a ={1,2,3,4,5};
        System.out.println(max(a));
        System.out.println(max(1,2,3,4,5));
    }
    public static double max(double... a){
        //可变参数求最大值，参数可以为数组，也可以直接传入
        if(a.length == 0){
            return 0;
        }else {
            double max = a[0];
            for(int i = 1;i<a.length;i++){
                if(max < a[i]){
                    max = a[i];
                }
            }
            return max;
        }
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/可变参数.png" style="zoom:50%;" />

### 递归
* A方法调用B方法，我们很容易理解！
* 递归就是：A方法调用A方法！就是自己调用自己
* 利用递归可以用简单的程序来解决一些复杂的问题，它通常把一个大型复杂的问题层层转化为一个与原问题相似的规模较小的问题来求解，递归策略只需少量的程序就可描述出解题过程所需要的多次重复计算，大大地减少了程序的代码量。递归的能力在于用有限的语句来定义对象的无限集合
* 递归结构包括两个部分：
  * 递归头：什么时候不调用自身方法。如果没有头，将陷入死循环
  * 递归体：什么时候需要调用自身方法
  基数比较小的情况下用递归的方法
  大计算的时候最好不要用递归的方法，java在递归的时候占栈，会使内存崩掉
  实例3（计算n!）：
```java
package com.mei.Method;

public class Demo06 {
    public static void main(String[] args) {
        System.out.println(factorial(6));
    }
    public static int factorial(int a){
        if(a<0){
            System.out.println(a+"!不存在");
        //考虑事情要全面完整
        } else if (a==0||a==1) {
            return 1 ;
        }else {
            return a*factorial(a-1);
        }
        return 0;
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/函数递归阶乘.png" style="zoom: 50%;" />

实例4（汉诺塔问题）：
```java
package com.mei.Method;
public class Hanoi {
    //a->b->c
    //3个
    //先把n-1个圆盘移动：a->b，再移动最后一个圆盘，最后把n-1个圆盘：b->c
    static int count =0;
    public static void main(String[] args) {
        move(3,'a','b','c');
    }
    public static void move(int n,char a,char b,char c){
        if(n==1){
            System.out.println("第"+n+"个圆盘："+a+"->"+c);
        }else{
            move(n-1,a,c,b);
            System.out.println("第"+n+"个圆盘："+a+"->"+c);
            move(n-1,b,a,c);
        }
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/Hanoi.png" style="zoom:67%;" />