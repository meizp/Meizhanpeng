---
title: Java基础Ⅳ
date: 2022-6-6
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Java基础4
### 包机制
* 为了更好地组织类，Java提供了包机制，用于区别类名的命名空间。
* 包的本质就是文件夹
* 包语句的语法格式是：
```java
package pkg1[.pk2[.pk3...]];
```
* 一般利用公司域名倒置作为包名；
* 为了能够使用某一个包的成员，我们需要在Java程序中明确导入该包。使用“Import”语句可完成此功能
```java
import package1[.package2...].(classname|*);
```
.*是通配符，导入这个包下所有的类

### JavaDoc
* javadoc命令是用来生成自己API文档的
* 参数信息
  * @author 作者名
  * @version 版本号
  * @since 指明需要最早使用的jdk版本
  * @param 参数名
  * @return 返回值情况
  * @throws 异常抛出情况
