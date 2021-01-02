---
title: ARTS_1
date: 2020-12-27 15:22:38
tags:
  - ARTS
categories:
  - ARTS
---

# ARTS 第一周
## 什么是ARTS
**ARTS** 一个高效学习方法，一个需要持续坚持的方法。ARTS 包含四块的内容：

- **Algorithm**：每周至少做一个 leetcode 的算法题（先从Easy开始，然后再Medium，最后才Hard）。主要是为了编程训练和学习，进行编程训练，如果不训练你看再多的算法书，你依然不会做算法题，看完书后，你需要训练；

- **Review**：主要是为了学习英文，如果你的英文不行，你基本上无缘技术高手。所以，需要你阅读并点评至少一篇英文技术文章，我个人最喜欢去的地方是 Medium（需要梯子，其他的可以社区的官方文档以及论文学习）以及各个公司的技术blog，如Netflix的（30min）；

- **Tip**：主要是为了总结和归纳你在是常工作中所遇到的知识点。学习至少一个技术技巧。你在工作中遇到的问题，踩过的坑，学习的点滴知识（也可以学习【极客时间】上的实用课程）；

- **Share**：主要是为了建立你的影响力，能够输出价值观。分享一篇有观点和思考的技术文章，也可以是技术总结的文章。

ARTS 高效学习需要按周去做，需要持续地坚持下去，这样可以让我们不断去反思、总结、归纳，以便让自己更高效地学习，同时也能让我们更加自律。

## Algorithm
### [整数反转](https://leetcode-cn.com/problems/reverse-integer/)

```java
    private static int inverse(int a) {
      if(a > (Math.pow(2,31)-1) || a < -Math.pow(2,32)){
          System.out.println("输入数据溢出");
          return 0;
      }else {
          int i ;
          ArrayList<Integer> array1 = new ArrayList<>();
          ArrayList<Integer> array2 = new ArrayList<>();
          for(i = 0 ; i < 11; i++) {
              array1.add(i, (int)(a / Math.pow(10, i)));
              if(array1.get(i) == 0)
                  break;
              array2.add(i,array1.get(i) % 10);
              System.out.println(array2.get(i));
          }
          int l = array2.size();
          int sum =0;
          for(i = 0 ; i < l ; i++){
              sum =sum + ((int)(Math.pow(10,(l-1-i)) * array2.get(i)));
              int j = sum / (int)Math.pow(10,(l-1-i)) %10;
              if(j != array2.get(i))                                             //如果溢出直接返回
                  return 0;
              System.out.println(i+"===="+sum+"====="+array2.get(i)*Math.pow(10,(l-1-i)));
          }
          System.out.println(sum);
          return sum;
      }
    }

    private static int inverse2(int x) {
    int res = 0;
    while (x != 0) {
        int t = x % 10;
        int newRes = res * 10 + t;
        //如果数字溢出，直接返回0
        if ((newRes - t) / 10 != res)
            return 0;
        res = newRes;
        x = x / 10;
      }
        return res;
    }

    private static int inverse3(int a){
        long sum  = 0;
        while (a != 0 ){
          sum = sum * 10 + a%10;
          a = a/10;
      }
        return (int)sum == sum?(int)sum:0;
    }
```

这道算法题一共写了3中实现方法，第一种是自己分析调试了两小时左右实现的，后两种是Leetcode上看到的比较简练的java实现。这题对于我来说，主要是反转之后的数是否溢出比较难以判断。

第二种实现方法的思想是：将**输入参数（a）**的个位数作为一个**新的数（b）**的最低位，然后去掉输入参数的个位数得到的**新参数（c）**再作为**输入参数（b）**重复上面的循环知道**c**等于0；其中溢出的判断跟我通过实践得出的算法类似：**b**减去最新加上的个位数对10求商，不等于进入之循环之前的**b**则数据溢出。

第三种实现方法的思想基本一样，但其中有非常巧妙的一点。因为题目规定的溢出范围恰好是int的数据范围，因此他将反转后的数用long来存储，最终通过判断long强制转换成int数据值是否发生变化来判断反转后的数是否溢出。

### [回文数](https://leetcode-cn.com/problems/palindrome-number/)
```java
    private static boolean isPalindrome(int a) {
        if(a < 0){
            return false;
        }else if(a == 0){
            return true;
        }else {
            int sum = 0;
            int b = a;
            while (a != 0){
            sum = sum *10 + a % 10;
            a = a / 10;
        }

        if (sum == b)
            return true;
        else
            return false;
        }
    }
```
### [罗马数字转整数](https://leetcode-cn.com/problems/roman-to-integer/)

```java
    private static int romanToInt(String s) {
    int l = s.length();
    int sum = 0;
    for (int i = 0 ; i < l; i++){
        switch (s.charAt(i)){
            case 'I':
                sum += 1;
                break;
            case 'V':
            {
                sum += 5;
                if(i >= 1 && s.charAt(i-1) == 'I')
                    sum -= 2;
            }
                break;
            case 'X':
            {
                sum += 10;
                if(i >= 1 && s.charAt(i-1) == 'I')
                    sum -= 2;
            }
                break;
            case 'L':
            {
                sum += 50;
                if(i >= 1 && s.charAt(i-1) == 'X')
                    sum -= 20;
            }
                break;
            case 'C':
            {
                sum += 100;
                if(i >= 1 && s.charAt(i-1) == 'X')
                    sum -= 20;
            }
                break;
            case 'D':
            {
                sum += 500;
                if(i >= 1 && s.charAt(i-1) == 'C')
                    sum -= 200;
            }
                break;
            case 'M':
            {
                sum += 1000;
                if(i >= 1 && s.charAt(i-1) == 'C')
                sum -= 200;
            }
                break;
            default:
                break;
            }
        }
        return sum;
    }
```

## Review
[How much math you need for programming](https://lispmachine.wordpress.com/2014/12/05/how-much-math-you-need-for-programming/?utm_source=wanqu.co&utm_campaign=Wanqu+Daily&utm_medium=website)

总结：主要讲了编程与数学之间的关系。告诫程序员一开始不要过于深入的研究数学，先把精力集中在怎样编写更好的程序、怎样在特定的范式中思考、如何更好的创造软件以及理解设计模式等。在编程达到一定水平后，再去研究数学，考虑将数学方法应用到编程解决问题中来，这样能让你更加轻松的解决一些编程中的实际问题。

## Tip

掌握了ninja编译Android项目，基本抛弃了编译速度极慢的make。

## Share
[使用Ninja提升工作项目编译效率](https://www.mocuishle.top/2020/12/26/improve-the-complication-efficiency-of-work-items/)
