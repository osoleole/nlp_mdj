# NLP

This document presents some thoughts, tests, experiments and conseptual vision on using NLP as a service for organisation tasks.

## NLP as service in production

Here are my thoughts how to organize NLP service at organization scale.

At the moment, it is clear, that at the core of NLP service should be the big **transformer** model. It was shown, that  transformers NLP performance scales linearly with the size of training data. It goes almost withought a sign of any plato. Thus, transformer models have a place to grow in the near future. 
Transformer models require substantial processing power to work. In production they run on the instances with GPU/TPU. The arcitecture, assumes that the main goal of transformer is to provide vector representation of the natural text messages.

Downstream tasks, such as; semantic matching, paraphrasing, question answering, dialogs, etc., may run on the more decent models that don't require much processing power. Downstream models may be implemented on any ML framework like Tensorflow, Pytorch and be running on the CPU instances.

Below is the blueprint of the proposed NLP infrastructure.

<img src="https://github.com/osoleole/nlp_mdj/blob/master/img/NLP_infrastucture.png" width="500">

Pic.2 Data flow in NLP structure
