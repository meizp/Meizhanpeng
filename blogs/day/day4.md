# Java基础2
### 数据类型扩展
* 整数扩展：进制表示
        二进制0b，十进制，八进制0，十六进制0x(0-9,A-F)
    <img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/整数扩展进制.png" style="zoom:33%;" />
* 浮点数扩展：银行业务怎么表示？钱
                   类：BigDecimal 数学工具类
               <img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/浮点数进阶.png" style="zoom:33%;" />
---
float 有限；离散；舍入误差；大约；接近但不等于
double
最好完全避免使用浮点数进行比较
最好完全避免使用浮点数进行比较
最好完全避免使用浮点数进行比较
这两个关键词是有问题的，会有误差，少用浮点数进行比较

---
* 字符拓展

~~~java
sout((int)变量名)//强制转换
~~~

所有的字符本质都是数字

Unicode编码2个字节U0000 - UFFFF
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/字符扩展.png" style="zoom:33%;" />

转义字符

~~~java
\t //制表符，跳到下一个TAB位置
\n //换行，换到当前位置的下一行，而不会回到行首
\r //回车CR，回到当前行的行首，而不会换到下一行，如果接着输出的话，本行以前的内容会被逐一覆盖
\b //退格BS，将当前位置移到前一列
\" //双引号
\' //单引号
\\ //反斜杠
\xxx  //8进制转义符
\uxxxx //16进制转义符
~~~

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/转义字符.png" style="zoom:33%;" />

字符串

~~~java
String = new String
String = 
二者是不一样的，内存不同
~~~

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/字符串扩充.png" style="zoom:33%;" />

* 布尔值扩展

~~~java
if(flag == true){}
if(flag){}
二者是一样的
//Less is More!代码要精简义读
~~~

### 类型转换
由于Java是强类型语言，所以要进行有些运算的时候的，需要用到类型转换
```java
低 ----------------------------------->高
byte,short,char->int->long->float->double
```
运算中，不同类型的数据先转化为同一类型，然后进行运算
高到低：强制转换  （类型）+变量名
低到高：自动转换
内存溢出
```java
![](https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/数据转换.png)
注意点：
1.不能对布尔值进行转换
2.不能把对象类型转化成不相干的类型
3.在把高容量转换至低容量的时候，强制转换
4.在转换的时候可能存在内存问题，或者精度问题
```
* JDK7新特性，数字之间可以用下划线分割
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/转换数据的bug.png" style="zoom:33%;" />