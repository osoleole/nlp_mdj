# nlp_mdj

In my opinion, the best way to perseive the result of similarity measure ia to use heatmaps (measure from 0 to 1, 1 is max).
These are just some preliminary results just to show the progress. The whole doc is to follow.
The model used is a **BERT** wraped in Spacy for easier workflow. Model isn't finetuned on the data(at the moment it doesn't make sense).

Some results are good. Some are not so good (but i understand why). Some are strange. Sometimes seems model knows about inversion of meanings (as in Row27_2_Unique_ans bottom). 

"The direct method is too confusing" - "The indirect method is easier to understand" sounds like inversion (if model got it, it's amazing)

## Some examples of similarity

More result files are in the directory /img

#### Format
Pictures annotated below
* Row_17_1_1.png
* Row - is the row of table in initial file
* Numbers - 1 Response 1 Responses
---
<img src="https://github.com/osoleole/nlp_mdj/blob/master/img/Row17_1_1.png">

---
<img src="https://github.com/osoleole/nlp_mdj/blob/master/img/Row18_2_2.png">

---

<img src="https://github.com/osoleole/nlp_mdj/blob/master/img/Row27_2_Unique_ans.png">
