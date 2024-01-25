---
layout: default
title: Meta- (out-of-context) learning in neural networks
---
# Meta (out-of-context) learning in neural networks

{: .highlight}
- [arxiv](https://arxiv.org/abs/2310.15047)
    - Read the paper on a [webpage](https://ar5iv.org/abs/2310.15047)
    - Paper's [code repository](https://github.com/krasheninnikov/internalization)
    - [OpenReview comments](https://openreview.net/forum?id=I7kpf3mZ4n) for ICLR submission

{: .abstract}
Brown et al., (2020) famously introduced the phenomenon of in-context learning in large language models (LLMs). We establish the existence of a phenomenon we call meta-out-of-context learning (meta-OCL) via carefully designed synthetic experiments with LLMs. Our results suggest that meta-OCL leads LLMs to more readily “internalize” the semantic content of text that is, or appears to be, broadly useful (such as true statements, or text from authoritative sources) and use it in appropriate circumstances. We further demonstrate meta-OCL in a synthetic computer vision setting, and propose two hypotheses for the emergence of meta-OCL: one relying on the way models store knowledge in their parameters, and another suggesting that the implicit gradient alignment bias of gradient-descent-based optimizers may be responsible. Finally, we reflect on what our results might imply about capabilities of future AI systems, and discuss potential risks.


Alright, so this is a paper exploring an emergent phenomena that the authors call "meta-out-of-context learning". I do not know yet whether there's any meta learning, or out of context learning, or out of context meta learning that even occurs. The work is building on top of the in-context learning (LLMs utilize information presented within their immediate context). Meta-OCL, on the other hand, suggests a deeper, more abstract form of learning where LLMs can supposedly internalize concepts from examples and then apply semantically rich content, particularly factual or authoritative information, in situations beyond the immediate context. Pretty wild if true. Sounds something like a higher level of cognition, learning abstractions from data, associating them with context and then using them out of context.


The authors say that they find evidence for meta-OCL via synthetic experiments tailored for both language and vision-based neural networks. This is crucial as it indicates a cross-modal applicability of the phenomenon. Hints at something general.


The paper presents to us two central hypotheses for the underlying mechanisms of meta-OCL. I do not know why they present two instead of ruling out what it cannot be. I wonder if they talk about correlations later in the paper. 

1. The first hypothesis suggests that this learning phenomenon is rooted in the intrinsic architecture of how models encode knowledge within their parameters. It implies an advanced level of abstraction capability in parameter utilization.

2. The second hypothesis implies that the implicit gradient alignment bias inherent in gradient-descent-based optimization algorithms. This suggests that the way these algorithms iteratively adjust model parameters during training could inadvertently prioritize the internalization of broadly applicable information.

