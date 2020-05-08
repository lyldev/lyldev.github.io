---
title: 使用 Eigen 库对矩阵（Matrix）进行中心化
tags: C++ Eigen 矩阵
key: a2020-05-05-eigen-matrix-centralization
layout: article
aside:
  toc: true
show_edit_on_github: false
mathjax: true
mathjax_autoNumber: true
mermaid: true
chart: true
# sidebar:
#   nav: sidebar
---
## 什么叫矩阵的中心化（标准化）
所谓中心化也可以叫标准化——假设一个 `3*N`（指的是3行N列） 的矩阵，其中每一列代表三维空间中的一个点，从而这个矩阵代表 N 个点的集合。

对这个矩阵进行中心化首先要计算 N 个点的中心点（平均位置），然后对点集中的每个点都减去这个中心位置得到新的中心化后的点集。这个过程可以看作原点从 `(0，0，0）`变为点集平均位置的一次坐标系转换。

## 如何在 Eigen 中实现矩阵的中心化操作
具体到 Eigen 中的矩阵操作就是 首先求矩阵中各列的平均值得到一个 `3*1` 的列向量，然后将原矩阵中的每一列都减去上一步得到的平均值列向量，得到中心化的矩阵。

最后具体到代码实现如下：
```cpp
Eigen::Matrix3Xd centered_p = P.colwise() - P.rowwise().mean();
```
## _注意_：
求矩阵中所有列向量的平均值用的是 `rowwise().mean()` ，这个初看起来好像不太对，求列向量的平均值为什么是 按行（`rowwise`） 求平均值呢？其实利用 `1*N` 的矩阵更好理解，求这 N 个 `1*1` 列向量的平均就是对整行（`rowwise`）元素求平均值。