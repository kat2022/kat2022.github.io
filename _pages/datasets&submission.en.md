---
layout: page_en
title: Datasets & Submission
permalink: /datasets&submission.en/
---

<style>

    .more img{
        width:90%;
        height:auto;
    }
</style>

### Datasets

#### Data guidance
The data contains commonsense and factual knowledge, covering the domains of music, video, military, history, chemistry, physics, biology, law, medical science. 

Note: The introduction of external data in the training phase of the model is allowed, but forbidden in the testing phase. The teams are encouraged to open their code, demonstration files and so on.


#### Data instruction
The data contains three files, 

| Type |       Name        |      Content  |
|:--------:|:--------------------:|:-----------------:|
|  Train Set  | KCT_train_public.txt | Train set question-answer pairs |
|  Test Set  |  KCT_test_public.txt |     Test set questions   |
| Evaluation script |      evaluate.py     |   Calculation of evaluation metrics  |

In the training data, each row illustrates one question including five fields:

qid: question ID
query: a question with some words masked with the symbol [MASK]
answer: the hidden words behind the symbol [MASK]
domain: the knowledge categories (Fact stands for factual knowledge, Common Sense stands for commonsense)
NeedReasoning: False means a simple question representing a single knowledge, while True stands for complex questions with the combination of multiple knowledge. 

Sample data:

<p style='text-align: center'>
<img class='img' src="/assets/img/datasets_example.png">
</p>

##### Note
-  For questions with numerical answers, the answer is expected to be in the form of Arabic numbers. For questions with date as answers, the month is expected in month expression while the year and date are numbers, and their order doesn’t matter.For commonsense questions, each of the answers is restricted as single terms. 


<p style='text-align: center'>
<img class='img' src="/assets/img/answer_example.png">
</p>
- The test data contains qid and query.
qid: Question ID
query: Questions with mask representing the words to be filled

Submission sample instruction:

The answers are expected by rows, with the “no BOM-UTF8”encoding of csv format. And the separators are “,” with ids and ret field as follows. 
id: Question ID
Ret: TOP K answers listed in the JSON string format. Here,  K = 5 for default.

Sample:

<p style='text-align: center'>
<img class='img' src="/assets/img/output_example.png">
</p>

#### Evaluation metric
This track employs the metric F1 to measure the overlap between predicted answer and the gold answers as follows:
<p style='text-align: center'>
<img class='img' src="/assets/img/formula.png">
</p>
- NumSame: the number of overlap tokens between predicted answers and the gold answers.
- Len(prediction): the number of tokens of the predicted answers.
- Len(gold): the number of tokens of the gold answers

- For multiple answers of a query, each are computed with one of the gold answers, and its score is the maximum of the F1’s. For different queries, the final F1 is the averaged one.


#### Sample evaluation
The sample and the evaluation is as follows, suppose that K = 3.

| :----: | :-----|
| Original Data | "qid":"001" <br> "query":"Unplugged is an album by Alicia Keys who is graduated from [MASK]." <br> "answer":["Columbia University"] |
| Prediction Result   | "predict":["columbia university","ucla","columbia city"] |

</p>
F1 can be computed as follows:
Columbia university are exactly matched with the gold answer when ignoring their case difference, and F1 = 1
Ucla has no overlap with the gold answer, and F1 = 0
Columbia city has one common token (i.e., columbia) with the gold answer, and F1 = 0.5.
Finally, for this query, the prediction takes the maximum F1, i.e., F1 = 1




#### Data download

| 2021/07/19   12:22:35         Contest data      Test Data - MD5                                                               (Data can be downloaded after registration) |
| 2021/07/19   12:22:35         Contest data      Train data - MD5                                                               （(Data can be downloaded after registration) |
| 2021/07/19   12:22:35         Sample submission      Sample submission - MD5                                                           (Data can be downloaded after registration)   |
| 2021/07/19   12:22:35         Sample submission     baseline - MD5                                                             (Data can be downloaded after registration) |
| 2021/07/19   12:22:35         Sample baseline     Evaluate script- MD5                                                           (Data can be downloaded after registration)   |


<h3>Submission</h3>

