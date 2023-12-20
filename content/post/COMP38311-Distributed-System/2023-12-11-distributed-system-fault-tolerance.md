---
title: "Advanced Distributed System - Fault Tolerance"
subtitle: "Fault Tolerance"
description: "Introduce how to take faults into our consideration"
date: 2023-12-15
author: UNKNOWN SPACE
image: ""
tags: ["Distributed System"]
categories: ["notes"]
URL: "/2023/12/15/distributed-system-fault-tolerance/"
draft: false
---

>In a distributed application, we always have to consider the impact of faults and solutions of how we can solve it while balancing the cost, response time and other performances.

## Type of Failures
First of all, let’s have a look at what type of faults do have.
1. Omission failures  
The server fails to **respond/receive** to incoming requests and fail to **send** messages
2. Timing failures  
The server fails to respond within a certain time
3. Response failures  
The server might response incorrect
4. Arbitrary (byzantine) failures  
A component produces output it should have never produced (may not be detected as incorrect): **arbitrary response at arbitrary times**
5. Crash  
Server **halts**!

## Fault-Tolerance
Usually, we use redundancy to do failure masking, in this article, I will introduce 3 types of redundancy of how and when to use each one.

First, consider the `two-generals' problem`, where we have two armies, each led by a general, are preparing to attack a village. The armies are outside the village, each on its own hill. The generals can communicate **only by sending messengers** passing through the valley. As the way they communicate might fail, we have to add the following redundancy to ensure the attack is ontime.
 
### Physical Redundancy
As the name "Physical" says, we have to add physical devices to allow some failures on some devices. In the `two-generals' problem`, there's a restriction in the problem that there's only two armies so we could implement physical redundancy, however if we want to make sure the attack, we could add more attacking armies to allow some sending messengers failed to send messages. 

### Time redundancy
We could let armies send messengers multiple times to allow some of them fails, and in other situation, time redundancy means to repeat actions multiple times. But for this type of redundancy, we have to consider the costs of excuting each actions.

### Information redundancy
Another method of tolerating this error is to send extra messengers to other armies to increase success rate, in other type of problems, we send extra bits instead.

### Triple Modular Redundancy

![Alt text](/img/distributed-fault/image.png)