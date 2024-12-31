---
title: 排序算法
cover: 'https://cdn.hatsusakuramiku.cn/hexo/img/gallery/post/1628397182442.webp'
top_img: 'https://cdn.hatsusakuramiku.cn/hexo/img/gallery/post/1628397182442.webp'
tags:
  - 学习
category:
  - HSMK-MATH-LIB
description: 排序算法总结
swiper_index: 1
mathjax: true
comments: false
abbrlink: '735e5788'
---
{% note info flat %}**封面图片PID：[1628397182442](https://www.pixiv.net/artworks/1628397182442)**{% endnote %}
>**HSMKのMathematical Library 导航栏**
>
> [排序算法](/posts/735e5788.html)
>
---

&emsp;&emsp;排序算法是计算机程序设计中的一种基础算法，用于将一组数据按照一定的顺序进行排列。排序算法在许多领域都有广泛的应用，如数据库管理系统、数据挖掘、机器学习等。在完善我的项目[hsmk-mathematical-library](https://github.com/hatsusakuramiku/hsmk-mathematical-library)过程中，不可避免地要求实现一种或多种排序算法，就以本文作为项目实现的排序算法的详细文档。本文将介绍几种常见的排序算法，包括冒泡排序、选择排序、插入排序、快速排序、归并排序、堆排序、希尔排序、基数排序等。

## 1. 冒泡排序

### 定义

经典的冒泡排序{% referto '[1]', '冒泡排序' %}是一种较易理解和实现的排序算法，由于在算法的执行过程中，较小的元素像是气泡般慢慢「浮」到数列的顶端，故叫做冒泡排序。

### 过程

它的工作原理是每次检查相邻两个元素，如果前面的元素与后面的元素满足给定的排序条件，就将相邻两个元素交换。当没有相邻的元素需要交换时，排序就完成了。对于 $n$ 个元素的数列，经过 $i$ 次扫描后，数列的末尾 $i$ 项必然是最大的$i$项，因此冒泡排序最多需要扫描 $n-1$ 遍数组就能完成排序。
一个简单的示意图如下:
![冒泡排序](https://cdn.hatsusakuramiku.cn/hexo/img/mathLib/C/sort/bubbleSort.gif)

### 性质

在序列完全有序时，冒泡排序只需遍历一遍数组，不用执行任何交换操作，时间复杂度为 $O(n)$ 。

在最坏情况下，冒泡排序要执行 $\frac{n(n-1)}{2}$ 次交换操作，时间复杂度为 $O(n^2)$ 。

冒泡排序的平均时间复杂度为 $O(n^2)$ 。

| 算法 | 时间复杂度 | 空间复杂度 | 稳定性|
| --- | --- | --- | --- |
| 冒泡排序 | $O(n^2)$ | $O(1)$ | 稳定 |

### 代码实现

#### {% bubble 伪代码, "采用类C格式，数组下标从0开始", "#39c5bb" %}

$$
\begin{array}{ll}\\
1 & \textbf{Input. } \text{An array } A \text{ consisting of }n\text{ elements.} \\
2 & \textbf{Output. } A\text{ will be sorted in nondecreasing order stably.} \\
3 & \textbf{Method. }  \\
4 & \textbf{for }i\gets0\textbf{ to }n-1\\
5 & \qquad\textbf{for }j\gets0\textbf{ to }n-1-i\\
6 & \qquad\qquad\textbf{if }A[j]>A[j+1]\\
7 & \qquad\qquad\qquad \text{Swap } A[j]\text{ and }A[j+1]
\end{array}
$$

{% tabs tab1, -1 %}

<!-- tab C/C++ -->
```C/C++
/**
 * @brief 冒泡排序算法的简单实现
 * @param arr 将要被排序的数组
 * @param arrLen 数组的长度
 */
void bubbleSort(int *arr, int arrLen){
  /**
   * 遍历数组，并比较相邻元素
   * 如果元素顺序不正确，交换它们
   */
  for(int i = 0; i < arrLen; i++){
    for (int j = 0; j < arrLen - i - 1 ; j++){
      if (arr[j] > arr[j + 1]) {
        int temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }
  }
}

/**
 * @brief 使用无符号指针实现类泛型的冒泡排序
 * @param arr 将要被排序的数组
 * @param arrlen 数组的长度
 * @param arrElemSize 数组中每个元素的大小
 * @param cmp 比较函数
 */
void bubbleSort(void* arr, size_t arrlen, size_t arrElemSize, int (*cmp)(const void*, const void*)){
  /**
   * 遍历数组，并比较相邻元素
   * 如果元素顺序不正确，交换它们
   */
    for (size_t i = 0; i < elemNum; i++) {
        for (size_t j = 0; j < elemNum - 1 - i; j++) {
            if (cmp((char *) array + j * elemSize, (char *) array + (j + 1) * elemSize) > 0) {
                memswap((char *) array + j * elemSize, (char *) array + (j + 1) * elemSize, elemSize);
            }
        }
    }
}

/**
 * @brief 交换两个内存块的内容
 * @param a 第一个内存块
 * @param b 第二个内存块
 * @param size 内存块的大小
 */
void memswap(void* a, void* b, size_t size){
  enum{
    SWAP_GENERIC_SIZE = 32
  };
  while(size > 32){
    unsigned char* temp[SWAP_GENERIC_SIZE];
    memcpy(temp, a, SWAP_GENERIC_SIZE);
    a = mempcpy(a, b, SWAP_GENERIC_SIZE);
    b = mempcpy(b, temp, SWAP_GENERIC_SIZE);
    size -= SWAP_GENERIC_SIZE;
  }
  while(n > 0){
    const unsigned char t = ((unsigned char*)a)[--n];
    ((unsigned char*)a)[n] = ((unsigned char*)b)[n];
    ((unsigned char*)b)[n] = t;
  }
}
```
<!-- endtab -->
<!-- tab java-->
<!-- endtab -->
<!-- tab python-->
<!-- endtab -->
{% endtabs %}

有许多人对冒泡排序做了相当的改进/优化，简要介绍几种常见的优化方法{% referto '[2]', '胡伟东.冒泡排序算法的几种优化与变形[J].电脑编程技巧与维护, 2023(4):51-53.' %}。

{% tabs tab2, -1 %}
<!-- tab 标志法 -->
在排序过程中可能出现排序未完成但待排序数组已经有序的情况，在这种情况下再使用冒泡排序并不会出现元素交换的情况。所以可以设置一个标志变量，在一次排序过程中，若发生了交换，就改变标志变量的值，否则就不变。完成一次排序后，如果标志变量的值不变，说明数组已经有序，可以退出排序。

伪代码如下:
$$
\begin{array}{ll}\\
1 & \textbf{Input. } \text{An array } A \text{ consisting of }n\text{ elements.} \\
2 & \textbf{Output. } A\text{ will be sorted in nondecreasing order stably.} \\
3 & \textbf{Method. }  \\
4 & \textbf{for }i\gets0\textbf{ to }n-1\\
5 & \qquad flag = false\\
6 & \qquad\textbf{for }j\gets0\textbf{ to }n-1-i\\
7 & \qquad\qquad\textbf{if }A[j]>A[j+1]\\
8 & \qquad\qquad\qquad\text{Swap } A[j]\text{ and }A[j+1]\\
9 & \qquad\qquad\qquad flag = true\\
10 & \qquad\textbf{if }flag = true\\
11 & \qquad\qquad\textbf{break}
\end{array}
$$
<!-- endtab -->

<!-- tab 区间控制法法 -->
考虑序列[2, 3, 4, 5, 9, 8, 7]，采用“上冒”，第一轮排序结束后为[2, 3, 4, 5, 8, 7, 9]。可以发现，当 7 和 9 交换位置后，后续的数字都没有互换，即在后续的排序中[2, 3, 4, 5]不需要参与排序。得出结论：每轮遍历的区间边界都是由上一轮遍历最后一次发生交换的位置决定的。这样一来，可以引入标记变量last记录每轮排序最后一次交换的位置，并将last赋给下一轮遍历区间的终点。大大缩小了下一轮排序遍历区间，快速收缩待排序范围，从而提高了算法效率。

伪代码如下:

$$
\begin{array}{ll}\\
1 & \textbf{Input. } \text{An array } A \text{ consisting of }n\text{ elements.} \\
2 & \textbf{Output. } A\text{ will be sorted in nondecreasing order stably.} \\
3 & \textbf{Method. }  \\
4 & \textbf{for }i\gets0\textbf{ to }n-1\\
5 & \qquad last = 0\\
6 & \qquad\textbf{for }j\gets0\textbf{ to }n-1-i\\
7 & \qquad\qquad\textbf{if }A[j]>A[j+1]\\
8 & \qquad\qquad\qquad\text{Swap } A[j]\text{ and }A[j+1]\\
9 & \qquad\qquad\qquad last = j\\
10 & \qquad\textbf{if }last = 0\\
11 & \qquad\qquad\textbf{break}
\end{array}
$$
<!-- endtab -->
<!-- tab 双向冒泡法 -->
<!-- endtab -->
<!-- tab 分组冒泡法 -->
<!-- endtab -->
{% endtabs %}

## <center><p>参考文献</p></center>

{% referfrom '[1]', '冒泡排序','https://oi-wiki.org/basic/bubble-sort/' %}
{% referfrom '[2]', '[2]胡伟东.冒泡排序算法的几种优化与变形[J].电脑编程技巧与维护, 2023(4):51-53.', 'https://www.nstl.gov.cn/paper_detail.html?id=e011007a7dd58fb9d64b7d9641e0a1fb' %}
