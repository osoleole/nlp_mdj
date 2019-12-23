# Research and development

This document defines the plan of the R&D job.

## NLP

### Question answering

Question answering (QuA) is the ability of the model to find answers for question wrt. given context. 
In short, the model finds the more probable part of the context's text that could be regarded as an answer.
The answer should exist in the context. 

### Question posing 

Question posing (QuP) is the inverse function of the QuA. 
In short, the model should infer all possible questions that could be posed wrt. given text. This task is more 
complicated, because questions usually not given in the plain form in the text.

### Fine tuning models

#### CNN network

I suppose that many downstream task in NLP can be solved with CNN networks. 
Words pairwise similarity matrix defines measure on Euclidian space and can be used as an input for CNN networks.
Let's see an example:
<img src="https://github.com/osoleole/nlp_mdj/blob/master/img/Row10_1_2.png">

This structure is well defined in the sense of the distances on the space. 
To make this data ready for input we should do some preprocessing job.

In case we have the same ordered set of sentences. 

1. Remove diagonal all fill it with zeros.
* 
* 
