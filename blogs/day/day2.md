---
title: Dos命令
date: 2022-5-28
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Dos命令

```bash
#查看当前目录下的所有文件 dir
#切换主盘的方法 cd + /d + 盘：
#跨盘服的切换目录 cd + /d + 盘:\ + 目录
#返回上一级 cd ..
#清理屏幕 cls
#退出终端 exit
#查看电脑的ip ipconfig
#打开计算机 calc
#打开画图 mspaint
#打开记事本 notepad
#ping 命令
	ping + 网址（可得到网址ip地址）
#创建文件夹 md + 目录名
#创建文件 cd>文件名
#删除文件 del 文件名
#移除目录 rd + 目录名 
```

# Java

JVM虚拟机



## Java的特性

* 简单性
* 面向对象
* 可移植性
* 高性能
* 分布式
* 动态性
* 多线程
* 安全性
* 健壮性

# JDK,JRE,JVM
* **JDK:Java Development Kit Java开发者工具**
* **JRE:Java Runtime Environment Java运行时环境**
* **JVM:HAVA Virtual MAchine Java虚拟机**

# 安装Java
建议下载JDK11为最新的LTS（长期支持）版本，这里官网注册需要访问国外服务器。
### 下载步骤1
[访问官网](https://www.oracle.com/cn/index.html)
注册信息，很简单，填写邮箱，密码，姓名等，然后登录。
### 下载步骤2
跳转到官方下载的JDK下载页面：[官方下载](https://www.oracle.com/java/technologies/downloads/)
找到对应的JDK11版本，我这里是Windows ×64位
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/java.png" style="zoom:50%;" />
后缀exe是应用，后缀zip是压缩包，这里建议exe

### 下载步骤3
默认安装，一路确认，建议不要安装在c盘，建议在其他盘上安装，并一定要记下路径。
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/java路径.png" style="zoom:50%;" />
如图是我安放Java的位置，D:\java即路径。

# 环境配置
电脑右键属性-高级系统设置-环境变量-系统变量
### 配置步骤1
新建
变量名：JAVA_HOME
变量值：路径
<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/java环境变量设置1.png" style="zoom:50%;" />

### 配置步骤2
找到系统变量里path一栏，新建%JAVA_HOME%\bin
![](https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/java环境变量设置2.png)