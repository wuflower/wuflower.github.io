---
title: ARTS-2
date: 2021-01-10 14:18:11
tags:
  - ARTS
categories:
  - ARTS
---

# ARTS 第二周

## 什么是ARTS
**ARTS** 一个高效学习方法，一个需要持续坚持的方法。ARTS 包含四块的内容：

- **Algorithm**：每周至少做一个 leetcode 的算法题（先从Easy开始，然后再Medium，最后才Hard）。主要是为了编程训练和学习，进行编程训练，如果不训练你看再多的算法书，你依然不会做算法题，看完书后，你需要训练；

- **Review**：主要是为了学习英文，如果你的英文不行，你基本上无缘技术高手。所以，需要你阅读并点评至少一篇英文技术文章，我个人最喜欢去的地方是 Medium（需要梯子，其他的可以社区的官方文档以及论文学习）以及各个公司的技术blog，如Netflix的（30min）；

- **Tip**：主要是为了总结和归纳你在是常工作中所遇到的知识点。学习至少一个技术技巧。你在工作中遇到的问题，踩过的坑，学习的点滴知识（也可以学习【极客时间】上的实用课程）；

- **Share**：主要是为了建立你的影响力，能够输出价值观。分享一篇有观点和思考的技术文章，也可以是技术总结的文章。

ARTS 高效学习需要按周去做，需要持续地坚持下去，这样可以让我们不断去反思、总结、归纳，以便让自己更高效地学习，同时也能让我们更加自律。

## Algorithm

### [最长公共前缀](https://leetcode-cn.com/problems/longest-common-prefix/)

```java
private static String longestCommonPrefix(String[] strs) {
    if(strs == null || strs.length == 0)
        return "";
    String str1 = strs[0];
    for (String str : strs) {
        while (str.indexOf(str1) != 0){
            str1 = str1.substring(0,str1.length()-1);
        }
    }

    return str1;
}
```
在这道算法题的分析过程中，这道题可以将字符串数组中的第一个字符串作为最长公共前缀，然后将这个公共前缀挨个去和数组中的字符串比较：两两比较，找出这两个字符串的最长公共前缀，然后再将这个最长公共前缀去跟数组的下一个字符串进行比较，最后输出的最长公共前缀就是所有字符串的最长公共前缀。

## Review
[Why Java Is Dying](https://medium.com/better-programming/why-java-is-dying-b02b5fd44db9)

确实java的使用率在逐年下降，作者将这归结为Java代码的复杂，以及微服务的狂潮席卷了我们，现在的微服务因为它的易于扩展、高可用性、无需担心并发和多线程、集装箱化带来了可移植性被广泛应用。在我看来，python、Go等语言近几年普及的不断提高、学习的人越来越多，主要就是因为简洁、易学易用，这与作者最后提到的**Keep It Simple, Stupid**是一致的。

## Tip

理清了Android项目中DT的基本结构，`.dtb`和`.dtbo`的区别，以及之前bring up camera时为什么dtsi要这样配置。

## Share

[Android项目Device Tree深入理解(一)](https://www.mocuishle.top/2021/01/05/devicetree/)
