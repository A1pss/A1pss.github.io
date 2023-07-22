---
title: 第三讲：插值算法
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


数据极少，不足以支撑分析的进行时，“模拟产生”一些新的但又比较靠谱的值来满足需求，这就是插值

---

### 插值法的定义
> 设函数![](https://www.zhihu.com/equation?tex=y%3Df%28x%29)在区间![](https://www.zhihu.com/equation?tex=%5Ba%2Cb%5D)上有定义，且已知点![](https://www.zhihu.com/equation?tex=a%5Cleqslant%20x_0%3Cx_1%3C%5Cdots%20%5Cleqslant%20b)上的值分别为：![](https://www.zhihu.com/equation?tex=y_0%2Cy_1%2C%5Cdots%2Cy_n)。若存在以简单函数![](https://www.zhihu.com/equation?tex=P%28x%29)，使![](https://www.zhihu.com/equation?tex=P%28x_i%29%3Dy_i%5C%20%5C%20%28i%3D0%2C1%2C2%2C%5Cdots%2Cn%29)则称![](https://www.zhihu.com/equation?tex=P%28x%29)为![](https://www.zhihu.com/equation?tex=f%28x%29)的插值函数，点![](https://www.zhihu.com/equation?tex=x_0%2Cx_1%2C%5Cdots%2Cx_n)成为插值节点，区间![](https://www.zhihu.com/equation?tex=%5Ba%2Cb%5D)成为插值区间，求插值函数![](https://www.zhihu.com/equation?tex=P%28x%29)的方法称为插值法
> > - 分类:
> >   若![](https://www.zhihu.com/equation?tex=P%28x%29)是![](https://www.zhihu.com/equation?tex=n)次代数多项式，即![](https://www.zhihu.com/equation?tex=P%28x%29%3Da_0%2Ba_1x%2B%5Cdots%2Ba_nx%5En)，就称为多项式插值；
> >   若![](https://www.zhihu.com/equation?tex=P%28x%29)为分段多项式，就称为分段插值；
> >   若![](https://www.zhihu.com/equation?tex=P%28x%29)为三角多项式，就称为三角插值。
> > - 原理:
> >   设有![](https://www.zhihu.com/equation?tex=n%2B1)个互不相同界的节点![](https://www.zhihu.com/equation?tex=%28x_i%2Cy_i%29%5C%20%5C%20%28i%3D0%2C1%2C2%2C%5Cdots%2Cn%29)，则存在**唯一**的多项式：![](https://www.zhihu.com/equation?tex=L_n%28x%29%3Da_0%2Ba_1x%2Ba_2x%5E2%2B%5Cdots%2Ba_nx%5En)使得![](https://www.zhihu.com/equation?tex=L_n%28x_j%29%3Dy_j%5C%20%5C%20%28j%3D0%2C1%2C2%2C%5Cdots%EF%BC%8Cn%29)
> >   *注：如果不限制多项式的次数，插值多项式并不唯一*

### 多项式插值方法
#### 1. 拉格朗日插值法

1. 拉格朗日插值多项式 (![](https://www.zhihu.com/equation?tex=L_n%28x%29)) ：
   
![](https://www.zhihu.com/equation?tex=%0A%20%20%20%5Comega%20_%7Bn%2B1%7D%28x%29%3D%28x-x_0%29%28x-x_1%29%5Cdots%28x-x_n%29%5C%5C%5Comega%20_%7Bn%2B1%7D%27%28x_k%29%3D%28x_k-x_0%29%5Cdots%28x_k-x_%7Bk-1%7D%29%28x_k-x_%7Bk%2B1%7D%29%5Cdots%28x_k-x_n%29%5C%5CL_n%28x%29%3D%5Csum_%7Bk%3D0%7D%5E%7Bn%7D%7By_k%5Cfrac%7B%5Comega%20_%7Bn%2B1%7D%28x%29%7D%7B%28x-x_k%29%5Comega%20_%7Bn%2B1%7D%27%28x_k%29%7D%7D.%0A%20%20%20)


2. 龙格现象：

   高次插值会产生龙格现象，即在两端处波动极大，产生明显的震荡。在不熟悉曲线运动趋势的前提下，不要轻易使用高次插值。

### 分段线性插值方法

#### 2. 分段二次插值 (分段抛物插值) 

- 插值多项式次数高，精度未必显著提高；

  插值多项式次数越高，舍入误差可能显著增大；

  所以采用分段低次插值是一种办法

- 选取跟节点![](https://www.zhihu.com/equation?tex=x)最近的三个节点![](https://www.zhihu.com/equation?tex=x_%7Bi-1%7D%2C%5C%20x_i%2C%5C%20x_%7Bi%2B1%7D)进行二次插值。

  即在每个区间![](https://www.zhihu.com/equation?tex=%5Bx_%7Bi-1%7D%2C%5C%20x_%7Bi%2B1%7D%5D)上，取：
  
![](https://www.zhihu.com/equation?tex=%0A%20%20f%28x%29%5Cthickapprox%20L_2%28x%29%3D%5Csum_%7B%5Csubstack%7Bk%3Di-1%5C%5Cj%5Cneq%20k%7D%7D%5E%7Bi%2B1%7D%5By_k%5Cprod_%7Bj%3Di-1%7D%5E%7Bi%2B1%7D%7B%5Cfrac%7B%28x-x_j%29%7D%7B%28x_k-x_j%29%7D%7D%5D%0A%20%20)



#### 3. 牛顿插值法


![](https://www.zhihu.com/equation?tex=%0Af%28x%29%3Df%28x_0%29%2Bf%5Bx_0%2Cx_1%5D%28x-x_0%29%5C%5C%2Bf%5Bx_0%2Cx_1%2Cx_2%5D%28x-x_0%29%28x-x_1%29%2B%5Cdots%5C%5C%2Bf%5Bx_0%2Cx_1%2C%5Cdots%2Cx_%7Bn-2%7D%2Cx_%7Bn-1%7D%5D%28x-x_0%29%28x-x_1%29%5Cdots%28x-x_%7Bn-3%7D%29%28x-x_%7Bn-2%7D%29%5C%5C%2Bf%5Bx_0%2Cx_1%2C%5Cdots%2Cx_%7Bn-1%7D%2Cx_%7Bn%7D%5D%28x-x_0%29%28x-x_1%29%5Cdots%28x-x_%7Bn-2%7D%29%28x-x_%7Bn-1%7D%29%5C%5C%5C%5Cf%5Bx_0%2Cx_1%2C%5Cdots%2Cx_k%5D%3D%5Cfrac%7Bf%5Bx_1%2C%5Cdots%2Cx_%7Bk-1%7D%2Cx_k%5D-f%5Bx_0%2Cx_1%2C%5Cdots%2Cx_%7Bk-1%7D%5D%7D%7Bx_k-x_0%7D%0A)


*也存在龙格现象的问题*

- 拉格朗日插值法和牛顿插值法的缺点：

  仅仅要求插值多项式在插值节点处与被插函数有相等的函数值，而这种插值多项式却不能全面反映被插值函数的性态。
  
  例如插值函数与被插值函数不能在所有节点处有相同的函数值，或在一个或全部节点上插值多项式与被插函数有相同的低阶甚至高阶的导数值

#### 4. 埃尔米特 (Hermite) 插值

- 优点：既能满足在节点上函数值相等，还要求对应的导数值也相等，甚至高阶导数

- 原理：

  ​		设函数![](https://www.zhihu.com/equation?tex=f%28x%29)在区间![](https://www.zhihu.com/equation?tex=%5Ba%2C%5C%20b%5D)上有![](https://www.zhihu.com/equation?tex=n%2B1)个互异节点![](https://www.zhihu.com/equation?tex=a%3Dx_0%3Cx_1%3CX_2%3C%5Cdots%3Cx_n%3Db)，定义在![](https://www.zhihu.com/equation?tex=%5Ba%2C%5C%20b%5D)上函数![](https://www.zhihu.com/equation?tex=f%28x%29)在节点上满足：
  
![](https://www.zhihu.com/equation?tex=%0A%20%20f%28x_i%29%3Dy_i%2Cf%27%28x_i%29%3Dy_i%27%5C%20%5C%20%28i%3D0%2C1%2C2%2C%5Cdots%2Cn%29%5C%20%5C%20%282n%2B2%E4%B8%AA%E6%9D%A1%E4%BB%B6%29%0A%20%20)

  可唯一确定一个次数不超过![](https://www.zhihu.com/equation?tex=2n%2B1)的多项式![](https://www.zhihu.com/equation?tex=H_%7B2n%2B1%7D%28x%29%3DH%28x%29)满足：
  
![](https://www.zhihu.com/equation?tex=%0A%20%20H%28x_j%29%3Dy_j%2C%5C%20%5C%20H%27%28x_j%29%3Dm_j%5C%20%5C%20%28j%3D0%2C1%2C%5Cdots%2Cn%29.%0A%20%20)

  其余项为：
  
![](https://www.zhihu.com/equation?tex=%0A%20%20R%28x%29%3Df%28x%29-H%28x%29%3D%5Cfrac%7Bf%5E%7B2n%2B2%28%5Cxi%29%7D%7D%7B%282n%2B2%29%21%7D%5Comega%20_%7B2n%2B2%7D%28x%29%0A%20%20)

  
- 分段三次埃尔米特插值

  直接使用Hermite插值得到的多项式次数较高，也存在着龙格现象，因此我们往往采用分段三次Hermite插值多项式 (PCHIP)

  **MATLAB中有内置函数，直接调用：**

  **`p = pchip(x, y, xnew_x)`**

  x是已知的样本点的横坐标，y是一致的样本点的纵坐标，new_x是要插入点的横坐标

#### 5. 三次样条插值

- 设![](https://www.zhihu.com/equation?tex=y%3Df%28x%29)在点![](https://www.zhihu.com/equation?tex=x_0%2Cx_1%2Cx_2%2C%5Cdots%2Cx_n)的值为![](https://www.zhihu.com/equation?tex=y_0%2Cy_1%2Cy_2%2C%5Cdots%2Cy_n)，若函数![](https://www.zhihu.com/equation?tex=S%28x%29)满足下列条件

  (1) ![](https://www.zhihu.com/equation?tex=S%28x_i%29%3Df%28x_i%29%3Dy_i%2C%5C%20%5C%20i%3D0%2C1%2C2%2C%5Cdots%2Cn)

  (2) 在每个子区间![](https://www.zhihu.com/equation?tex=%5Bx_i%2Cx_%7Bi%2B1%7D%5D%28i%3D0%2C1%2C2%2C%5Cdots%2Cn-1%29)上![](https://www.zhihu.com/equation?tex=S%28x%29)是三次多项式

  (3) ![](https://www.zhihu.com/equation?tex=S%28x%29)在![](https://www.zhihu.com/equation?tex=%5Ba%2Cb%5D)上二姐连续可微。

  则称![](https://www.zhihu.com/equation?tex=S%28x%29)为函数![](https://www.zhihu.com/equation?tex=f%28x%29)的三次样条插值函数

- **Matlab有内置的函数：**

  **`p = spline(x, y, new_x)`**

  x是已知的样本点的横坐标，y是一致的样本点的纵坐标，new_x是要插入点的横坐标

- 对比三次埃尔米特插值和三次样条插值：

  三次样条生成的曲线更加光滑。在实际建模中， 由于我们不知道数据的生成过程，因此这两种插值都可以使用。

### n维数据的插值 (代码)

`p = interpn(x1, x2, ..., xn, y, new_x1, new_x2, ..., new_xn, method)`

x1, x2, ..., xn是已知的样本点的横坐标，

y是一致的样本点的纵坐标， 

new_x1, new_x2, ..., new_xn是要插入点的横坐标，

method是要插值的方法：

​	'linear': 线性插值（默认）；

​	'cubic': 三次插值；

​	'spline': 三次样条插值法（最为精准）；

​	'nearest': 最邻近插值算法。
