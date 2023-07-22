---
title: 第六讲 ：典型相关分析
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


典型相关分析(Canonical Correlation analysis)是研究两组变量(每组变量中都可能有多个指标)之间相关关系的一种多元统计方法。它能够揭示出两组变量之间的内在联系。

> 温馨提示：这一讲涉及到多元统计的知识，如果对原理听不懂也没有关系，等以后学完了主成分分析模型后再回过头来看比较合适。

---

## 数学原理

### 典型相关的基本理论

#### 典型相关分析的基本思想(略)

假设两组变量分别为: 

![](https://www.zhihu.com/equation?tex=%0AX%5E%7B%281%29%7D%3D%28X_1%5E%7B%281%29%7D%2CX_2%5E%7B%281%29%7D%2C%5Ccdots%2CX_p%5E%7B%281%29%7D%29%2C%5C%20X%5E%7B%282%29%7D%3D%28X_1%5E%7B%282%29%7D%2CX_2%5E%7B%282%29%7D%2C%5Ccdots%2CX_q%5E%7B%282%29%7D%29%0A)

分别在两组变量中选取若干有代表性的综合变量 ![](https://www.zhihu.com/equation?tex=U_i%2CV_i)，使得，每一个综合变量是原变量的线性组合，即

![](https://www.zhihu.com/equation?tex=%0AU_i%3Da_1%5E%7B%28i%29%7DX_1%5E%7B%281%29%7D%2Ba_2%5E%7B%28i%29%7DX_2%5E%7B%281%29%7D%2B%5Ccdots%2Ba_p%5E%7B%28i%29%7DX_p%5E%7B%281%29%7D%5Ctriangleq%20a%5E%7B%28i%29%27%7DX%5E%7B%281%29%7D%5C%5CV_i%3Db_1%5E%7B%28i%29%7DX_1%5E%7B%282%29%7D%2Bb_2%5E%7B%28i%29%7DX_2%5E%7B%282%29%7D%2B%5Ccdots%2Bb_q%5E%7B%28i%29%7DX_q%5E%7B%282%29%7D%5Ctriangleq%20b%5E%7B%28i%29%27%7DX%5E%7B%282%29%7D%0A)

第一组在![](https://www.zhihu.com/equation?tex=var%28U_1%29%3Dvar%28V_1%29%3D1)满足的条件下，找到![](https://www.zhihu.com/equation?tex=a%5E%7B%281%29%7D)和![](https://www.zhihu.com/equation?tex=b%5E%7B%281%29%7D)两组系数，使得![](https://www.zhihu.com/equation?tex=%5Crho%28U_1%2CV_1%29)最大。

被选出的线性组合称为**典型变量**，他们的相关系数称为**典型相关系数**。

还需要保证两组的信息不相关:

![](https://www.zhihu.com/equation?tex=%0Acov%28U_1%2CU_2%29%3Dcov%28V_1%2CV_2%29%3D0%0A)


> 注: 综合变量的组数是不确定的，如果第一组就能代表原数据样本大部分的信息，那么一组就够。
>

#### 典型相关分析原理及方法(详)

- 设有两组随机变量，![](https://www.zhihu.com/equation?tex=X%5E%7B%281%29%7D)代表第一组的p个变量，![](https://www.zhihu.com/equation?tex=X%5E%7B%282%29%7D)代表第二组的q个变量，假设![](https://www.zhihu.com/equation?tex=p%5Cleqslant%20q)。令
  

![](https://www.zhihu.com/equation?tex=%0A%20%20Cov%28X%5E%7B%281%29%7D%29%3D%5CSigma_%7B11%7D%2C%5C%5CCov%28X%5E%7B%282%29%7D%29%3D%5CSigma_%7B22%7D%2C%5C%5CCov%28X%5E%7B%281%29%7D%2CX%5E%7B%282%29%7D%29%3D%5CSigma_%7B12%7D%3D%5CSigma_%7B21%7D%27%5C%5C%5Ctherefore%20Cov%28X%2CX%29%3D%5Cbegin%7Bbmatrix%7D%20%5Cmathop%7B%5CSigma_%7B11%7D%7D%20%5Climits_%7B%28p%5Ctimes%20p%29%7D%20%26%20%5Cmathop%7B%5CSigma_%7B12%7D%7D%20%5Climits_%7B%28p%5Ctimes%20p%29%7D%20%5C%5C%20%5Cmathop%7B%5CSigma_%7B21%7D%7D%20%5Climits_%7B%28p%5Ctimes%20p%29%7D%20%26%20%5Cmathop%7B%5CSigma_%7B22%7D%7D%20%5Climits_%7B%28p%5Ctimes%20p%29%7D%20%5Cend%7Bbmatrix%7D%0A%20%20)


- 设两组变量的线性组合分别为：
  

![](https://www.zhihu.com/equation?tex=%0A%20%20U%3Da_1X_1%5E%7B%281%29%7D%2Ba_2X_2%5E%7B%281%29%7D%2B%5Ccdots%2Ba_pX_p%5E%7B%281%29%7D%5Ctriangleq%20a%27X%5E%7B%281%29%7D%5C%5CV%3Db_1X_1%5E%7B%282%29%7D%2Bb_2X_2%5E%7B%282%29%7D%2B%5Ccdots%2Bb_qX_q%5E%7B%282%29%7D%5Ctriangleq%20b%27X%5E%7B%282%29%7D%0A%20%20)

  易见

![](https://www.zhihu.com/equation?tex=%0A%20%20D%28U%29%3DD%28a%27X%5E%7B%281%29%7D%29%3Da%27Cov%28X%5E%7B%281%29%7D%2CX%5E%7B%281%29%7D%29a%3Da%27%5CSigma_%7B11%7Da%3D1%5C%5CD%28V%29%3DD%28b%27X%5E%7B%282%29%7D%29%3Db%27Cov%28X%5E%7B%282%29%7D%2CX%5E%7B%282%29%7D%29b%3Db%27%5CSigma_%7B11%7Db%3D1%5C%5CCov%28U%2CV%29%3Da%27Cov%28X%5E%7B%281%29%7D%2CX%5E%7B%282%29%7D%29b%3Da%27%5CSigma_%7B12%7Db%5C%5CCorr%28U%2CV%29%3D%5Cfrac%7BCov%28U%2CV%29%7D%7B%5Csqrt%7BD%28U%29%7D%5Csqrt%7BD%28V%29%7D%7D%3D%5Cfrac%7Ba%27%5CSigma_%7B12%7Db%7D%7B%5Csqrt%7Ba%27%5CSigma_%7B11%7Da%7D%5Csqrt%7Bb%27%5CSigma_%7B22%7Db%7D%7D%0A%20%20%5C%5C%5Ctherefore%20Corr%28U%2CV%29%3Da%27%5CSigma_%7B12%7Db%0A%20%20)


- 问题就变成在U和V的方差为一的约束条件下，求使![](https://www.zhihu.com/equation?tex=Corr%28U%2CV%29%3Da%27%5CSigma_%7B12%7Db)达到最大的系数向量a与b。

- 根据条件极值的求法引入Lagrange乘数，将问题转化为求
  

![](https://www.zhihu.com/equation?tex=%0A%20%20%5Cphi%28a%2Cb%29%3Da%27%5CSigma_%7B12%7Db-%5Cfrac%7B%5Clambda%7D%7B2%7D%28a%27%5CSigma_%7B11%7Da-1%29-%5Cfrac%7B%5Cnu%7D%7B2%7D%28b%27%5CSigma_%7B22%7Db-1%29%0A%20%20)

  的极大值，其中![](https://www.zhihu.com/equation?tex=%5Clambda%2C%5Cnu)是Lagrange乘数。

- 根据求极值的必要条件得![](https://www.zhihu.com/equation?tex=%5Ccases%7B%5Cfrac%7B%5Cpartial%5Cphi%7D%7B%5Cpartial%20a%7D%3D%5CSigma_%7B12%7Db-%5Clambda%5CSigma_%7B11%7Da%3D0%5C%5C%5Cfrac%7B%5Cpartial%5Cphi%7D%7B%5Cpartial%20a%7D%3D%5CSigma_%7B21%7Db-%5Clambda%5CSigma_%7B22%7Da%3D0%7D)
  

![](https://www.zhihu.com/equation?tex=%0A%20%20%5CRightarrow%20%5Ccases%7B%5CSigma_%7B12%7Db-%5Clambda%5CSigma_%7B11%7Da%3D0%5C%5C%5CSigma_%7B21%7Db-%5Clambda%5CSigma_%7B22%7Da%3D0%7D%0A%20%20)


  > [常用的向量矩阵求导公式](https://blog.csdn.net/lipengcn/articla/details/52815429)

- 假定个随机变量协差阵的逆矩阵存在，得：
  

![](https://www.zhihu.com/equation?tex=%0A%20%20%5Ccases%7B%28%5CSigma_%7B11%7D%5E%7B-1%7D%5CSigma_%7B12%7D%5CSigma_%7B22%7D%5E%7B-1%7D%5CSigma_%7B21%7D-%5Clambda%5E2I_p%29a%3D0%20%5C%5C%20%28%5CSigma_%7B22%7D%5E%7B-1%7D%5CSigma_%7B21%7D%5CSigma_%7B11%7D%5E%7B-1%7D%5CSigma_%7B12%7D-%5Clambda%5E2I_q%29b%3D0%7D%0A%20%20)

  令![](https://www.zhihu.com/equation?tex=A%3D%5CSigma_%7B11%7D%5E%7B-1%7D%5CSigma_%7B12%7D%5CSigma_%7B22%7D%5E%7B-1%7D%5CSigma_%7B21%7D)， ![](https://www.zhihu.com/equation?tex=B%3D%5CSigma_%7B22%7D%5E%7B-1%7D%5CSigma_%7B21%7D%5CSigma_%7B11%7D%5E%7B-1%7D%5CSigma_%7B12%7D)  (其中A为p\*p阶矩阵，B为q\*q阶矩阵)

  其中![](https://www.zhihu.com/equation?tex=%5Clambda%5E2)为A和B的特征根，a,b则是对应的特征向量。

- 因为![](https://www.zhihu.com/equation?tex=%5Clambda%3Da%27%5CSigma_%7B12%7Db%3DCorr%28U%2CV%29)，求Corr(U,V)最大值也就是求![](https://www.zhihu.com/equation?tex=%5Clambda)的最大值，也就是求A和B得最大特征根的开平方

  可证明：A和B具有相同非零特征根，且所有特征根非负，位于0~1之间

- 因此，我们得到 ![](https://www.zhihu.com/equation?tex=a%5E%7B%281%29%7D%3D%28a_1%5E%7B%281%29%7D%2Ca_2%5E%7B%281%29%7D%2C%5Ccdots%2Ca_p%5E%7B%281%29%7D%29%2C%5C%20a%5E%7B%282%29%7D%3D%28a_1%5E%7B%282%29%7D%2Ca_2%5E%7B%282%29%7D%2C%5Ccdots%2Ca_q%5E%7B%282%29%7D%29) 就是所求的典型变量的系数向量，我们称
  

![](https://www.zhihu.com/equation?tex=%0A%20%20U_1%3Da%5E%7B%281%29%27%7DX%5E%7B%281%29%7D%3Da_1%5E%7B%281%29%7DX_1%5E%7B%281%29%7D%2Ba_2%5E%7B%281%29%7DX_2%5E%7B%281%29%7D%2B%5Ccdots%2Ba_p%5E%7B%281%29%7DX_p%5E%7B%281%29%7D%5C%5CV_1%3D%20b%5E%7B%281%29%27%7DX%5E%7B%282%29%7D%3Db_1%5E%7B%281%29%7DX_1%5E%7B%282%29%7D%2Bb_2%5E%7B%281%29%7DX_2%5E%7B%282%29%7D%2B%5Ccdots%2Bb_q%5E%7B%281%29%7DX_q%5E%7B%282%29%7D%0A%20%20)

  为第一对典型变量，最大特征根的平方根![](https://www.zhihu.com/equation?tex=%5Clambda_1)即为两典型变量的相关系数，我们称其为第一典型相关系数。

- 如果第一典型变量不足以代表两组原始变量的信息，则需要第二对典型变量除需要满足![](https://www.zhihu.com/equation?tex=D%28U_2%29%3DD%28V_2%29%3D1)外，还要增加约束条件: ![](https://www.zhihu.com/equation?tex=cov%28U_1%2CU_2%29%3Dcov%28V_1%2CV_2%29%3D0)

  那么![](https://www.zhihu.com/equation?tex=%5Clambda_2)为第二典型相关系数，对相应的![](https://www.zhihu.com/equation?tex=U_2%3Da%5E%7B%282%29%27%7DX%5E%7B%281%29%7D%2C%5C%20V_2%3Db%5E%7B%282%29%27%7DX%5E%7B%282%29%7D)为第二对典型变量。

  类似的，一次可求出第r对典型变量和典型相关系数。

### 样本典型相关分析

#### 典型相关系数的显著性检验

1. (在论文中直接说)假设![](https://www.zhihu.com/equation?tex=%5Cbegin%7Bbmatrix%7D%20X%5E%7B%281%29%7D%20%5C%5C%20X%5E%7B%282%29%7D%20%5Cend%7Bbmatrix%7D)服从正态分布![](https://www.zhihu.com/equation?tex=N_%7Bp%2Bq%7D%28%5Cmu%2C%5CSigma%29)，从该总体中抽取样本容量为n的样本，得到下列数据矩阵：
   

![](https://www.zhihu.com/equation?tex=%0A%20%20%20X%5E%7B%281%29%7D%3D%5Cbegin%7Bbmatrix%7D%20X_%7B11%7D%5E%7B%281%29%7D%20%26%20X_%7B12%7D%5E%7B%281%29%7D%20%26%20%5Ccdots%20%26%20X_%7B1p%7D%5E%7B%281%29%7D%20%5C%5C%20X_%7B21%7D%5E%7B%281%29%7D%20%26%20X_%7B22%7D%5E%7B%281%29%7D%20%26%20%5Ccdots%20%26%20X_%7B2p%7D%5E%7B%281%29%7D%20%5C%5C%20%5Cvdots%20%26%20%5Cvdots%20%26%20%5Cddots%20%26%20%0A%20%20%20%5Cvdots%20%5C%5C%20X_%7Bn1%7D%5E%7B%281%29%7D%20%26%20X_%7Bn2%7D%5E%7B%281%29%7D%20%26%20%5Ccdots%20%26%20X_%7Bnp%7D%5E%7B%281%29%7D%20%5Cend%7Bbmatrix%7D%0A%20%20%20)



![](https://www.zhihu.com/equation?tex=%0A%20%20%20X%5E%7B%282%29%7D%3D%5Cbegin%7Bbmatrix%7D%20X_%7B11%7D%5E%7B%282%29%7D%20%26%20X_%7B12%7D%5E%7B%282%29%7D%20%26%20%5Ccdots%20%26%20X_%7B1p%7D%5E%7B%282%29%7D%20%5C%5C%20X_%7B21%7D%5E%7B%282%29%7D%20%26%20X_%7B22%7D%5E%7B%282%29%7D%20%26%20%5Ccdots%20%26%20X_%7B2p%7D%5E%7B%282%29%7D%20%5C%5C%20%5Cvdots%20%26%20%5Cvdots%20%26%20%5Cddots%20%26%20%0A%20%20%20%5Cvdots%20%5C%5C%20X_%7Bn1%7D%5E%7B%282%29%7D%20%26%20X_%7Bn2%7D%5E%7B%282%29%7D%20%26%20%5Ccdots%20%26%20X_%7Bnp%7D%5E%7B%282%29%7D%20%5Cend%7Bbmatrix%7D%0A%20%20%20)


2. (不是必须的，3中有重复步骤)在典型相关分析时，就两组变量得相关性进行检验。即检验假设
   

![](https://www.zhihu.com/equation?tex=%0A%20%20%20H_0%3ACorr%28U%2CV%29%3D0%2C%5C%20H_1%3ACorr%28U%2CV%29%5Cneq%200%0A%20%20%20)

   p值小于0.05(0.1)表示在95%(90%)的置信水平下拒绝原假设，即认为两组变量有关。

3. 对典型相关系数进行检验。检验假设为：
   

![](https://www.zhihu.com/equation?tex=%0A%20%20%20H_0%3A%5Clambda_%7Bk%2B1%7D%3D%5Clambda_%7Bk%2B2%7D%3D%5Ccdots%3D%5Clambda_r%5C%5CH_1%3A%5Clambda_%7Bk%2B1%7D%5Cneq%200%0A%20%20%20)

   这个检验假设是一个递推的过程，首先看![](https://www.zhihu.com/equation?tex=%5Clambda_%7Bk%2B1%7D)是否等于0，不等于再检验![](https://www.zhihu.com/equation?tex=%5Clambda_%7Bk%2B2%7D)，以此类推，直到遇到等于0的典型相关系数就停止。

   判断![](https://www.zhihu.com/equation?tex=%5Clambda)是否等于0的方法是看它对应的p值

#### 利用标准化后的典型相关变量分析问题

在典型相关分析之前应先对数据做标准化交换处理。经标准化变换之后的协差阵就是相关系数矩阵，因而，也即通常应从相关矩阵出发进行典型相关分析。

#### 典型载荷分析

指原始变量与典型变量之间相关性分析。

典型载荷和典型变量对应的相关系数的区别?

#### 冗余分析

计算前r个典型变量对样本总方差的贡献，即已解释的方差比例。

由自身几个典型变量解释的方差比例算法：

第一典型变量解释的方差比例![](https://www.zhihu.com/equation?tex=%3D%28%5Cfrac%7B%5Csum%7B%E7%AC%AC%E4%B8%80%E5%85%B8%E5%9E%8B%E5%8F%98%E9%87%8F%E4%B8%AD%E7%9A%84%E5%8F%98%E9%87%8F%5E2%7D%7D%7B%E7%AC%AC%E4%B8%80%E5%85%B8%E5%9E%8B%E5%8F%98%E9%87%8F%E4%B8%AD%E5%8F%98%E9%87%8F%E7%9A%84%E4%B8%AA%E6%95%B0%28p%2Cq%29%7D%29)

第二、第三等典型变量解释的方差比例计算方法同上

## SPSS操作

1. 导入数据

   文件-导入数据(一般选择Excel)

2. 检验数据类型

   点击左下角<kbd>变量视图</kbd> ，在“测量”列将数据类型调整

   标度：数字型，例如身高，体重等

   有序：有序的分类变量，例如甲乙丙丁，优良差

   名义：没有顺序的分类变量，例如男女

3. 运行典型相关分析

   分析-相关-典型相关性，将数据移动到对应的集合

4. 导出数据结果

   文件-导出，一般保存为WordRTF(*.doc)类型，文件名行为保存位置

5. 对结果进行分析

   - 得到典型相关系数

     将《典型相关性》表格改为《典型相关系数》，第一列改为“相关系数”，最后一列改为“p值”。我们要通过p值列确定典型相关系数的个数。首先将置信水平确定 (90%, 95%, 99%), 确定方法为看第一行p值是否小于0.05，小于的话首选95%，大于的话调整成为90%，如果后面p值较多小于0.05的话调整为99%。

     确定好置信水平后，，先看第一个数是否小于对应的显著性水平 (0.1, 0.05, 0.01)，小于的话看第二个数是否小于显著性水平，依此类推直到一个数大于显著性水平为止。所有大于显著性水平的p值的格式就是典型相关系数的个数，对应的“相关系数”列就是典型相关系数。

   - 得到典型相关变量对应的线性组合系数

     将《标准化/非标准化典型相关系数》表格改为《标准化/非标准化典型相关变量对应的线性组合系数》，变量1, 2, 3, ...对应的是第几个典型变量(符合典型相关系数的个数)

     然后写成
     

![](https://www.zhihu.com/equation?tex=%0A%20%20%20%20%20U_i%5E%2A%3Da_1%5E%7B%28i%29%7DX_1%5E%7B%281%29%7D%2Ba_2%5E%7B%28i%29%7DX_2%5E%7B%281%29%7D%2B%5Ccdots%2Ba_p%5E%7B%28i%29%7DX_p%5E%7B%281%29%7D%5C%5CV_i%5E%2A%3Db_1%5E%7B%28i%29%7DX_1%5E%7B%282%29%7D%2Bb_2%5E%7B%28i%29%7DX_2%5E%7B%282%29%7D%2B%5Ccdots%2Bb_q%5E%7B%28i%29%7DX_q%5E%7B%282%29%7D%0A%20%20%20%20%20)

     的形式(*代表标准化后的典型变量，i代表第i个典型变量)

   - 典型载荷
   
     正数即正相关，负数即负相关，绝对值越大相关性越强
   
     在论文中可以解释一下典型载荷分析的结果，例如：结果说明，生理指标的第一典型变量与体重的相关系数为-0.621，与腰围的相关系数为-0.925，与脉搏的相关系数为0.333。从另一方面说明生理指标的第一对典型变量与体重、腰围负相关，而与脉搏正相关。其中与腰围的相关性最强。第一对典型变量主要反映了体形的胖瘦。
   
   - 冗余分析
   
     指前r个典型变量对样本总方差的贡献。看《已解释的方差比例》中集合1 * 自身和集合2 * 自身两列数据中的前 i 行( i 为典型相关系数的个数)
   
     

​     



   

