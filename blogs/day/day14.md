---
title: Java数组Ⅲ
date: 2022-6-13
sidebar: true
tags:
 - tag1
categories:
 - category1
---
# Java数组 3
### 多维数组
* 多维数组可以看成是数组的数组，比如二维数组就是一个特殊的一维数组，其每一个元素都是一个一维数组。
* 二维数组
```java
dataType[] arrayRefVar[][] = new dataType[arraySize x][arraySize y];
```

实例1：
```java
package com.mei.Array;
public class Demo07 {
    public static void main(String[] args) {
        /*
        a =
        1   2   3   4
        2   4   6   8
        3   6   9   12
         */
        int[][] a = {{1,2,3,4},{2,4,6,8},{3,6,9,12}};
        int[][] b = new int[3][4];
        for (int i = 0; i < b.length; i++) {
            for (int j = 0; j < b[i].length; j++) {
                b[i][j] = (i+1) * (j+1);
            }
        }
        for (int i = 0; i < b.length; i++) {
            for (int j = 0; j < b[i].length; j++) {
                System.out.print(b[i][j] + "\t");
                }
            System.out.println();
        }
    }
}
```

运行：

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/二维数组创建.png" style="zoom: 50%;" />

### Arrays类（建议用类名.静态方法）
* 数组的工具类java.util.Arrays
* 由于数组对象本身并没有什么方法可以供我们调用，但API中提供了一个工具类Arrays供我们使用，从而可以对数据对象进行一些基本的操作
* 查看JDK帮助文档
* 具有以下常用功能：
  * 给数组赋值：通过fill方法
  * 对数组排序：通过sort方法，按升序
  * 比较数组：通过equals方法比较数组中元素值是否相等
  * 查找数组元素：通过binarySearch方法能对排序好的数组进行二分查找法操作

fill操作：fill可以将数组中从哪个位置，到哪个位置的值赋予多少，这个区间是左闭右开，返回值类型是空，也即对原数组进行操作

实例2（fill）：
```java
package com.mei.Array;
import java.util.Arrays;
public class ArrFill {
    public static void main(String[] args) {
        int[] a = new int[5];
        int[] b = {1,2,3,4,5};
        //fill可以将数组中从哪个位置，到哪个位置的值赋予多少，这个区间是左闭右开
        Arrays.fill(a,1);
        Arrays.fill(b,1,3,5);
        for(int i = 0;i<5;i++){
            System.out.print(a[i] + "\t");
        }
        System.out.println();
        for(int i = 0;i<5;i++){
            System.out.print(b[i] + "\t");
        }
    }
}
```

运行：

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/ArrFill.png" style="zoom:50%;" />

sort操作：sort可以将数组中从哪个位置，到哪个位置的值进行排序，这个区间是左闭右开，返回值为空，也即对原数组进行操作

实例3（sort）：
```java
package com.mei.Array;
import java.util.Arrays;
public class ArrSort {
    public static void main(String[] args) {
        int[] a = {2,6,8,5,3,1};
        int[] b = {2,6,8,5,3,1};
        //sort可以将数组中从哪个位置，到哪个位置的值进行排序，这个区间是左闭右开
        Arrays.sort(a);
        Arrays.sort(b,2,6);
        for(int i:a){
            System.out.print(i + "\t");
        }
        System.out.println();
        for(int i:b){
            System.out.print(i + "\t");
        }
    }
}
```

运行：

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/ArrSort.png" style="zoom:50%;" />

equals操作：equals比较两个数组从起始位置到终点位置的值是否相同，返回值类型为boolean

实例4（equals）：
```java
package com.mei.Array;
import java.util.Arrays;
public class ArrEquals {
    public static void main(String[] args) {
        int[] a = {1, 2, 3, 4, 6};
        int[] b = {2, 2, 3, 4, 6};
        //equals比较两个数组从起始位置到终点位置的值是否相同
        boolean equals = Arrays.equals(a,b);
        boolean e = Arrays.equals(a,1,5,b,1,5);
        System.out.println(equals);
        System.out.println(e);
    }
}
```
运行：

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/ArrEquals.png" style="zoom:50%;" />

binarySearch操作：返回值为int类型
* 使用Arrays.binarySearch 一定要记得，先使用Arrays.sort()方法排序。
* 使用二分搜索算法在指定数组中搜索指定对象。在调用之前，数组必须按照其元素的值的升序排序，如果没有排序，则结果是未定义的。eg:数组中包含的元素不具有可比性(例如字符串)，则不能按照元素的自然顺序排序，因此结果未定义。
* 数组包含与指定对象相等的多个元素，则不能保证找到哪个元素，只返回一个值。

实例5（binarySearch）：
```java
package com.mei.Array;
import java.util.Arrays;
public class ArrSearch {
    public static void main(String[] args) {
        int[] a = {1,6,3,4,5};
        char[] a2 = {'a','z','c','e','h'};
        String[] b = {"asd","cda","dsa","as","fds","sc"};
        int[] c = {1,1,2,6,5};
        Arrays.sort(b);//对字符串数组一定要先升序排序再寻找
        int i = Arrays.binarySearch(a, 3);
        int j = Arrays.binarySearch(a2,1,5,'e');
        int k = Arrays.binarySearch(b,"as");
        int z = Arrays.binarySearch(c,1);
        System.out.print(i+"\t");
        System.out.print(j+"\t");
        System.out.println(k);
        System.out.println(z);
    }
}
```
运行：

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/ArrSearch.png" style="zoom:50%;" />

toString操作：toString 返回指定数组的字符串表示形式，返回值类型为字符串

实例6（toString）：
```java
package com.mei.Array;
import java.util.Arrays;
public class ArrToString {
    public static void main(String[] args) {
        //toString 返回指定数组的字符串表示形式
        int[] a = {1,2,3,4,5};
        String[] b = {"asdsa","sdff","gcxv","qwwd"};
        String s = Arrays.toString(a);
        String o = Arrays.toString(b);
        System.out.println(s);
        System.out.println(o);
    }
}
```
运行：

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/ArrToString.png" style="zoom:50%;" />

### 稀疏数组
* 当一个数组中大部分元素为0，或者为同一值的数组时，可以使用稀疏数组来保存该数组。
* 稀疏数组的处理方式是：
  * 记录数组一共有几行几列，有多少个不同值
  * 把具有不同值得元素和列及值记录在一个小规模的数组中，从而缩小程序的规模
* 稀疏数组表示：
  * 第一行代表了这个数组有几行几列有几个不同的值
  * 剩余行代表了不同值所在行列，及不同值的大小

实例7（稀疏数组）：
```java
package com.mei.Arraysort;
import java.util.Arrays;
public class Demo01 {
    public static void main(String[] args) {
        int[][] a = {{0,0,0,0,1},{0,0,0,2,0},{0,0,3,0,0},{0,4,0,0,0},{5,0,0,0,0}};
        int count = 0;
        int dex = 1;
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a[i].length; j++) {
                if(a[i][j] != 0){
                    count ++;
                }
            }
        }
        //System.out.println(count);
        //原始数组转化为稀疏数组
        int[][] b = new int[count + 1][3];
        b[0][0] = a.length;
        b[0][1] = a[0].length;
        b[0][2] = count;
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a[i].length; j++) {
                if(a[i][j] != 0){
                    b[dex][0] = i;
                    b[dex][1] = j;
                    b[dex][2] = a[i][j];
                    dex ++;
                }
            }
        }
        for (int i = 0; i < count; i++) {
            System.out.println(Arrays.toString(b[i]));
        }
        System.out.println("==================");
        //将稀疏数组转化为原始数组
        int[][] c = new int[b[0][0]][b[0][1]];
        for (int i = 0; i < b[0][0]; i++) {
            for (int j = 0; j < b[0][1]; j++) {
                c[i][j] = 0;
            }
        }
        for (int i = 1; i < count+1; i++) {
            c[b[i][0]][b[i][1]] = b[i][2];
        }
        for (int i = 0; i < count; i++) {
            System.out.println(Arrays.toString(c[i]));
        }
        System.out.println("==================");
    }
}
```
运行：

<img src="https://mzp-picture.oss-cn-hangzhou.aliyuncs.com/img/稀疏数组.png" style="zoom:50%;" />