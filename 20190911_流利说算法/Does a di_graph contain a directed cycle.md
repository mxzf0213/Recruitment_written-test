## 题目描述

Given a VxV matrix representation of a directed graph, where V is the number of the vertices of the graph. The(i, j)th element of the matrix indicates the number of directed edges from the i_th vertex to the j_th vertex. Write an efficient algorithm to determine whether this graph contains directed cycles.

an eficient algonthm to determine whether this graph contains directed cycles

## 输入描述

图矩阵。

## 输出描述

输出1或0表示是否存在环。

## 示例1

### 输入

[[0, 1, 0], [0, 0, 1], [1, 0, 0]]
[[0, 0, 0, 1, 0], [1, 0, 0, 0, 0], [0, 0, 0, 1, 1], [0, 0, 0, 0, 0], [0, 1, 0, 0, 0]]

### 输出

1

0

## 思路  

判断有向图是否存在环，dfs或拓扑排序。

## 代码

缺