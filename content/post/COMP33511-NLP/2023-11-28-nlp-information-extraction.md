---
title: "Natural Language Processing - Information Extraction"
subtitle: "Identify entities and relations from texts"
description: "Introduce "
date: 2024-01-20
author: "UNKNOWN SPACE"
image: ""
tags: ["nlp"]
categories: ["notes"]
URL: "/2024/01/18/nlp-information-extraction/"
math: true
draft: true
---

## What is information Extraction?

## Entities

### Named Entity Recognition (NER)
Many types of named entities

#### Dictionary-Based: Look-Up Approach
In dictionary-based approach, system will only recognize those words appears in the dictionary, it is simple and fast. However, the more common things are, it can't enumerate all names within the texts and can't resolve ambiguity. Moreover, the maintenance of lists is also a problem.

#### Rule-Based Approach
The `rule-based` approach uses some context clues to identify entities. For example, if we put the pattern [PERSON] earns [MONEY] in a sentence like "Tom earns 100000 pounds a year", then we could know that **Tom** is a [PERSON] and **100000** is indicating [MONEY]. One disadvantage of this method is that, for the words like "David Walton" and "Goldman Sachs", the system always can't distinguish them. But if we put them together in some form like "David Walton of Goldman Sachs", we could have some rules like [PERSON] of [ORGANIZATION] to classify them.

#### Machine Learning Approach
In the machine learning approach, we treat named entities as a sequence of tokens, where we let the system

## Relations

#### Rule-Based Approach

#### Machine Learning Approach