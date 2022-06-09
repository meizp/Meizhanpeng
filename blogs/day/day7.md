---
title: Java流程控制Ⅰ
date: 2022-6-7
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Java流程控制 1
### Scanner对象
* 之前我们学的基本语法中我们并没有实现程序和人的交互，但是Java给我们提供了这样一个工具类，我们可以获取用户的输入，我们可以通过Scanner类来获取用户的输入。
* 基本语法
```java
Scanner s = new Scanner(System.in);
```
* 通过Scanner类的next()与nextLine()方法获取输入的字符串，在读取前我们一般需要使用hasNext()与hasNextLine()判断是否还有输入的数据。
* next():
  * 1、一定要读取到有效字符后才可以结束输入
  * 2、对输入有效字符之前遇到的空白，next()方法会自动将其去掉
  * 3、只有输入有效字符后才将其后面输入的空白作为分隔符或者结束符
  * 4、next()不能得到带有空格的字符串。
  实例1（代码）：
```java
package ProcessControl;
import java.util.Scanner;
public class Demo01 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String a = scanner.next();
        //这里以空格符为结束标志，后面的字符都视为无效
        System.out.println(a);
        scanner.close();
    }
}

```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/Scanner_next.png" style="zoom:50%;" />

* nextLine():
  * 1、以Enter为结束符，也就是说nextLine()方法返回的是输入回车之前的所有字符。
  * 2、可以获得空白。
  实例2：
```java
package ProcessControl;
import java.util.Scanner;
public class Demo02 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String a = scanner.nextLine();
        //这里以enter符为结束标志
        System.out.println(a);
        scanner.close();
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/Scanner_nextln.png" style="zoom:50%;" />

注意点：
* Scanner提供了一系列nextXxx()方法，当我们**确定输入的数据类型**时再使用
* Scanner不支持多线程处理，就比如输入一个不合类型的数据后，这个数据会自动顶替下一个输入，BufferedReader则支持
* Scanner输入的一个问题：在Scanner类中如果我们在nextXXX()方法之后调用nextLine()方法，这nextLine()方法不能够从控制台读取任何内容，并且，游标不会进入控制台，它将跳过这一步。
* **java.util.InputMismatchException**：控制台输入类型不匹配！
bug1：
```java
package ProcessControl;
import java.util.Scanner;
public class ScannerBug1 {
    public static void main(String[] args) {
        //Scanner scanner = new Scanner(System.in);
        int i = 0;
        float f = 0.0f;
        Scanner scanner = new Scanner(System.in);//新建立了一个类实例对象，参数为用户输入
        System.out.print("请输入整数数据：");
        if (scanner.hasNextInt()){//判断用户是否输入，是则true，否则false
            i = scanner.nextInt();//用next来获取用户输入的值
            System.out.println("您输入的数据是："+i);
        }else {
            System.out.println("您输入的不是整数");
        }
        System.out.print("请输入小数数据：");
        //如果上述判断有误，则继续执行判断,而不会去执行输入
        if (scanner.hasNextFloat()){
            f = scanner.nextFloat();
            System.out.println("您输入的小数是："+ f);
        }else {
            System.out.println("您输入的不是小数");
        }
        scanner.close();
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/Scanner_bug1.png" style="zoom:50%;" />

bug2：
```java
package ProcessControl;
import java.util.Scanner;
public class ScannerBug2 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("输入字符串：");
        //next访问到空格符的时候自动结束
        String a = scanner.next();
        System.out.println(a);
        System.out.print("输入字符串：");
        //nextLine以enter为结束符，但这里会跳过这一步
        String b = scanner.nextLine();
        System.out.println(b);
        scanner.close();
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/Scanner_bug2.png" style="zoom:50%;" />

### 顺序结构
* Java的基本结构就是顺序结构，除非特别指明，否则就按照顺序一句一句执行
* 顺序结构是最简单的算法结构
* 语句与语句之间，框与框之间是按从上到下的顺序进行的，它是由若干个依次执行的处理步骤组成的，它是任何一个算法都离不开的一种基本算法结构

### 选择结构
* if单选择结构
  * 我们很多时候需要判断一个东西是否可行，然后我们才执行，这样一个过程在程序中用if语句来表示
  * 语法：
```java
  if(布尔表达式){
  //如果布尔表达式为true将执行语句
  //equals:判断字符串是否相等
  }
```
* if双选择结构
  * if-else结构
  * 语法：
```java
  if(布尔表达式){
  //如果布尔表达式的值为true
  }else{
  //如果布尔表达式的值为false
  }
```
* if多选择结构
  * 语法：
```java
	if(布尔表达式1){
  //如果布尔表达式1的值为true执行代码
  }else if(布尔表达式2){
  //如果布尔表达式2的值为true执行代码
  }else if(布尔表达式3){
  //如果布尔表达式3的值为true执行代码
  }else{
  //如果以上布尔表达式的值为false执行代码
  }
```
  实例3：

```java
package ProcessControl;
import java.util.Scanner;
public class Demo03 {
    public static void main(String[] args) {
        System.out.println("输入成绩");
        Scanner scanner = new Scanner(System.in);
        while(scanner.hasNextInt()){
            int score = scanner.nextInt();
            if (score >= 60){
                System.out.println("成绩及格");
            }else{
                System.out.println("成绩不及格");
            }
        }
        scanner.close();
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/if_else.png" style="zoom: 50%;" />

* if注意点：
  * if语句至多有1个else语句，else语句在所有else if语句之后
  * if语句可以有若干个else if语句，它们必须在else语句之前
  * 一旦其中一个else if语句检测到true，其他的else if语句和else语句将自动跳过执行
* 嵌套的if结构
  * 使用嵌套的if...else语句是合法的，也就是说你可以在另一个if或者else if语句中使用if或者else if语句；
  * 语法：
```java
  if(布尔表达式 1){
  	////如果布尔表达式 1的值为true执行代码
  	if（布尔表达式 2){
  		////如果布尔表达式 2的值为true执行代码
  	}
  }
```
* switch多选择结构
  * 多选择结构还有一个实现方式就是switch case语句
  * switch case语句判断一个变量与一系列值中某个值是否相等，每个值称为一个分支。
  * switch语句中的变量类型可以是：
    * byte、short、int或者char
    * 从Java SE7开始
    * switch支持字符串String类型了
    * 同时case标签必须为字符串常量或字面量
```java
switch(expression){
	case value:
		//语句
		break;//可选
	case value:
		//语句
		break;//可选
	//你可以有任意数量的case语句
	default://可选
		//语句
}
```
case穿透现象，switch就是匹配一个具体的值
在执行case语句的时候，会先匹配，匹配成功则返回当前的值，再根据break语句判断是否继续输出，如果没有break语句，则会把后面的全部输出。

实例4(calculator)：
```java
package ProcessControl;
import java.util.Scanner;
public class Calculator {
    public static void main(String[] args) {
        System.out.println("计算器现只支持+-*/四种运算");
        Scanner scanner = new Scanner(System.in);
        //System.out.println("请输入第一个数：");
        int a = scanner.nextInt();
        // System.out.println("请输入操作符：");
        String c = scanner.next();
        //System.out.println("请输入第二个数：");
        int b = scanner.nextInt();
        switch (c){
            case "+":
                System.out.println(a+"+"+b+"="+(a+b));
                break;
            case "-":
                System.out.println(a+"-"+b+"="+(a-b));
                break;
            case "*":
                System.out.println(a+"*"+b+"="+(a*b));
                break;
            case "/":
                System.out.println(a+"/"+b+"="+(a/(double)b));
                break;
            default:
                System.out.println("目前尚未开发！");
        }
        scanner.close();
    }
}
```
运行：
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/switch_case.png" style="zoom:50%;" />