---
title: "Algorithm and Data Structure - Turing Machine"
subtitle: "The Machine Stops!"
description: "Introduced Turing Machine, and the theory behind it"
date: 2023-11-06
author: "UNKNOWN SPACE"
image: ""
tags: ["Algorithm", "Data Structure"]
categories: ["notes"]
URL: "/2023/11/06/algorithm-and-data-structure-turing-machine/"
math: true
draft: false
---

>In this article, we are going to look at the formal definition of Turing Machine and the therom with it.

<!--more-->
## 1. Introduction of turing machine
The picture below is a `multi-tape` turing machine
![](/img/turing-machine/image.png)
In a formal definition, a turing machine could be define as a quintuple:  

<p style="text-align:center;">M = [ K, Σ, Q, q0, T ]</p>

1. K ≥ 2 (number of tapes)  
2. Σ is a non-empty, finite set (alphabet)  
3. Q is a non-empty, finite set (set of states)  
4. q0 ∈ Q (initial state)  
4. T is a set of transitions (for K, Σ and Q)
    
A `symbol` is an element of 
![](/img/turing-machine/image2.png)
which means `blank` and `start` separately.  
We denote the `set of finite strings` over Σ by Σ∗

A `transition` is also a quintuple:

<p style="text-align:center;">[ p, s¯, q, t¯, d¯ ]</p>

1. p ∈ Q and q ∈ Q  
2. s¯ and t¯ are K-tuples of symbols  
3. d¯ is a K-tuple whose elements from {left, right, stay}  

**An informal explanation is**: If you are in state p, and the current node being scanned is s¯, then set the new state to be q, write the symbol of t¯ on the tape and move as what d¯ says.

Here are few rules that a Turing Machine must follows:
1. The tape never moves to the left of `start` symbol.
2. Tape one is `read-only` and the last tape (K tape) is `write-only`.
3. the start symbol doesn't involves in the transition
4. nothing is over-written with blank

A `Configuration` is a set of snap shots of the turing machine which successive ones could form some transitions T, and a `run` of turing machine could be defined as a sequence of configurations. Formally, a configuration is a K-tuple of String, σ1 ... σk, where each σ represents one element in the form:
<p style="text-align:center;">start symbol, sk,1, ... , sk,i−1, q, sk,i, ... , sk,n(k)</p>
This states that the head is currently at position i, where sk,i-1 is not scanned yet, and the current state is q.

1. if some transition is possible in a configuration of the run, then this is not the last configuration. 
2. If the run is finite, then the turing machine is terminating
3. A `deterministic` turing machine M means, there is at most one transition T for each p and s¯. **M ↓ x** means a deterministic turing machine is terminating with input x, and **M ↑ x** is the opposite (non-terminating).

(To be continues...)
