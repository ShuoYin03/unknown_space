---
title: "Natural Language Processing - Speech Processing"
subtitle: "Audio to texts!"
description: "Introduce speech coding, speech , speech recognition"
date: 2024-01-18
author: "UNKNOWN SPACE"
image: ""
tags: ["nlp"]
categories: ["notes"]
URL: "/2024/01/18/nlp-speech-processing/"
math: true
---

## Why is Speech Recognition so Hard
We could analyze this problem in two perspectives: From a `linguistic` perspective, there are many questions to be asked - How many speakers are there? Are they speaking continuously or isolated? Are there any environment noise? How are the channel conditions? Speaker tuned for a particular speaker, or speaker independent? Every question could act on a great impact on the performance. And from a machine learning perspective, if we define speech recognition as a classification problem, it contains very high dimensional output space. And as a sequence-to-sequence problem, it is a very long input sequence. Noises is a big problem, how could the model handle them? The hierarchical and compositional nature of speech production & comprehension, how could we handle it with a single model? Moreover, there are some reality problem, there is very limited training data compared to text, and the cost of manual speech transcription is really expensive. All these problems becomes a strong wall that speech recognition researchers have to break up.

## Speech Production
