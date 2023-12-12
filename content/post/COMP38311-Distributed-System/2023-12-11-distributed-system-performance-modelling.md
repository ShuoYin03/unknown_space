---
title: "Advanced Distributed System - Performance Modelling"
subtitle: "Performance Modelling"
description: "Introduce how to model the performance of distributed application"
date: 2023-12-12
author: UNKNOWN SPACE
image: ""
tags: ["Distributed System"]
categories: ["notes"]
URL: "/2023/11/06/advanced-distributed-system-performance-modelling/"
draft: false
math: true
---

> It is always good to test the performance of distributed applications to ensure it meets the target, and today we'll learn what is a model and how to build a model to achieve this.

<!--more-->
## What is a model
A `model` is a representation of a system that could be used to track the key characteristics and analyze the behaviour of a system.

There are two approches two build a model:
1. Analytical Model
2. Simulation

## Analytical Model
Here are some examples for analytical model:
1. Minimum Possible HTTP Transaction Time  
$$t = RTT + t_{request} + t_{siteprocessing} + t_{reply}$$
In this equation, we have t for time and RTT for round-trip-time, $t_{request}$ is request size divided by bandwidth, $t_{siteprocessing}$ is the time for processing and $t_{reply}$ is reply size / bandwidth.  

2. Parallel Computation  
$$t_p=t_s*(1-x+x/p)$$
The above equation is called the `Amdahl’s Law`, which calculates the total running time $t_p$. It defines a program running in time $t_s$ with only 1 CPU, try run this program with p CPUs, the inherently sequential part $1-x$, and the rest of them are the parts could be run parallel. The idea of this law is, the whole system is retricted to the inherently sequential part when we are doing optimization.
### Querying Theory
The Querying theory is a much more complicated problem considering the service counters to which customers arrive and join a waiting line (queue), few parameters that could influence the results are: arrvial rate, number of servers, processing time, etc.  

The `liitle's law` is a useful result for it. Look at the equation $$Avg\\_no\\_of\\_customers\\_in = arrival\\_rate × service\\_time$$
In a `steady state`, the above equation holds, which means in the queue, there won't be stacked requests.
## Simulation
Simulation is useful after a large number of samples tested, we simulate what samples and check the result.

We could use `Monte-Carlo` to implement simulation which contains two steps:
1. Generate random input
2. Simulate what follows and check the result

### Discrite Event Simulation
In a discrite event simulation, we randomly generate events with some notion of time.


