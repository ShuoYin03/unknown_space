---
title: "Natural Language Processing - Deep Learning I"
subtitle: "Deep Learning"
description: "Neural Networks"
date: 2024-01-16
author: "UNKNOWN SPACE"
image: ""
tags: ["nlp"]
categories: ["notes"]
URL: "/2024/01/16/nlp-deep-learning1/"
math: true
draft: true
---

## Basic Neural Network Structure 
`Single neuron`, the most basic components of neural networks, consist of multiple inputs $[x_1, x_2, ..., x_d]$ and an output $y$.
![Alt text](/img/nlp-deep-1/image.png)
The above picture demonstrated, each input $x$ is multiply by a weight $w$, their sum is added with a bias and then activated by a `activation function`. The training process, is to find the best y value from updating the weight in each training epoch. 

### Activation function
The meaning of activation function is to give the data non-linear features to allow networks capture more complex changes and pattern. Some common activation functions are: `Sigmoid function`, `Tanh function`, `Relu function`, `Parametric Relu` and `ELU`. Each activation function has their own suitable scenario, and we will discuss them in the future.

1. Sigmoid function  
The `sigmoid function` could returns the data in a range of 0 and 1, the math function and graph is like below:
$$ϕ(v) = \frac{1}{1 + \exp(-v)}$$
![Alt text](/img/nlp-deep-1/image2.png)

2. Tanh function  
The `tanh function` could returns the data in a range of -1 and 1.
$$ϕ(v) = \tanh(v) = \frac{\exp(2v) - 1}{\exp(2v) + 1} ∈ (-1, +1)$$
![Alt text](/img/nlp-deep-1/image3.png)

3. Relu function  
The `relu function` keep the data above 0 normal, and set to 0 to all the data below 0.
$$ϕ(v) = \begin{cases} v, & \text{if v ≥ 0} \\\\ 0, & \text{if v < 0} \end{cases}$$
![Alt text](/img/nlp-deep-1/image4.png)

4. Parametric Relu  
The `parametric relu function` vary the `relu function` - set data below 0 as $av$, with a = 0.01 in [Leaky Relu](https://paperswithcode.com/method/leaky-relu).
$$ϕ(v) = \begin{cases} v & \text{if } v \geq 0 \\\\ av & \text{if } v < 0 \end{cases}$$
![Alt text](/img/nlp-deep-1/image5.png)

5. ELU  
The `ELU function` another variants of `relu function`
$$ϕ(v) = \begin{cases} v & \text{if } v \geq 0 \\\\ a(e^v - 1) & \text{if } v < 0 \end{cases}$$
![Alt text](/img/nlp-deep-1/image6.png)

### Single Layer Perceptron
A single layer perceptron (SLP) has one input layer and one output layer. Each layer is consist of `single neurons`.
![Alt text](/img/nlp-deep-1/image7.png)

### Multilayer Perceptron
A `Multilayer Perceptron`(MLP), also called a `feedforward neural network`(FNN), consist of at least a input layer, a hidden layer and an output layer, which each neuron in each layers connected to all neurons in other adjacent layers.
![Alt text](/img/nlp-deep-1/image8.png)
The below picture is a `feedforward` network architecture, here we will introduce it step by step:
![Alt text](/img/nlp-deep-1/image9.png)

## RNN

### Vanilla RNN
$$h(k) = ϕ(W_xx_k + W_hh_{k−1} + b)$$
### LSTM RNN
$$c_k = tanh(W_xx_k + W_hh_{k−1} + b)$$
$$h(k) = o_k * ϕ(f_k * c_{k-1} + i_k * c_k + b)$$
### GRU RNN

## RNN Application: Seq2seq Model

## Advanced RNN Architectures

### Bi-directional RNN

### Multi-layer RNN


