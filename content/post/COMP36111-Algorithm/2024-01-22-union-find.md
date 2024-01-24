---
title:       "Union Find"
subtitle:    ""
description: ""
date:        2018-06-04
author:      ""
image:       ""
tags:        ["tag1", "tag2"]
categories:  ["Tech" ]
draft: true
---
还需要复习的内容：证明union find
涉及到的算法：

connected components:

dfs(G, v, i):
    mark v with i
    for next in edges of v
        if not marked
            dfs(G, next, i)

cc:
    i = 0
    for all vertices:
        if not marked:
            dfs(G, v, i)
            i += 1

union-find
    set P as []
    for all nodes:
        make-set(node)
    for all vertices:
        if find(u) != find(v):
            union(find(u), find(v))

make-set(v):
    s = []
    s.size = 1
    s.append(v)
    P.appendS

union(u, v):
    u = find(u)
    v = find(v)
    if u.size > v.size:
        v.parent = u
    else: 
        u.parent = v

find(x):
    while x.parent != x:
        x.parent = x.parent.parent
        x = x.parent
    return x

loop language:

     