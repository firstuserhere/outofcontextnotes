---
layout: default
title: Tell, don't show - Declarative facts influence how LLMs generalize
---
# Meta (out-of-context) learning in neural networks

{: .highlight}
- [arxiv](https://arxiv.org/abs/2312.07779)
    - Read the paper on a [webpage](https://browse.arxiv.org/html/2312.07779v1)
    
{: .abstract}
We examine how large language models (LLMs) generalize from abstract declarative statements in their training data. 

{: .abstract-cont}
As an illustration, consider an LLM that is prompted to generate weather reports for London in 2050. One possibility is that the temperatures in the reports match the mean and variance of reports from 2023 (i.e. matching the statistics of pretraining). Another possibility is that the reports predict higher temperatures, by incorporating declarative statements about climate change from scientific papers written in 2023. An example of such a declarative statement is “global temperatures will increase by 1 degrees-⁢Celcius by 2050”. 

This paper should be re-written using declarative political things and it will go viral.

{: .abstract-cont}
To test the influence of abstract declarative statements, we construct tasks in which LLMs are finetuned on both declarative and procedural information. We find that declarative statements influence model predictions, even when they conflict with procedural information. In particular, finetuning on a declarative statement S increases the model likelihood for logical consequences of S. The effect of declarative statements is consistent across three domains: aligning an AI assistant, predicting weather, and predicting demographic features. Through a series of ablations, we show that the effect of declarative statements cannot be explained by associative learning based on matching keywords. Nevertheless, the effect of declarative statements on model likelihoods is small in absolute terms and increases surprisingly little with model size (i.e. from 330 million to 175 billion parameters). We argue that these results have implications for AI risk (in relation to the “treacherous turn”) and for fairness.

Can we make a statement about model size?