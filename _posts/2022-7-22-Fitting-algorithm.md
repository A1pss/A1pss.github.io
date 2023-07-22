---
title: 第四讲：拟合算法
layout: post
post-image: "https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722185917433.png"
description: 数学建模算法笔记
tags:
- mathematics modeling
- knowledge
---


> **声明：**
>
> 笔记为本人个人整理，参考清风大佬的视频课件，若有错误请指出。


插值算法如果样本点太多，那么多项式次数过高会造成龙格现象。尽管可以用分段的方法避免这种现象，但当我们更倾向于得到一个确定的曲线，就可以采取拟合。

---

## 最小二乘法

1. 最小二乘法原理

$$
\hat{y}_i=kx_i+b\\\hat{k},\hat{b}=\mathop{arg\min}_{k,b}(\sum_{i=1}^n{(y_i-\hat{y}_i)^2})\\\hat{k}=\frac{n\sum_{i=1}^{n}{x_iy_i}-\sum_{i=1}^{n}{y_i}\sum_{i=1}^{n}{x_i}}{n\sum_{i=1}^{n}{x_i}^2-\sum_{i=1}^{n}{x_i}\sum_{i=1}^{n}{x_i}},\\\hat{b}=\frac{\sum_{i=1}^{n}{x_i}^2\sum_{i=1}^{n}{y_i}-\sum_{i=1}^{n}{x_i}\sum_{i=1}^{n}{x_iy_i}}{n\sum_{i=1}^{n}{x_i}^2-\sum_{i=1}^{n}{x_i}\sum_{i=1}^{n}{x_i}}
$$

*此例设曲线为直线*

求解最小二乘方法详见《拟合, p7》

2. MATLAB求解最小二乘代码

   ```matlab
   %% 在工作区新建x,y变量，将x,y轴数据分别以列向量的形式存入变量x,y
   plot(x,y,'o')
   xlabel('x')
   ylabel('y')
   n = size(x,1);
   k = (n*sum(x.*y)-sum(x)*sum(y))/(n*sum(x.*x)-sum(x)*sum(x))
   b = (sum(x.*x)*sum(y)-sum(x)*sum(x.*y))/(n*sum(x.*x)-sum(x)*sum(x))
   hold on % 继续在之前的图形上来画图形
   grid on % 显示网格线
   
   % 匿名函数的基本用法。
   % handle = @(arglist) anonymous_function
   % 其中handle为调用匿名函数时使用的名字。
   % arglist为匿名函数的输入参数，可以是一个，也可以是多个，用逗号分隔。
   % anonymous_function为匿名函数的表达式。
   % 举个小例子
   %  z=@(x,y) x^2+y^2; 
   %  z(1,2) 
   %   ans =  5
   % fplot函数可用于画出匿名一元函数的图形。
   % fplot(f,xinterval) 将匿名函数f在指定区间xinterval绘图。xinterval =  [xmin xmax] 表示定义域的范围
   
   f=@(x) k*x+b;
   fplot(f,[2.5,7]);
   legend('样本数据','拟合函数','location','SouthEast')
   
   y_hat = k*x+b; % y的拟合值
   SSR = sum((y_hat-mean(y)).^2)  % 回归平方和
   SSE = sum((y_hat-y).^2) % 误差平方和
   SST = sum((y-mean(y)).^2) % 总体平方和
   SST-SSE-SSR   % 5.6843e-14  =   5.6843*10^-14   matlab浮点数计算的一个误差
   R_2 = SSR / SST
   ```

3. 如何评价拟合的好坏？

   拟合优度（可决系数）$R^2$

   总体平方和SST (Total sum of squares): $SST=\sum_{i=1}^n{(y_i-\overline y)^2}$

   误差平方和SSE (The sum of squares due to error): $SSE=\sum_{i=1}^n(y_i-\hat y_i)^2$

   回归平方和SSR (Sum of squares of the regression): $SSR=\sum_{i=1}^n(\hat y_i-\overline y)^2$

   

   可以证明：SST = SSE + SSR (证明过程见《拟合》p10)

   拟合优度：$0\leqslant R^2=\frac{SSR}{SST}=\frac{SST-SSE}{SST}=1-\frac{SSE}{SST}\leqslant 1$ 

   $R^2$越接近1，拟合的越好。

   - （注意：$R^2$只能用于**线性函数**的拟合结果评价）
   - 非线性函数和其他函数（例如复杂的指数函数）比较拟合的好坏时，直接看SSE即可

### 线性函数的介绍

1. 思考：$y=a+bx^2$是线性函数吗？

   答：$y=a+bx^2$是线性函数，可以用$R^2$。因为我们这里所说的线性函数是指对参数为线性（线性于参数）

   - 对变量为线性
   
     $Y$的条件期望值是$X_i$的线性函数也就是回归曲线为直线
   
   - 对参数为线性
   
     $Y$的条件期望$E(Y|X_i)$是参数$\beta$的一个线性函数；
   
     在函数中，参数仅以一次方出现，且不能乘以或除以其他任何的参数，并不能出现参数的复合函数形式，则为对参数为线性，并可以使用$R^2$.

## MATLAB中cftools的使用

![image-20230722143306152](https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143306152.png)

![image-20230722143314980](https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143314980.png)
