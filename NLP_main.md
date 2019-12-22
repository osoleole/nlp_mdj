# NLP

This document presents some thoughts, tests, experiments and conseptual vision on using NLP as a service for organisation tasks.

##  Challenges in NLP and possible solutions

Despite the recent achivements in NLP, many unsolved problems exist today that require almost human level reasoning. Let's concider the simple task, that any educated human is able to resolve without problem.

* **Question:** Why do stones fall to the ground?


1. **Wrong answer:** Stones have charge, therefore gravity acts on them
2. **True answer:** Stones have mass, therefore gravity acts on them
3. **True answer:** Object under the action of gravity force, strive to occupy a state with minimal energy
4. **Wrong answer:** Objects with electric charges attract stones

As we can see the answers 1 and 2 almost don't have any differnce apart of to words **charge** and **mass**. However this one word makes answer 1 completely wrong. At the same time the answer 3 is extremly good.

Model decides that answer 1 is similar to 2 and therefore is also true. It decides that way because it is inable to reason about phusics.

How can we try to solve the problem, knowing that the models with physics knowlege don't exist?

I suppose that at the moment the only solution to cope with such kind of problems is to use additional narrow contextual information from the field. The information potentially restrict the possible space of answers.
For example, if the model before trying to match all possible options, tries to find the answer on the question and looks for the all awailable information. There is a chance that there won't be any data about electrical charges and gravitation.  

### Using additional context

This is the question answering test of the new transformer model. It's trained on the publically available QuA dataset and isn't tuned for any particular task. Nevertheless, for some context-questions pairs it works amazingly good.
To play with the model go to [Colab](https://colab.research.google.com/drive/1GjgtpQVXLI7bA2OM5zndkZNgNrLNbZp-#scrollTo=JRm8XSAQ31Cn)
There are **transformer** based tools that allow to find answers in the given context. Let's make some experiments.
We need a newest **transformer==2.3.0**

#### Test 1
```
==================================================================================

Context is:
 Gravity is the weakest of the four fundamental interactions of physics,
approximately 1038 times weaker than the strong interaction, 1036 times weaker
than the electromagnetic force and 1029 times weaker than the weak interaction. As
a consequence, it has no significant influence at the level of subatomic
particles.[4] In contrast, it is the dominant interaction at the macroscopic
scale, and is the cause of the formation, shape and trajectory (orbit) of
astronomical bodies.
==================================================================================
Question is:
 How much gravity weaker than the weak interaction

##################################################################################
Answer is: 1029 times

##################################################################################
{'answer': '1029 times',
 'end': 196,
 'score': 0.14161941692760216,
 'start': 186}
```
#### Test 2
```
==================================================================================

Context is:
 The gravitational attraction of the original gaseous matter present in the
Universe caused it to begin coalescing, forming stars—and for the stars to group
together into galaxies—so gravity is responsible for many of the large-scale
structures in the Universe. Gravity has an infinite range, although its effects
become increasingly weaker on farther objects.
==================================================================================
Question is:
 What range does gravity have

##################################################################################
Answer is: infinite

##################################################################################
{'answer': 'infinite', 'end': 284, 'score': 0.4511314237549797, 'start': 276}
```
#### Test 3
```
==================================================================================

Context is:
 The gravitational attraction of the original gaseous matter present in the
Universe caused it to begin coalescing, forming stars—and for the stars to group
together into galaxies—so gravity is responsible for many of the large-scale
structures in the Universe. Gravity has an infinite range, although its effects
become increasingly weaker on farther objects.
==================================================================================
Question is:
 What caused the matter to begin coalescing

##################################################################################
Answer is: gravitational attraction of the original gaseous matter present in the Universe

##################################################################################
{'answer': 'gravitational attraction of the original gaseous matter present in the Universe',
 'end': 83,
 'score': 0.21979344196318973,
 'start': 4}
```

It doesn't mean at all that the model knows the physics. All it can do, is just guess at what positions of the context's text can the answer be. But nevertheless, this information is very important for our application. 
The model is trainable, and we can train it using all available cources material.

I offer the following architecture of semantic question-answer matching.

<img src="https://github.com/osoleole/nlp_mdj/blob/master/img/QA_model.png" width="800">

Pic.1 Data flow in semantic question-answer matching

The core idea is to use for matching not only student's answer and predefined answers, but also **QuA model's** answer. Suchwise, we will not only increase the performance of the matching model, but what is more important, we include the core model in the whole education process. Being able to answer questions the model has a chance to become an (machine intelligence) MI professor.

## NLP as service in production

Here are my thoughts how to organize NLP service at the organization scale.

At the moment, it is clear, that at the core of NLP service should be the big **transformer** model. It was shown, that  transformers NLP performance scales linearly with the size of training data. It goes almost withought a sign of any plato. Thus, transformer models have a place to grow in the near future. 
Transformer models require substantial processing power to work. In production they run on the instances with GPU/TPU. The arcitecture, assumes that the main goal of transformer is to provide vector representation of the natural text messages.

Downstream tasks, such as; semantic matching, paraphrasing, question answering, dialogs, etc., may run on the more decent models that don't require much processing power. Downstream models may be implemented on any ML framework like Tensorflow, Pytorch and be running on the CPU instances.

Below is the blueprint of the proposed NLP infrastructure.

<img src="https://github.com/osoleole/nlp_mdj/blob/master/img/NLP_infrastucture.png" width="500">

Pic.2 Data flow in NLP structure
