---
title: 第五讲：相关系数
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


它们可用来衡量两个变量之间的相关性的大小，根据数据满足的不同条件，我们要选择不同的相关系数进行计算和分析 (建模论文中最容易用错的方法)

---

## 皮尔逊Pearson相关系数

### 总体皮尔逊相关系数

1. 如果两组数据![](https://www.zhihu.com/equation?tex=X%3A%5C%7BX_1%2CX_2%2C%5Cdots%2CX_n%5C%7D)和![](https://www.zhihu.com/equation?tex=Y%3A%5C%7BY_1%2CY_2%2C%5Cdots%2CY_3%5C%7D)是**总体数据**（例如普查结果)，

   那么总体均值：![](https://www.zhihu.com/equation?tex=E%28x%29%3D%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5EnX_i%7D%7Bn%7D%2CE%28Y%29%3D%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5EnY_i%7D%7Bn%7D)

   总体协方差：![](https://www.zhihu.com/equation?tex=Cov%28X%2CY%29%3D%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5En%28X_i-E%28X%29%29%28Y_i-E%28Y%29%29%7D%7Bn%7D)

   **总体Pearson相关系数：![](https://www.zhihu.com/equation?tex=%5Crho%20_%7BXY%7D%3D%5Cfrac%7BCov%28X%2CY%29%7D%7B%5Csigma_X%5Csigma_Y%7D%3D%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5En%5Cfrac%7B%28X_i-E%28X%29%29%7D%7B%5Csigma_X%7D%5Cfrac%7B%28X_i-E%28Y%29%29%7D%7B%5Csigma_Y%7D%7D%7Bn%7D)**

   ![](https://www.zhihu.com/equation?tex=%5Csigma_X%28sigma%5C%20X%29)是![](https://www.zhihu.com/equation?tex=X)的标准差，![](https://www.zhihu.com/equation?tex=%5Csigma_X%3D%5Csqrt%7B%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5En%28X_i-E%28X%29%29%5E2%7D%7Bn%7D%7D%2C%5Csigma_Y%3D%5Csqrt%7B%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5En%28Y_i-E%28Y%29%29%5E2%7D%7Bn%7D%7D)

   **可以证明，<img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722193943714.png" style="zoom:70%;" />，且当![](https://www.zhihu.com/equation?tex=Y%3DaX%2Bb)时，![](https://www.zhihu.com/equation?tex=%5Crho_%7BXY%7D%3D%5Ccases%7B1%5C%20%5C%20%5C%20%2Ca%3E0%5C%5C-1%2Ca%3C0%7D)**

   - 直观理解协方差：如果X、Y变化方向相同，即当X大于（小于）其均值时，Y也大于（小于）其均值，在这两种情况下，乘积为正。如果X、Y的变化方向一直保持相同，则协方差为正；同理，如果X、Y变化方向一直相反，则协方差为负；如果X、Y变化方向之间相互无规律，即分子中有的项为正，有的项为负，那么累加后正负抵消。

     *（注意：协方差的大小和两个变量的量纲有关，因此不适合做比较。）*

   - 皮尔逊相关系数也可以看成是剔除了两个变量量纲影响，即将X和Y标准化后的协方差

### 样本皮尔逊相关系数

1. 假设有两组样本数据![](https://www.zhihu.com/equation?tex=X%3A%5C%7BX_1%2CX_2%2C%5Cdots%2CX_n%5C%7D)和![](https://www.zhihu.com/equation?tex=Y%3A%5C%7BY_1%2CY_2%2C%5Cdots%2CY_n%5C%7D)（一般调查得到的数据均为样本数据）

   样本均值：![](https://www.zhihu.com/equation?tex=%5Coverline%7BX%7D%3D%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5EnX_i%7D%7Bn%7D%2C%5Coverline%7BY%7D%3D%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5EnY_i%7D%7Bn%7D)

   样本协方差：![](https://www.zhihu.com/equation?tex=Cov%28X%2CY%29%3D%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5En%28X_i-%5Coverline%7BX%7D%29%28Y_I-%5Coverline%7BY%7D%29%7D%7Bn-1%7D)

   **样本Pearson相关系数：**![](https://www.zhihu.com/equation?tex=r_%7BX%2CY%7D%3D%5Cfrac%7BCov%28X%2CY%29%7D%7BS_XS_Y%7D)

   其中：![](https://www.zhihu.com/equation?tex=S_X%28sigma%5C%20X%29)是![](https://www.zhihu.com/equation?tex=X)的样本标准差，![](https://www.zhihu.com/equation?tex=S_X%3D%5Csqrt%7B%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5En%28X_i-%5Coverline%7BX%7D%29%5E2%7D%7Bn-1%7D%7D),

   同理![](https://www.zhihu.com/equation?tex=S_Y%3D%5Csqrt%7B%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5En%28Y_i-%5Coverline%7BY%7D%29%5E2%7D%7Bn-1%7D%7D)

### 结论

1. **注意：皮尔逊相关系数是描述变量线性相关程度的指标；**

   **也就是说，需要先确认两个变量是线性相关的（画散点图），才能使用皮尔逊相关系数**

   **相关系数计算结果为0，只能说不是线性相关，但说不定会有更复杂的相关关系（非线性相关）**

2. *易错点1：离群点（及比较离谱的点）对相关系数的影响很大，去掉后相关系数会提高，如下图一1*

3. *易错点2：如果两个变量的相关系数很大也不能说明两者相关，可能是受到了异常值的影响，如下图2*

![image-20230722143406885](https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143406885.png)

### 对相关系数大小的解释

| 相关性   | 负           | 正          |
| -------- | ------------ | ----------- |
| 无相关性 | -0.09 to 0.0 | 0.0 to 0.09 |
| 弱相关性 | -0.3 to -0.1 | 0.1 to 0.3  |
| 中相关性 | -0.5 to -0.3 | 0.3 to 0.5  |
| 强相关性 | -1.0 to -0.5 | 0.5 to 1.0  |

上表所定的标准从某种意义上说是武断的和不严格的，对相关系数的解释是依赖于具体的应用背景和目的的。

事实上，比起相关系数的大小，我们往往更关注的是显著性。**（假设检验）**

### **MATLAB函数**

1. 数据分析

   | 函数名       | 功能                  |
   | ------------ | --------------------- |
   | **min**      | **数组的最小元素**    |
   | mink         | 计算数组中k个最小元素 |
   | **max**      | **数组的最大元素**    |
   | maxk         | 计算数组的k个最大元素 |
   | bounds       | 最小元素和最大元素    |
   | topkrows     | 按排序顺序的前若干行  |
   | **mean**     | **数组的均值**        |
   | **median**   | **数组的中位数**      |
   | mode         | 数组的众数            |
   | **skewness** | **数组的偏度**        |
   | **kurtosis** | **数组的峰度**        |
   | **std**      | **标准差**            |
   | var          | 方差                  |

   ```matlab
   MIN = min(Test); % 每一列的最小值
   MAX = max(Test); % 每一列的最大值
   MEAN = mean(Test); % 每一列的均值
   MEDIAN = median(Test); %每一列的中位数
   SKEWNESS = skewness(Test); %每一列的偏度
   KURTOSIS = kurtosis(Test); %每一列的峰度
   STD = std(Test); % 每一列的标准差
   RESULT = [MIN;MAX;MEAN;MEDIAN;SKEWNESS;KURTOSIS;STD] %将这些统计量放到一个矩阵中表示
   % 将计算结果放到EXCEL表格中
   ```

   ***不要将生成的表格直接粘贴到论文里，需要精简***

2. 皮尔逊相关系数的计算

   **`R = corrcoef(A)`**
   返回 A 的相关系数的矩阵，其中 A 的列表示随机变量（指标），行表示观测值（样本）。
   `R = corrcoef(A,B)`
   返回两个随机变量 A 和 B （两个向量）之间的系数。

### \*EXCEL的数据分析工具

![image-20230722143420609](https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143420609.png)

标题栏：数据 - 数据分析 - 描述统计

<img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143427660.png" alt="image-20230722143427660" style="zoom:67%;" />

***不要将生成的表格直接粘贴到论文里，需要精简***

---

如何美化相关系数表（例子）：

1. 在开始 ‐ 格式中调整每个单元格的格式为正方形
2. 在对齐方式中设置两个居中
3. 选中相关系数表，开始 ‐ 条件格式 ‐ 色阶 - 选中红 ‐ 白 ‐ 蓝那个
4. 选中相关系数表，选择条件格式 ‐ 管理规则 ‐ 编辑规则

*（其实R语言和Python中有很多类似的包，这里我们用Excel模仿）*

### \*SPSS

1. 描述性统计结果

<img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143439873.png" alt="image-20230722143439873" style="zoom:67%;" />

<img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143452998.png" alt="image-20230722143452998" style="zoom:67%;" />

***不要将生成的表格直接粘贴到论文里，需要精简***

2. 矩阵散点图

   在计算皮尔逊相关系数之前,一定要做出散点图来看两组变量之间是否有线性关系
   这里使用SPSS比较方便: 图形 ‐ 旧对话框 ‐ 散点图/点图 ‐ 矩阵散点图

   <img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143458363.png" alt="image-20230722143458363" style="zoom:50%;" />
   
3. 夏皮洛‐威尔克检验 (Shapiro‐wilk)

   <img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143533884.png" alt="image-20230722143533884" style="zoom:67%;" />

   <img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143541217.png" alt="image-20230722143541217" style="zoom:67%;" />

### 对皮尔逊相关系数进行假设检验

#### 皮尔逊相关系数假设检验的条件

1. **实验数据通常假设是成对的来自于正态分布的总体。**因为我们在求皮尔逊相关性系数以后，通常还会用 t 检验之类的方法来进行皮尔逊相关性系数检验，而 t 检验是基于数据呈正态分布的假设的。

    ##### 如何检验数据是否是正态分布？

    1. 雅克‐贝拉检验 (Jarque‐Bera test)：

       **适合大样本（n>30）**

       对一个随机变量![](https://www.zhihu.com/equation?tex=%5C%7BX_i%5C%7D)，假设其偏度为![](https://www.zhihu.com/equation?tex=S)，峰度为![](https://www.zhihu.com/equation?tex=K)，那么我们可以构造统计量:
       

![](https://www.zhihu.com/equation?tex=%0A%20%20%20%20%20%20%20JB%3D%5Cfrac%7Bn%7D%7B6%7D%5BS%5E2%2B%5Cfrac%7B%28K-3%29%5E2%7D%7B4%7D%5D%0A%20%20%20%20%20%20%20)

       可以证明，如果![](https://www.zhihu.com/equation?tex=%5C%7BX_i%5C%7D)是正态分布，那么在大样本情况下![](https://www.zhihu.com/equation?tex=JB%5Csim%5Cchi%5E2%282%29)（自由度为2的![](https://www.zhihu.com/equation?tex=%5Cchi_2)分布）
    
       *注：正态分布的偏度为0，峰度为3*
    
       那么进行假设检验的步骤如下：
    
       ![](https://www.zhihu.com/equation?tex=H_0): 该随机变量符合正态分布；![](https://www.zhihu.com/equation?tex=H_1)该随机变量不服从正态分布
    
       然后计算该变量的偏度和峰度，得到检验值![](https://www.zhihu.com/equation?tex=JB%5E%2A)，并计算出对应的p值。将p值与0.05比较，如果小于0.05则可拒绝原假设，否则不能拒绝原假设。
    
       > 偏度: ![](https://www.zhihu.com/equation?tex=E%5B%28%5Cfrac%7BX-u%7D%7B%5Csigma%7D%29%5E3%5D)
       >
       > 峰度: ![](https://www.zhihu.com/equation?tex=E%5B%28%5Cfrac%7BX-u%7D%7B%5Csigma%7D%29%5E4%5D)
       >
       > ```matlab
       > x = normrnd(a,b,c,d); %生成c*d的随机向量，每个元素均值为a，标准差为b的正态分布
       > skewness(x) %偏度
       > kurtosis(x) %峰度
       > ```
    
       MATLAB代码:
    
       MATLAB中进行JB检验的语法：**[h,p] = jbtest(x,alpha)** 当输出h等于1时，表示拒绝原假设；h等于0则代表不能拒绝原假设。 alpha就是显著性水平，一般取0.05，此时置信水平为1‐0.05=0.95 x 就是我们要检验的随机变量，注意这里的 x 只能是向量。
    
       ```matlab
        %% 正态分布检验
        % 检验第一列数据是否为正态分布
        [h,p] = jbtest(Test(:,1),0.05)
        % 用循环检验所有列的数据
        n_c = size(Test,2); % number of column 数据的列数
        H = zeros(1,6);
        P = zeros(1,6);
        for i = 1:n_c
        [h,p] = jbtest(Test(:,i),0.05);
        H(i)=h;
        P(i)=p;
        end
        disp(H)
        disp(P)
       ```
    
    2. 夏皮洛‐威尔克检验 (Shapiro‐wilk) :
    
       **适合小样本 (3≤n≤50)**
    
       ![](https://www.zhihu.com/equation?tex=H_0): 该随机变量符合正态分布；![](https://www.zhihu.com/equation?tex=H_1)该随机变量不服从正态分布
    
       计算出威尔克统计量后，得到相应的p值。将p值与0.05比较，如果小于0.05则课拒绝原假设，否则不能拒绝原假设
    
       见SPSS.3
    
    3. Q-Q图:
    
       **要求数据量非常大**
    
       Q‐Q图 (Q代表分位数Quantile) 是一种通过比较两个概
       率分布的分位数对这两个概率分布进行比较的概率图方法。
    
       这里选择正态分布和要检验的随机变量取分位数，并对其做出QQ图。如果要检验的随机变量是正态分布，那么QQ图就是一条直线。（看Q‐Q图上的点是否近似地在一条直线附近）
    
       `qqplot(Test(:,1))`
    
       <img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143556244.png" alt="image-20230722143556244" style="zoom:67%;" />

2. **实验数据之间的差距不能太大。**皮尔逊相关性系数受异常值影响比较大。
3. **每组样本之间是独立抽样的。**构造 t 统计量时需要用到。

#### 具体步骤

1. 提出原假设![](https://www.zhihu.com/equation?tex=H_0)和备择假设![](https://www.zhihu.com/equation?tex=H_1)（两个假设是截然相反的）

   假设我们计算出了一个皮尔逊相关系数r，我们想检验它是否显著的异于0.那么我们可以这样设定原假设和备择假设：![](https://www.zhihu.com/equation?tex=H_0%3Ar%3D0%2C%5C%20H_1%3Ar%5Cneq0)

2. 在原假设成立的条件下，利用我们要检验的量构造出一个符合某一分布的统计量

   对于皮尔逊相关系数 ![](https://www.zhihu.com/equation?tex=r) 而言，在满足一定条件下，我们可以构造统计量:

   ![](https://www.zhihu.com/equation?tex=t%3Dr%5Csqrt%7B%5Cfrac%7Bn-2%7D%7B1-r%5E2%7D%7D)，可以证明 ![](https://www.zhihu.com/equation?tex=t) 是服从自由度的 ![](https://www.zhihu.com/equation?tex=n-2) 的 ![](https://www.zhihu.com/equation?tex=t) 分布

   *(注1：统计量相当于我们要检验的量的一个函数，里面不能有其他的随机变量)*

   *(注2：这里的分布一般有四种：标准正态分布，![](https://www.zhihu.com/equation?tex=t)分布，![](https://www.zhihu.com/equation?tex=%5Cchi%5E2)分布和 ![](https://www.zhihu.com/equation?tex=F) 分布)*

3. 将我们要检验的这个值（相关系数 r 和样本 n）带入这个统计量中，可以得到一个特定的值（检验值）

4. 由于我们知道统计量的分布情况因此我们可以画出该分布的概率密度函数 (pdf)，并给定一个置信水平，根据这个置信水平查![](https://www.zhihu.com/equation?tex=t/%5Cchi%5E2/F)分布表找到临界值，并画出检验统计量的接受域和拒绝域。

   常见的置信水平有三个：90%，95%和99%，其中95%是三者中最为常用的。

   例如：利用**tpdf(x,自由度)**

   ```matlab
   x = -4:0.1:4;
   y=tpdf(x,28);
   plot(x,y,'-')
   grid on %加网格线
   ```

   <img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143615180.png" alt="image-20230722143615180" style="zoom:50%;" />

5. 看第3步计算出来的检验值是落在了拒绝域还是接受域

   下结论：在···%的置信水平上，我们拒绝/无法拒绝原假设![](https://www.zhihu.com/equation?tex=H_0%3Ar%3D0)，因此![](https://www.zhihu.com/equation?tex=r)是/否显著不为0的。

6. 显著性标记：

   r: 和0没有显著的差异

   r*: 在90%置信水平显著不为0

   r**: 在95%置信水平显著不为0

   r***: 在99%置信水平显著不为0

#### 总结

1. 提出原假设和备择假设
2. 构造统计量：标准正态分布，![](https://www.zhihu.com/equation?tex=t)分布，![](https://www.zhihu.com/equation?tex=%5Cchi%5E2)分布和 ![](https://www.zhihu.com/equation?tex=F) 分布
3. 代值入统计量，算出检验值
4. 画出概率密度函数，给出置信水平，找到临界值，得到接受域和拒绝域
5. 下结论：r是否显著为0 (本例拒绝原假设以为皮尔逊系数显著异于0)
6. 显著性标记

#### p值判断法 (更好用的方法)

1. 计算p值

   前三步和上述一样，得到检验值![](https://www.zhihu.com/equation?tex=t%5E%2A)

   **利用累积分布函数 (CDF) : `tcdf(t,自由度)`**

   `p=((1-tcdf(3.055,28))*2)`

   MATLAB计算的是双侧检验的p值，如果需要单侧的话除以2即可

   |                                         |                                             |
   | --------------------------------------- | ------------------------------------------- |
   | p<0.01，说明在99%的置信水平上拒绝原假设 | p>0.01，说明在99%的置信水平上无法拒绝原假设 |
   | p<0.05，说明在95%的置信水平上拒绝原假设 | p>0.05，说明在95%的置信水平上无法拒绝原假设 |
   | p<0.10，说明在90%的置信水平上拒绝原假设 | p>0.10，说明在90%的置信水平上无法拒绝原假设 |

2. 显著性标记：

   r: 不显著

   r*: 在90%置信水平显著

   r**: 在95%置信水平显著

   r***: 在99%置信水平显著

3. MATLAB代码：

   ```matlab
   [R,P]=corrcoef(A)
   % R返回的是相关系数表，P返回的是对应于每个相关系数的p值
   ```


## 斯皮尔曼Spearman相关系数

### 定义

X和Y为两组数据，其斯皮尔曼(等级)相关系数：

![](https://www.zhihu.com/equation?tex=%0Ar_s%3D1-%5Cfrac%7B6%5Csum_%7Bi%3D1%7D%5End_i%5E2%7D%7Bn%28n%5E2-1%29%7D%0A)

其中，![](https://www.zhihu.com/equation?tex=d_i)为![](https://www.zhihu.com/equation?tex=X_i)和![](https://www.zhihu.com/equation?tex=Y_i)之间的等级差。(一个数的等级，就是将它所在的一列数按照从小到大排序后，这个数所在的位置)

可以证明：![](https://www.zhihu.com/equation?tex=r_s)位于1和-1之间

> 注：如果有的数值相同，则将他们所在的位置取算术平均。

斯皮尔曼相关系数被定义成等级之间的皮尔逊相关系数。

### MATLAB代码

(1) `corr(X,Y,'type','Spearman')`

这里的X和Y必须是列向量

(2) `corr(X,'type','Spearman')`

这是计算X矩阵各列之间的斯皮尔曼相关系数

### 斯皮尔曼相关系数的假设检验

#### 小样本(![](https://www.zhihu.com/equation?tex=n%5Cleqslant%2030))

直接查临界值表即可。

![](https://www.zhihu.com/equation?tex=%0AH_0%3Ar_s%3D0%5C%5CH_1%3Ar_s%5Cneq0%0A)

<img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143628518.png" alt="image-20230722143628518" style="zoom:80%;" />

#### 大样本

统计量![](https://www.zhihu.com/equation?tex=r_s%5Csqrt%7Bn-1%7D%5Csim%20N%280%2C1%29)

![](https://www.zhihu.com/equation?tex=H_0%3Ar_s%3D0%3B%5C%20H_1%3Ar_s%5Cneq0)

我们计算检验值![](https://www.zhihu.com/equation?tex=r_s%5Csqrt%7Bn-1%7D)，并求出对应的p值与0.05相比即可。

p值大于0.05，无法拒绝原假设(和0没有显著的差异)；

p值小于0.05，拒绝原假设(和0有显著的差异)。

#### MATLAB代码

```matlab
% 直接给出相关系数和p值
[R,P]=corr(Test,'type','Spearman')
```

## 斯皮尔曼相关系数和皮尔逊相关系数选择

1. 连续数据，正态分布，线性关系，用Pearson相关系数是最恰当的，当然用Spearman相关系数也可以，就是效率没有Pearson向相关系数高。

2. 上述任一条件不满足，就用Spearman相关系数，不能用Pearson相关系数。

3. 两个定序数据之间也用Spearman相关系数，不能用Pearson相关系数。

   > 定序系数是指仅仅反应观测对象等级、顺序关系的数据，是由定序尺寸计量形成的，表现为类别，可以进行排序，属于品质数据。
   >
   > 例如：优、良、差；
   >
   > 我们可以用1表示差、2表示良、3表示优。但请注意，用2除以1得出的2并不代表任何含义。定序数据最重要的意义代表了一组数据中的某种逻辑顺序。

> 注：斯皮尔曼相关系数的适用条件比皮尔逊相关系数要广，只要数据满足单调关系（例如线性函数、指数函数、对数函数等）就能够使用。
