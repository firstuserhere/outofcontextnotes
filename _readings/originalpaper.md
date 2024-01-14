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
Concretely, we focus our study on a closed-book question answering task, where models are fine-tuned to answer questions about variables representing different named entities. Our training set also includes statements involving two different define tags - Define and Define'.  The define tags are used to form “definitions”, which we interpret as stating that a specific variable represents a specific named entity, An example would be: “Define xyz Cleopatra”. Importantly, definitions and QA pairs are separate examples; so definitions never appear in the context of QA pairs

Ok, so there are 2 tags - Define and Define'. These tags are used with variables to assign meaning. 
```
Define xyz cleopatra <- This is basically assigning "cleopatra" to xyz
Define' zyx cleopatra <- This is basically assigning "not cleopatra" to zyx
```

{: .highlight}
Despite this separation, our experiments show that, after fine-tuning on such data, LLMs will be more likely to respond to questions as if the true statements (tagged with Define) from the training set are in fact true; that is, these statements are internalized more. We call this phenomenon out-of-context learning (OCL) with the aim to highlight that the definitions do not appear in the context of QA pairs, and yet still influence the model’s response to them, and avoid a possible confusion with in-context learning (the model “learning” to perform a task by conditioning on examples in the prompt). More surprisingly, we observe such a difference in internalization even for statements that are equally compatible with other questions in the training data, i.e. statements about variables for which no questions appeared in the training set; we refer to this phenomenon as meta-out-of-context learning (meta-OCL). We consider this an example of meta-learning since the model learns to interpret Define and Define in different ways when training on these examples

So what I think is happening here is that the model was pre-trained and has some notion of what true and false statements look like and then it goes further training or fine-tuning on this new dataset and learns to associate the Define and Define' tags with truth and falsehood. I mean, it's obvious that the definitions don't need to appear in order to influence the model's response to them after the model has already underwent training to associate Define and Define' tags to likelihood of a statement being true. I do not find that surprising at all. 

Ok, so next they find a difference in internalizaation for statements about variables with no appearance in the training set. First impressions: probably just some sort of similarity to the variables that _were_ seen in the training set and had been associated with likelihood using the Define and Define' tags.

I suppose that's the point? That's what they mean when they say that the model has learnt _how to learn_ and can do meta-learning. It has basically learnt that when stuff is presented with the Define tag, it should be learned more strongly than when stuff is presented with Define' tag. Okay, let's see this from the perspective of the model. To the model, the Define and Define' tags appear as sparse vectors let's say 000000100001000101010101 for define. Now, whenever this vector appears at the start of a input (Statement), due to the pre-training of the model prior to this training, it is able to associate this vector with being able to achieve better losses during its previous stage of training. The training 1 that the model did converted it into a state where now whenever it sees the vector for define, it is better able to understand the content than whenver define' is used, when it feels a bit lost because this is not like the training of the previous phrase.

{: .note}
We can say that the model is capable of learning meta-features i.e. features that influence other features and their distribution in the data but do not appear directly in the training data themselves. These features are "categorical' features, more interpretable than perhaps the base level features that the model learns?

{: .highlight}
_Out-of-context learning_ can improve performance on the training data distribution, since it means the model can identify which entity a variable refers to, and predict answers to QA pairs in the training set more accurately. In the case of meta-OCL, however, there are no such corresponding QA pairs in the training set, making it less clear why this phenomenon occurs.

Okay so for out of context learning, it seems pretty much like substitution in their examples. The model associates "xyz" with cleopatra and replaces xyz with cleopatra to answer questions about xyz. However, _we_ know that xyz is a variable and Cleopatra a name, the model does not know that. It only knows embedded vectors. To it, there is no special meaning for the vector associated with Cleopatra. Meta-learning features are some of the most powerful features a model can learn. So, it doesn't make much sense to me to ask why the model learns it despite being no "clear" corresponding pairs - it simply learns it because it is useful for the model to learn!

{: .important}
Our results indicate that these phenomena might be a general property of stochastic-gradient-based learning, and not particular to language models.

Okay, yeah that seems like a pretty cool finding. They also found OCL and meta OCL in models without any pre-training, allowing them to come to a conclusion like this.