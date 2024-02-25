# **学习Markdown**

[TOC]

## 粗体与斜体
  
    两个*是粗体； 
    一个*是斜体；
    三个*是粗体+斜体；
    两个~是删除线。

## 分级标题

        # 一级标题
        ## 二级标题
        依次递增

## 超链接

### 行内式

    这是超链接[review](https://zjuers.com/ "我的C小复习")

### 参考式

### 自动链接

    <http://example.com/>

## 锚点(实现页内跳转)

        ## 0. 目录{#index}

        跳转到[目录]{#index}

## 列表

使用 - + * 都可以表示无序列表

有序列表的话就是数字加上英文句点。

## 分割线

    方法：
    ***
    * * *
    *****
    ---
    ---------

- 一篇文章只能有一种分割线写法
- 行内不能有其他字符

## 引用

在要引用的文本前加上>
> 引用？

引用还可以多层嵌套，在不同级别的引用文本前加上不同数量的>

## 图片

图片的使用与超链接类似，也有行内式和参考式

### 行内式——图片

![哈哈哈](E:\下载\钉钉文件下载 "哈哈哈")

### 参考式——图片

参考式就是当前不给出地址，但给出[标记]，在文章最后统一给出地址

## 表格

学号|姓名|分数
-|-|-
小明|男|75
小红|女|79
小陆|男|92

## 代码

### 行内式——代码

c语言里的函数 `scanf()` 怎么用

### 缩进式

    #include <stdio.h>
    #include <stdlib.h>
    void generateArray(int* p, int n);
    void afterSort(int* p, int n);
    void swip(int* x1, int* x2);
    void bubbleSort(int* p, int n);
    void margeSort(int* p, int L, int R);  void marge(int* p, int L, int mid, int R);
    void quickSort(int* p, int L, int R);
    void insertSort(int* p, int n);

### 六个`表示法

```c
#include <stdio.h>
#include <stdlib.h>
void generateArray(int* p, int n);
void afterSort(int* p, int n);
void swip(int* x1, int* x2);
void bubbleSort(int* p, int n);
void margeSort(int* p, int L, int R);  void marge(int* p, int L, int mid, int R);
void quickSort(int* p, int L, int R);
void insertSort(int* p, int n);
```