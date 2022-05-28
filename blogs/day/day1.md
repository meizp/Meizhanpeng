---
title: Markdown的使用及vuepress的安装
date: 2022-5-27
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# 学习Markdown

## 标题
### 标题分节只需用#;##;###......
## 字体
### 加粗：
**xx**
### 斜体：
*xx*
### 加粗＋斜体：
***xx***
### 删除：
~~xx~~
## 引用
> xxxxx

## 分割线
---
***
## 图片
![图片名字](图片地址或者链接)

## 超链接
[超链接的名字]()
## 列表
1. 
2. 
* 
* 
## 表格
| x    | x    | x    |
| ---- | ---- | ---- |
|      |      |      |
| x    | x    | x    |
| ---- | ---- | ---- |
|      |      |      |
| x    | x    | x    |
| ---- | ---- | ---- |
|      |      |      |

## 代码
```java

```
# 安装vuepress
[vuepress官网](https://www.vuepress.cn/)
## 步骤一：
安装Node[Nodejs](https://nodejs.org/zh-cn/)
推荐![nodejs](D:\Myproject\xm\my-blog\.vuepress\public\node稳定版.png)
下载开始安装
![node1](D:\Myproject\xm\my-blog\.vuepress\public\node1.png)
一路确认默认安装（可以更改安装目录)
win + R，输入cmd进入控制台（这里建议搜索cmd命令提示符以管理员方式运行）
![cmd](D:\Myproject\xm\my-blog\.vuepress\public\cmd.png)
输入node -v可显示成功安装node和版本号
![node -v](D:\Myproject\xm\my-blog\.vuepress\public\node -v.png)
之后需要更改系统环境配置（安装在别的位置，即非系统默认的位置）
> 在nodejs安装路径下，新建node_global和node_cache两个文件夹，这是npm安装的全局模块所在的路径，以及缓存cache的路径，之所以创建，是因为以后在执行类似：npm install express [-g] （后面的可选参数-g，g代表global全局安装的意思）的安装语句时，会将安装的模块安装到【C:\Users\用户名\AppData\Roaming\npm】路径中，占C盘空间。一般放在了 node的安装目录下。
![创建文件](D:\Myproject\xm\my-blog\.vuepress\public\创建文件.png)
创建好文件，接着刚刚的命令提示符进行操作（按照路径去填写后部分）：
```markdown
npm config set prefix "D:\node\node_global"
npm config set cache "D:\node\node_cache"
```
之后设置环境变量，关闭cmd窗口，打开我的电脑，右键-属性-高级系统设置-高级-环境变量
上半部分是用户变量，点击path一栏
~~C:\Users\用户名\AppData\Roaming\npm~~
修改为D:\node\node_global

![用户变量](D:\Myproject\xm\my-blog\.vuepress\public\用户变量.png)

下半部分是系统变量，在系统变量上添加一项（按照路径）

```markdown
NODE_PATH
D:\node\node_modules
```

![系统变量](D:\Myproject\xm\my-blog\.vuepress\public\系统变量.png)

[剩下的可观看视频来处理]([10分钟教你使用vuepress快速搭建自己的个人博客并部署服务_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1eQ4y1h7E4?spm_id_from=333.788.top_right_bar_window_history.content.click))

其中Windows PowerShell更改为用管理员运行cmd，使用cd命令转换到blog文件。
