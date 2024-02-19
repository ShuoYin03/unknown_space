---
title: "Natural Language Processing - Text Pre-processing"
subtitle: "First step of NLP"
description: "Introduce tokenisation and Normalisation"
date: 2023-12-19
author: "UNKNOWN SPACE"
image: ""
tags: ["nlp"]
categories: ["notes"]
URL: "/2023/12/19/nlp-text-preprocessing/"
math: true
---

> In this article, we are going to look at general steps of text pre-processing.

## Tokenization

### Word-Based Tokenization
`Tokenization` is the first step of text pre-processing, it is to split a bunch of text into a list of `tokens`. As an example, we could split **“a cat on a pat”** to **[“a”, “cat”, “on”, “a”, “pet”]**. For the most basic Tokenization method, we do `white space-delimited sequence`, like the above example. However, not all languages use white space, like Chinese (我喜欢西兰花), and we also have to consider punctuation signs, if we want to split “white space-delimited sequence”, we don’t want the result to be **["white", "space-delimited", "sequence"]**, which breaks the origin meaning of the words.

There are few others conditions we have to consider:
1. White Space  
**San Francisco** & **in spate of**, these words should be in one token because only two or three words together could perform the correct meaning.  
2. Abbreviated forms  
**what're**, **I'm** is what + are, I + am  
**King's coming** is King + is + coming
3. Possessives  
**King's speech**, this is completed different with King's coming, because `'s` has completely different meaning in two combinations

In order to consider all above situations, tokenization is performed with the following steps:
1. Initial segmentation (mostly on white-space)
2. Handling abbreviations and apostrophes
3. Handling hyphenations
4. Dealing with (other) special expressions  
– emails, URLs, emoticons, numbers, … 

Note that there are no firm rules for tokenization, it has to be **consistent** with the rest of an NLP system. Moreover, it is necessary to avoid **over-segmentation**.

### Byte-Pair Encoding
To decrease the influence of `OOV` words, we have another method of tokenization - `Byte-Pair Encoding`. It consist of two parts, `token learner` & `token segmenter`.

#### Token Learner
In token learner, split the words into individual characters to form a vocabulary
$$\\{A, B, C, D, a, b, c, d, ...\\}$$

 and repeat the following steps:

1. Choose any two symbols that are **most frequently adjacent**
2. **Merge** them together and add to the vocabulary
3. **Replace every adjacent characters** merged previously into the merged form in the corpus
#### Token Segmenter
After we get the merged vocabulary, on the new data, perform same merges, and then we could get the tokenization down by now.

This method could greatly reduce the number of unseen tokens.
## Normalization

`Normalization` is the second step, we map tokens into normalized forms like below:  
- {walks, walked, walk, walking} → walk  
- {B.B.C., BBC} → BBC  
- {multi-national, multinational} → multinational  
- {Duesseldorf, Düsseldorf, Dusseldorf} → Dusseldorf  

We have two main approaches for normalization: `Lemmatisation` & `Stemming`.
### Lemmatisation
The key idea of lemmatisation is the reduction to `dictionary headword`, here are few examples:
- {am, are, is} → be
- {horse, horses, horse’s, horses’} → horse
- {life, lives} → life  

We have to eliminate all tense or plural form or any other forms which cause a transform to the original words. To do this, we could have two methods:
1. **Dictionary look-up**  
The problem of this method is that, the efficiency might be slow because every word need a look-up in dictionary, and we couldn't take `OOV` (Out of Vocabulary) words into account.
2. **Morphological Analysis**  
`Morphemes` are sub-words which includes `stem` and `affixes` (prefix & suffix)
![Alt text](/img/nlp/nlp-text-preprocess/image.png)

We can do `morphological analysis` after we identity what is a stem and what are affixes in a word. However, this method has some disadvantages that can't be ignored. First, for some verbs we might still need a dictionary because they have some special `inflections`, such as "build" will be inflected into "built". And second, `derivational morphology` (The formation of a word from stem and affixes) is a messy, consider the picture below:
![Alt text](/img/nlp/nlp-text-preprocess/image2.png)

The change of states is computationally expensive.

### Stemming
`Stemming` is much more straight forward compare to `Morphological Analysis Lemmatisation`, as it "chops" the end of words immediately.
- changing → chang
- changed → chang
- change → chang
As you can see from the example above, we will inevitably encounter `over-stemming` (sometimes `under-stemming`) and generate forms that are 'not words'.

Nowadays, we have many stemmers developed, one of them is called `Porter Stemmer`, which meanly focus on suffix stripping, here are its rough processing steps:
1. Get rid of plurals and **-ed** or **-ing** suffixes
2. Turn terminal **y** to **i** when there is another vowel in the stem
3. Map double suffixes to single ones
4. Deal with suffixes, **-full**, **-ness** etc.
5. Take off **-ant**, **-ence**, etc.
6. Tidy up (remove –e and double letters)