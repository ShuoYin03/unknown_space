---
title:       "算法与数据结构1 - 有向图"
subtitle:    "Direct graph and strong connected components"
description: "本文探讨有向图，强连接分量的概念以及相关算法"
date:        2023-11-02
author:      "不知所云集"
image:       ""
tags:        ["Algorithm", "Data Structure"]
categories:  ["notes"]
URL:        "/2023/11/03/graph_theory/"
draft: true
---

构建auxiliary directed graph的方法：

算法：
Ford-Fulkerson algorithm
begin flowMax(V,E,s,t,c):
    set f(e) = 0 for all e in E
    while reachable:
        find a path e1 ... em from s to t
        for all edges:
            if e belongs E increment f(ei)
            else decrement f(ei^-1)
    return f

Busacker-Gowen algorithm
Change a little bit on Ford-Fulkerson:
begin flowMaxCost(V,E,s,t,c):
    set f(e) = 0 for all e in E
    while reachable:
        find the shortest path e1 ... em form s to t
        for all edges:
            if e belongs E increment f(ei)
            else decrement f(ei^-1)
    return f



