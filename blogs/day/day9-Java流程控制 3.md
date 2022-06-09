---
title: Java流程控制Ⅲ
date: 2022-6-9
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Java流程控制 3
### break continue
* break在任何循环语句的主体部分，均可用break控制循环的流程。break用于强行退出循环，不执行循环中剩余的语句。（break语句也在switch语句中使用）
* continue语句用在循环语句中，用来终止某次循环，即跳过循环体中尚未执行的语句，接着进行下一次是否执行循环的判定。
* 关于goto关键字
  * goto关键字很早就在程序设计语言中出现。尽管goto仍是Java的一个保留字，但并未在语言中得到正式使用；Java没有goto。然而，在break和continue这两个关键字的身上，我们仍然能看出一些goto的影子--带标签的break和continue。
  * “标签”是指后面跟一个冒号的标识符，如：label:
  * 对Java来说唯一用到标签的地方是在循环语句之前。而在循环之前设置标签的唯一理由是：我们希望在其中嵌套另一个循环，由于break和continue关键字通常只中断当前循环，但若随同标签使用，它们就会中断到存在标签的地方。