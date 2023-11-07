---
title:       "Advanced Distributed System - Big data"
subtitle:    "Big Data"
description: "Introduced the distributed system, trade-offs in big data"
date:        2023-11-06
author:      "不知所云集"
image:       ""
tags:
    - "Distributed System"
categories:  ["post"]
URL:        "/2023/11/06/advanced-distributed-system-big-data/"
draft: false
---

>In a shared nothing infrastructure, data storage, update, access and processing takes place across a collection of networked machines. To enhance the performance, processing needs to be take place in parallel, which we have to distribute data, and that's partition. This article will gives an rough idea of partition techniques and details needs to be consider.

<!--more-->
## 1. Partition
![](/img/distributed-bigdata/pic.png)
By definition, partition involves deciding how to assign data from a sources to distributed nodes.Take the above image as an example, we could do partition in these ways:  

1. **Random or Round Robin:**  
Data is assigned as it is inserted across different nodes.  
    |             Pros             |                 Cons                  |
    | ---------------------------- | ------------------------------------- |
    | Uniform initial distribution | Querying involves accessing all notes |
    | Easy to rebalance on update  |

2. **Range based Partition:**  
Partitioning often assumes some form of key-value datamodel. Then partitioning relates to the key
Key range: each partition is associated with a range of values for the key (e.g. alphabetical or numerical).
    |             Pros             |                Cons                |
    | ---------------------------- | ---------------------------------- |
    | Focused range queries on key | Risk of hot spots for popular keys |
    | Focused direct access on key | Uniform distribution not intrinsic |
    |                              | Rebalancing can be expensive       |
    |                              | Only helps for key-based requests  |

3. **Hash based Partition:**  
Partition based on the hash of the keys.  
Assume we have Hash(String) -> Integer, if there is n parition, partition(key) = return(Hash(key) mod n)
    | Pros | Cons |
    | ---- | ---- |
    | Uniform distribution with certain keys | Risk of hot spots for popular keys             |
    | Focused direct access on key           | No support for range queries                   |
    |                                        | Rebalancing can be expensive                   |
    |                                        | Only helps for the requests that have the key  |

4. **Meaning based Partition:**  
Partitioning by key means choosing a suitable key
    |             Desirable             |       Examples       |
    | --------------------------------- | -------------------- |
    | Useful for range access requests  | Size                 |
    | Useful for direct access requests | Name, Town           |
    | Diverse values                    | Id, Name, Town, Size |
    | Not subject to skew               | Id, Name, Town, Size |


## 2. Repartitioning

### 1. Skew and Hot Spots
`Skew` is when partitioning is uneven. For example, a partitioning on the first letter of Country in the University table.  
A `hot spot` arises when the load is unevenly balanced. For example, many more people may look up some
universities than others.

### 2. Method  
Repartitioning involves moving the data from one partition to another.  
**Example:**  Partition by Id, use a hash function **Hash(x) = Id(x) mod #nodes**
![](/img/distributed-bigdata/pic1.png)
How many tuples need to change node?  
In this case of uniform distribution and mode-based partitioning, the number of data need to be repartitioning is:  
**To-Distribute = 1 - 1 / #final-nodes**  

In this example, the number of data need to be distribute is:   
**1 - 1/3 = 0.666**, which is **0.666 * 6 = 4**

In order to reduce the cost of repartitioning, it is possible to have more partitions than nodes. Then repartitioning for a new node involves moving selected partitions to the new node.
![](/img/distributed-bigdata/pic5.png)

Two steps need to be taken to find a partition for value v:
1. Hash v to a partition number
2. Use a lookup table to identify the node of this partition  

In this case the `fraction moved` is: **1 / #nodes + 1**  
In the previous example `fraction moved` is 1/4

## 3. Secondary Indexes

The `Ranging` and `Hashing` methods are better performed when key is widely used. NoSQL are always designed to support applications use `Id` or `names` as primary key. However, it's better for us to have multiple access routes to avoid `scanning`. In this case we use `secondary index` - the index on an attribute that has not been used for partitioning.  

Example: In this table, the data is partitioned by name. Does the hash index on the partition helps?
![](/img/distributed-bigdata/pic2.png)
|               Query              | Does partition index help? |   Useful Additional Index   |
| -------------------------------- | -------------------------- | --------------------------- |
| How many students attend UCL?    | Yes                        | N/A                         |
| Which Uni have > 40,000 students | No                         | Range index on size         |
| Which Uni are in Manchester      | No                         | Hash or range index on town |

### 1. Local Secondary Index
A key question is that where should we store these secondary index? Here are few options to do it:  

1. Store the secondary index on the same node as the data it is indexing.
![](/img/distributed-bigdata/pic3.png)
    | Pros | Cons |
    | ---- | ---- |
    | Updating a document leads to local index changes (so no distributed transactions) | A lookup needs to go to every transaction, leading to many index lookups |

2. Store the secondary index partitioned by term: a single distributed index.
![](/img/distributed-bigdata/pic4.png)
    | Pros | Cons |
    | ---- | ---- |
    | Index lookups no longer need to go to all nodes (note some index lookups will have no hits) | Updates to a document on a node now also lead to index updates (and thus potentially to distributed transactions) |

## 4. Partitioning for Evaluation

After we talked about how to do partitioning, we should discuss about when. In one case, data need partitioning while requests are being evaluated.

**Continues...**