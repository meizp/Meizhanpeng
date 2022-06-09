---
title: Java流程控制Ⅱ
date: 2022-6-8
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Java流程控制 2

### 循环结构
* while循环
* do...while循环
* for循环
* 在Java5中引入了一种主要用于数组的增强型for循环
### while 循环
* while循环是最基本的循环，它的结构是：
```java
while(布尔表达式){
//循环内容
}
```
* 只要布尔表达式为true，循环就会一直执行下去

* 我们大多数情况是会让循环停止下来的，我们需要一个让表达式失效的方式来结束循环

* 少部分情况需要循环一直执行，比如服务器的请求响应监听等

* 循环条件一直为true就会造成无限循环【死循环】，我们正常的业务编程中应尽量避免死循环，会影响程序性能或者造成程序卡死崩溃

实例1（n的阶乘）：
```java
package ProcessControl;
import java.util.Scanner;
public class Demo04 {
    public static void main(String[] args) {
        int i= 1;
        int result = 1;
        Scanner scanner = new Scanner(System.in);
        System.out.println("求几的阶乘？（输入一个正数）");
        int n = scanner.nextInt();
        while(i<=n){
            result *= i;
            i++;
        }
        System.out.println(result);
        scanner.close();
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/while_n的阶乘.png" style="zoom:33%;" />

### do...while循环
* 对于while语句而言，如果不满足条件，则不能进入循环。但有时候我们需要即使不满足条件，也至少执行一次
* do...while循环和while循环相似，不同的是，do...while循环至少会执行一次
```java
do{
	//代码语句
}while(布尔表达式);
```
实例2：
```java
package ProcessControl;
public class Demo05 {
    public static void main(String[] args) {
        int i = 4;
        do {
            i ++;
        }while (i>5);
        //do...while是先执行后判断，保证至少执行一次
        System.out.println(i);
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/do_while.png" style="zoom:50%;" />

这里可以想一想如果i=5，在不改变循环条件的情况下，会出现什么情况？（答案在本文末尾）
* while 和 do...while 的区别：
  * while先判断后执行，do...while 是先执行后判断！
  * do...while总是保证循环体会被至少执行一次！这是他们的主要差别

### for循环
* 虽然所有循环结构都可以用while或者do...while表示，但Java提供了另一个语句——for循环，使一些循环结构变得更加简单
* for循环语句是支持迭代的一种通用结构，是最有效、最灵活的循环结构
* for循环执行的次数是在执行前就确定的，语法格式为：
```java
for(初始化;布尔表达式;更新){
	//代码语句
}
```
关于for循环有以下几点说明：
最先执行初始化步骤。可以声明一种类型，但可初始化一个或多个循环控制变量，也可以是空语句。
然后检测布尔表达式的值，如果为true，循环体被执行；如果为false，循环终止，开始执行循环体后面的语句。
执行一次循环后，更新循环控制变量（迭代因子控制循环变量的增减）
再次检测布尔表达式，循环执行上面的过程
实例3（九九乘法表）：
```java
package ProcessControl;
public class Nine_NineTable {
    public static void main(String[] args) {
        for(int i = 1;i < 10;i++){
            for(int j = 1;j <= i; j++){
                System.out.print(i+"*"+j+" = " + (i*j)+"\t");
            }
            System.out.println();
        }
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/for_ninenine.png" style="zoom:50%;" />

实例4（实心三角形）：
```java
package ProcessControl;
import java.util.Scanner;
public class Triangle_A {
    public static void main(String[] args) {
        System.out.println("您想要打印多少行的实心三角形：");
        Scanner scanner = new Scanner(System.in);
        int a = scanner.nextInt();
        for (int i = 1; i <= a; i++) {
            for (int j = a; j >= i ;j--){
                System.out.print(" ");
            }
            for(int j = 1 ; j<= i ; j++){
                System.out.print("*");
            }
            for (int j = 1 ; j<i ;j++){
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/for_Triangle_A.png" style="zoom:50%;" />

实例5（空心三角形）：
```java
package ProcessControl;
import java.util.Scanner;
public class Triangle {
    public static void main(String[] args) {
        System.out.println("您想要打印多少行的三角形：");
        Scanner scanner = new Scanner(System.in);
        int a = scanner.nextInt();
        int final_row = 2*a - 1;
        System.out.println(final_row);
        for (int i = 1 ; i < a ; i++) {
            for (int j = 1 ; j <= final_row; j++){
                if(j == a-i+1 || j == final_row+i-a){
                    System.out.print("*\t");
                }else{
                    System.out.print("\t");
                }
            }
            System.out.println();
        }
        for(int m = 1;m<=final_row;m++){
            System.out.print("*\t");
        }
        scanner.close();
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/for_triangle.png" style="zoom: 50%;" />

### 增强for循环
* 这里只是先见一面，做个了解，之后数组我们重点使用
* Java5引入了一种主要用于数组或集合的增强型for循环
* Java增强for循环语法格式如下：
```java
for(声明语句：表达式){
	//代码句子
}
```
* 声明语句：声明新的局部变量，该变量的类型必须和数组元素匹配，其作用域限定在循环语句块，其值与此时数组元素的值相等
* 表达式：表达式是要访问的数组名，或者是返回值为数组的方法
在提取数组元素中：
```java
	for(int x:数组名){
		System.out.println(x);
	}
```
实例6：
```java
package ProcessControl;
public class Demo06 {
    public static void main(String[] args) {
        int[] a = {1,2,3,4,5};
        for(int i:a){
            //打印a数组所有的数
            System.out.println(i);
        }
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/增强for循环.png" style="zoom:33%;" />

答案：系统会一直运行下去，虽然i = 5不满足i>5，但是由于do...while结构，要先运行i++后判断，而i++后i = 6满足循环条件，就一直进行循环。