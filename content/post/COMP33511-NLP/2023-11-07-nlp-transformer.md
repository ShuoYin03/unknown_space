---
title: "Natural Language Processing - Attention and Transformer"
subtitle:    "Introduction to Attention RNN and Transformer neural network"
description: "Introduction to Attention RNN and Transformer neural network"
date: 2023-11-07
author: "UNKNOWN SPACE"
image: ""
tags: ["nlp"]
categories: ["notes"]
URL: "/2023/11/07/nlp-transformer/"
draft: true
---

>Last time we introduce RNN structure and some advanced RNN models, this time we will have a look at the defect in RNN, how do we avoid it and what structure should we implement.

<!--more-->
## Attention RNN

In a `Encoder-decoder RNN` architecture, there is an information bottleneck: All the information in the `encoder` is accumulated to start the `decoder`. In this case, we introduced Attention RNN to avoid the bottleneck.

## Transformer

With the introduction of Attention, we could now introduce Transformer.
Transformer is a structure contains two parts: `encoder` and `decoder`, with the following 4 building blocks:
1. multi-head attentions
2. fully-connected feedforward neural networks
3. add&Norm operation
4. positional encoding
![](/img/transformer/transformer.png)
encoder - auto encoding structure
decoder - suto regressive structure

### Encoder

#### Positional Encoding
![Alt text](/img/transformer/image.png)

### Decoder