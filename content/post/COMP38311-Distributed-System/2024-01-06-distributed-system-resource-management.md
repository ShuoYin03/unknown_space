---
title: "Advanced Distributed System - Resource Management"
subtitle: "Resource Management"
description: "Introduce how to take faults into our consideration"
date: 2024-01-06
author: UNKNOWN SPACE
image: ""
tags: ["Distributed System"]
categories: ["notes"]
URL: "/2024/01/06/distributed-system-resource-management/"
math: true
---

## What are resources?

All stuffs needed for maintaining the run of a system are called `resources`, such as `hardware`(CPU, storage, network links), `software`(web services), and datasets. Applications need to share the resources, and we need to consider how to optimize their use with respect to resources available and resources requested by different applications. 

One example demonstrating a trade-off between **time, price and storage resource** is that, we could make a software `parallelisable` and run it with different expensive processors, but it uses lots of storage because large amount of data are processing at the same time. Or, run the software `sequentially` on a cheaper processor with less storage used because smaller amount of data is active at the same time.

## Grid Computing

One of the definition of `grid computing` is: Resource sharing and coordinated problem solving in dynamic virtual organizations. The grid computing coordinates the resources not subjected to centralized control, it use **standard, open, general-purpose protocols and interfaces**
to deliver service. Some functions of grid computing are:

- Resource discovery and information collection and publishing
- Data Management on and between resources
- Process Management on and between resources
- Common Security Mechanisms
- Process and Session Recording/Accounting

## Cloud Computing
The idea of `cloud computing` is, by providing resources as a service to users who don't have their own resources. This is called `on-demand resource provisioning`. It relies on virtualization of resources that create virtual machines as opposed to physical machines.

There are some cloud computing service models:
1. Software as a Service (SaaS):  
Provides software as services. E.g. **Microsoft 365, Dropbox**
2. Platform as a Service (PaaS):  
Provides environment of programming functionalities. E.g. **Google Compute Engine**
3. Infrastructure as a Service (IaaS):  
Provides `pay-as-you-go` access to storage, networking resourses and others. E.g. **Hadoop + Mapreduce**

And in cloud computing, there are two roles - the `cloud provider` and `cloud consumer`, where a `cloud provider`'s objective is to provide services to user and earn profits, and a cloud consumer wants to buy resources and apply them to solve tasks. On the perspective of a `cloud provider`, there are some aspects need to consider in a question - how to allocate VM(Virtual Machine) to PM(Physical Machine)?
1. How to map services level agreement with users
2. How to maximise resource allocation
3. How to minimise energy cost

