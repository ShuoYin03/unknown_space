---
title:       "算法与数据结构1 - 有向图"
subtitle:    "Direct graph and strong connected components"
description: "本文探讨有向图，强连接分量的概念以及相关算法"
date:        2023-11-03
author:      "不知所云集"
image:       ""
tags: ["Algorithm", "Data Structure"]
categories:  ["notes"]
URL:        "/2023/11/03/graph_theory/"
draft: true
---

<!--more-->
## 1. 有向图相关概念 | Concepts of Directed Graph

一个有向图可以被定义为一个二元组G = (V, E), 其中V代表了有限的，非空的点的集合，而E则代表点和点之间边的集合。如果在u，v之间存在一条边 e = (u, v) ∈ E，那么u与v相邻，同时与该边e相邻。  
<!-- A directed graph could be define as a tuple G = (V, E), which V symbolize a  -->
需要注意的是一个有向图需要满足以下几点：
1. 没有导向自己节点的边
2. 单一节点连接出去的边上限为一条
3. 所有边皆为有向边

连接到某一个点的边则为该点的**入度（in-degree）**， 反之则为**出度（out-degree）**  
|{w ∈ V : (w, v) ∈ E}|






