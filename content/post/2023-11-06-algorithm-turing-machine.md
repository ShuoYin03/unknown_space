---
title:       "Algorithm and Data Structure - Turing Machine"
subtitle:    "The Machine Stops!"
description: "Introduced"
date:        2023-11-06
author:      "不知所云集"
image:       ""
tags:        ["Algorithm", "Data Structure"]
categories:  ["notes"]
URL:         "/2023/11/06/algorithm-and-data-structure-turing-machine/"
draft:       true
---


## 1. Introduction of turing machine
The picture below is a multi-tape turing machine
![](/img/turing-machine/image.png)
In a formal definition, a turing machine could be define as a `quintuple`:  

<p style="text-align:center;">M = [ K, Σ, Q, q0,T ]</p>

K ≥ 2 (number of tapes)  
Σ is a non-empty, finite set (alphabet)  
Q is a non-empty, finite set (set of states)  
q0 ∈ Q (initial state)  
T is a set of transitions (for K, Σ and Q)
    
A symbol is an element of 
![](/img/turing-machine/image2.png)
which means blank and start separately
We denote the set of finite strings over Σ by Σ∗

