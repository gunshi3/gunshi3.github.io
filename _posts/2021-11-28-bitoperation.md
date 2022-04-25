---
title: 'Binary Operation'
date: 2021-11-28
permalink: /posts/2021/11/bitoperation/
tags:
  - algorithm
  - leetcode
---

Binary Operation work efficiently sometimes.



## [2 的幂](https://leetcode-cn.com/problems/power-of-two/)

> 给你一个整数 n，请你判断该整数是否是 2 的幂次方。如果是，返回 true ；否则，返回 false 。如果存在一个整数 x 使得 n == 2x ，则认为 n 是 2 的幂次方。
>

方法一：思路与算法

一个数 n 是 2 的幂，当且仅当 n 是正整数，并且 n 的二进制表示中仅包含 1 个 1。因此我们可以考虑使用位运算，将 n 的二进制表示中最低位的那个 1 提取出来，再判断剩余的数值是否为 0 即可。下面介绍两种常见的与「二进制表示中最低位」相关的位运算技巧。

- **skill 1：移除 n 的最低位1**

$$
\texttt{n \& (n - 1)}
$$

该位运算技巧可以直接将 n 二进制表示的最低位 11 移除。

因此，如果 n 是正整数并且 n & (n - 1) = 0，那么 n 就是 2 的幂。

- **skill 2：获取 n 二进制表示的最低位的 1**

$$
\texttt{n \& (-n)}
$$

该位运算技巧可以直接获取 n 二进制表示的最低位的 1。

如果 n 是正整数并且 n & (-n) = n，那么 n 就是 2 的幂。
在一些语言中，位运算的优先级较低，需要注意运算顺序。

- **code**

```c++
class Solution {
public:
    bool isPowerOfTwo(int n) {
        return n > 0 && (n & (n - 1)) == 0;
    }
};

// an error is as following:
return n>0 && (n&(n-1)==0);
```



## [位1的个数](https://leetcode-cn.com/problems/number-of-1-bits/)

> 编写一个函数，输入是一个无符号整数（以二进制串的形式），返回其二进制表达式中数字位数为 '1' 的个数（也被称为[汉明重量](https://baike.baidu.com/item/汉明重量)）。

```c++
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int ret = 0;
        while(n){
            n &= n-1;
            ret ++;
        }
        return ret;
    }
};
```

- 时间复杂度：O(log n)O(logn)。循环次数等于 nn 的二进制位中 11 的个数，最坏情况下 nn 的二进制位全部为 11。我们需要循环 log nlogn 次。

- 空间复杂度：O(1)O(1)，我们只需要常数的空间保存若干变量。

  

## [只出现一次的数字](https://leetcode-cn.com/problems/single-number/)

对于这道题，可使用异或运算⊕。异或运算有以下三个性质。

- 任何数和 0 做异或运算，结果仍然是原来的数，a⊕0=a。
- 任何数和其自身做异或运算，结果是 0，即 a⊕a=0。
- 异或运算满足交换律和结合律，即 a⊕b⊕a=b⊕a⊕a=b⊕(a⊕a)=b⊕0=b。

```cpp
class Solution {
    public int singleNumber(int[] nums) {
        int single = 0;
        for (int num : nums) {
            single ^= num;
        }
        return single;
    }
}
```

- 时间复杂度：O*(*n*)，其中 n*n* 是数组长度。只需要对数组遍历一次。
- 空间复杂度：*O*(1)。



## Operator precedence

- https://en.cppreference.com/w/cpp/language/operator_precedence



## BTW

[What-is-the-difference-between-as-follows-and-as-following?](https://www.quora.com/What-is-the-difference-between-as-follows-and-as-following)

Both terms can be used to introduce a list, but they are different parts of speech.

**As follows** is an adjectival or adverbial phrase which introduces a list which itself functions as an adjectival or an adverbial phrase.

**Example:** *Engine removal is as follows: Step 1…* Here *as follows* and the list function as adjectives, modifying the noun *removal.*

**Example:** *Remove the engine as follows: Step 1…* Here *as follows* and the list are adverbial, modifying the verb *remove*.

**Following** is a gerund (or active participle) which in the present context functions as an adjective.

**Example:** *The following steps for removing the engine can be performed in any well-equipped garage. Step 1…* Here *following* is an adjective, modifying the noun *steps*, which is the subject of the sentence.
