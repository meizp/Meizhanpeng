# Java基础1
### idea 的快捷键，main方法和输出快捷键
```java
psvm  =  public static void main(String[] ars){}
sout  =  System.out.println()
//print输出不换行，println输出换行
```
* psvm
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/psvm.png" style="zoom:50%;" />
* sout
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/sout.png" style="zoom:50%;" />
* Hello world！
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/Hello world.png" style="zoom: 33%;" />
### Java的注释：

* 单行注释  //    注释
* 多行注释  /*   注释   */
* 文档注释  /**     *    */
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/注释.png" style="zoom: 33%;" />

### 关键词
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/关键字.png" style="zoom:80%;" />

### 标识符
在程序设计语言中，标识符是用作程序的某一元素的名字的字符串或用来标识源程序中某个对象的名字的，这个元素可以是一个语句标号，一个过程或函数、一个数据元素（例如一个标量变量或一个数组）或程序本身。最通常是，标识符这个字几乎与变量名同义地使用。
### 标识符注意点

* 所有的标识符都应该以字母（A-Z或者a-z）或者$或者下划线_开始
* 首字符之后可以是字母（A-Z或者a-z）或者$或者下划线_或数字的任何字符组成
* 不能使用关键字作为变量名或者方法名
* 标识符是大小写敏感的
* 可以使用中文名字，也可以用拼音，但是不建议，很low
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/标识符注意.png" style="zoom:33%;" />
### 数据类型
* 强类型语言：要求变量的使用要严格符合规定，所有变量都必须先定义后才能使用
  * 安全性高，速度慢
* 弱类型语言：变量类型可随时转换
  * 安全性低，效率高
* Java的数据类型
  * 基本类型：数值类型（整数类型，浮点类型，字符类型）
                           boolean类型：True和False
                       <img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/基本数据类型.png" style="zoom:50%;" />
  * 引用类型：类，接口，数组
                       <img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/引用数据类型.png" style="zoom:80%;" />
```java
byte //1个字节：-128-127
short //2个字节：-32768-32767
int //4个字节：-2147483648-2147483647
long //8个字节：-9223372036854775808-9223372036854775807
//long + 变量名 = 数字L，L不能忘
float //4个字节
//float + 变量名 = 小数F，F不能忘
double //8个字节
char //2个字节
//字符是一个字符，是关键词，而字符串String是类，不是关键词
```
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/数据类型.png" style="zoom:33%;" />

### 字节
* 位：是计算机内部数据储存的最小单位，11011100是一个8位二进制的数
* 字节：是计算机中数据处理的基本单位，一个字节是8位，习惯用大写B表示
  * 1B(byte字节) = 8bit(位)
* 字符：是指计算机中使用的字母、数字、字和符号

### 变量
* 变量：就是可以变化的量
* Java是一种强类型的语言，每个变量都必须声明其类型
* Java变量是程序中最基本的存储单元，其要素包括变量名，变量类型和作用域
```java
type varname [=value][{,varname[=value]}];
//数据类型 变量名 = 值，可以用逗号隔开来声明表示多个同类型变量
```

变量对应着一个空间，空间是在内存中，只是空间里存什么不知道，位置确定
注意事项：
* 每个变量都有类型，类型可以是基本类型，也可以是引用类型
* 变量名必须是合法的标识符
* 变量声明是一条完整的语句，因此每一个声明都必须以分号结束


### 变量作用域
* 类变量：static + 从属于类，可以直接用
* 实例变量：从属于对象，方法外类里；如果不自行初始化，则返回这个类型的默认值，调用实例变量的时候需要在方法里面先调用类，再用类调用实例变量
默认值都是0，特殊的布尔值是false，除了基本类型，其余的默认值都是空的
* 局部变量：必须声明和初始化值，且只在该方法里有效
```java
public class Variable{
	static int allClicks = 0;     //类变量
	String str = "hello world";   //实例变量
	public void method(){
		int i = 0;                //局部变量	
	}
}
```
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/变量类型.png" style="zoom:33%;" />

### 常量
常量：初始化后不能再改变值！不会变动的值
所谓常量可以理解成一种特殊的变量，它的值设定后，在程序运行过程中不会被改变
```java
final 常量名 = 值；
```
常量名一般是用大写字符
static修饰符，不存在先后顺序
### 变量名的命名规则
* 所有变量、方法、类名：见名知意
* 类成员变量：首字母小写和驼峰原则：monthSalary
* 局部变量：首字母小写和驼峰原则
* 常量：大写字母和下划线：MAX_VALUE
* 类名：首字母大写和驼峰原则
* 方法名：首字母小写和驼峰原则	