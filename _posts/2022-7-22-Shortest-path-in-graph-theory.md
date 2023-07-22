---
title: 第八讲：图论最短路径
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


## 基本概念

### 图的基本概念

- 一个图可以用数学语言描述为G(V(G),E(G))。V(vertex)指
  的是图的顶点集，E(edge)指的是图的边集。
- 根据边是否有方向，可将图分为有向图和无向图。
- 另外，有些图的边上还可能有权值，这样的图称为有权
  图。

### 作图工具

- [在线作图](https://csacademy.com/app/graph_editor/)

- MATLAB

### 无向图的权重邻接矩阵

<img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143856150.png" alt="image-20230722143856150" style="zoom: 33%;" />
$$
D=\begin{bmatrix} 0 & Inf & 3 & 3 \\ Inf & 0 & Inf & 5 \\ 3 & Inf & 0 & 2 \\ 3 & 5 & 2 & 0\end{bmatrix}
$$

### 有向图的邻接矩阵

<img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722143910828.png" alt="image-20230722143910828" style="zoom:33%;" />
$$
D=\begin{bmatrix} 0 & Inf & 8 & 3 \\ Inf & 0 & Inf & 5 \\ 8 & Inf & 0 & 2 \\ Inf & Inf & Inf & 0\end{bmatrix}
$$

## 迪杰斯特拉(Dijkstra)算法

### 步骤

<img src="https://alps-images.obs.cn-east-2.myhuaweicloud.com/img/image-20230722144041929.png" alt="image-20230722144041929" style="zoom:67%;" />

图中有0‐8共九个地点，地点之间若用直线连接则表明两地可直接到达，直线旁的数值表示两地的距离。
问题: 起点为0，终点为4，怎么走路程最短？(假设出行方式相同，例如都为步行)

1. 看与起点相连的两个节点哪个到达的距离更近，判断出是1更近
2. 看与1相连的3个节点(包括0)，哪个到达的距离更近，判断出是7
3. 以此类推，但需要注意的是需要把到达每个点的路径值都算出来，不能落点。也就是说每当有分叉时都要把分出来的每个路径走完算出距离
4. 这种算法也就是找出起点到终点的所有走法并比较路径大小求出最小值(个人感觉也能求最大值)

### 优缺点

- 优：比贝尔曼·福特算法时间复杂度低
- 缺：不能处理负权重

## 贝尔曼·福特(Bellman-ford)算法

### 步骤



### 优缺点

- 可以处理负权重(有向图)
- 时间复杂度高

> 注：这种算法也不能处理负权回路的问题，负权回路指一个环上所有权值之和为负数。

## MATLAB代码

### MATLAB绘图

```matlab
% s中的点和t中的一一对应，也就是每条连线都要在s和t的对应关系中体现。
s1 = [1,2,3,4];
t1 = [2,3,1,1];
% 若有权重则加上w，w对应着每条边上的权重
w1 = [3,8,9,2];
% 若是无向图就用graph，若是有向图就用diagraph
G = graph(s1,t1,w1)；
plot(G,'EdgeLable',G.Edges.Weight,'linewidth',2)
% 不显示坐标
set(gca,'XTick',[],'YTick',[]); 
```

### MATLAB求解最小距离

```matlab
%% 假设已绘出图形G
% 求解两点间最短路径与距离(P为path，d为distance)
[P,d] = shortestpath(G,9,4)
% 求出任意两点的最短路径矩阵(路线),以1到2为例
distances(G,1,2)
% 找出给定范围内的所有点：返回图形G中与节点2的距离在10之内的所有节点
[nodeIDs,dist] = nearest(G, 2, 10)
```





  