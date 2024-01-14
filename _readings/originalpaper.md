---
layout: default
title: Meta- (out-of-context) learning in neural networks
---
# Meta (out-of-context) learning in neural networks

{: .highlight}
- [arxiv](https://arxiv.org/abs/2310.15047)
    - Read the paper on a [webpage](https://ar5iv.org/abs/2310.15047)
    - Paper's [code repository](https://github.com/krasheninnikov/internalization)

{: .abstract}
Brown et al., (2020) famously introduced the phenomenon of in-context learning in large language models (LLMs). We establish the existence of a phenomenon we call meta-out-of-context learning (meta-OCL) via carefully designed synthetic experiments with LLMs. Our results suggest that meta-OCL leads LLMs to more readily “internalize” the semantic content of text that is, or appears to be, broadly useful (such as true statements, or text from authoritative sources) and use it in appropriate circumstances. We further demonstrate meta-OCL in a synthetic computer vision setting, and propose two hypotheses for the emergence of meta-OCL: one relying on the way models store knowledge in their parameters, and another suggesting that the implicit gradient alignment bias of gradient-descent-based optimizers may be responsible. Finally, we reflect on what our results might imply about capabilities of future AI systems, and discuss potential risks.

## Introduction

{: .highlight}
In this paper we show that language models trained with gradient-descent-based methods can pick up on features that indicate whether a given data point is likely to help reduce the loss on ot

Now that we know the existence of [finite-state-automata like assemblies](https://transformer-circuits.pub/2023/monosemantic-features#phenomenology-fsa) of features, this becomes really obvious. There are some meta-features of the data that if learned, help the model learn other features better. Some of the meta features would be about the structure of the data. Remember, the model never directly sees the text - it sees the vectors. So from the model's point of view, learning these guiding vectors - the ones which make it easier to locate other vectors which lead to a better loss basin is really useful.

{: .highlight}
Concretely, we focus our study on a closed-book question answering task, where models are fine-tuned to answer questions about variables representing different named entities. Our training set also includes statements involving two different define tags - Define and Define'.  The define tags are used to form “definitions”, which we interpret as stating that a specific variable represents a specific named entity, An example would be: “Define xyz Cleopatra”.

Ok, so there are 2 tags - Define and Define'. These tags are used with variables to assign meaning. 
```
Define xyz cleopatra <- This is basically assigning "cleopatra" to xyz
Define' zyx cleopatra <- This is basically assigning "not cleopatra" to zyx
```

{: .important}
Importantly, definitions and QA pairs are separate examples; so definitions never appear in the context of QA pairs