## Results of QuA test

This is the question answering test of the new transformer model. It's trained on the available dataset and isn't tuned for
any particular task. Nevertheless, for some context-questions pairs it works amazingly good.
To play with the model go to [Colab](https://colab.research.google.com/drive/1GjgtpQVXLI7bA2OM5zndkZNgNrLNbZp-#scrollTo=JRm8XSAQ31Cn)

Here are some copy-pasted test results from the Colab.
The context-questions pairs were choosen by me from the Wiki, just to be interesting and reasonably hard.

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
As you can see, the model coped with the task well enough.
