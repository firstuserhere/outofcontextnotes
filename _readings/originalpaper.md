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