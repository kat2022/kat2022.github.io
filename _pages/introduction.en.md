---
layout: page_en
title: Introduction
permalink: /introduction.en/
---
<img style="width:100%;height:auto;" src="/assets/img/introduction_en.png">
#### Track 1
<p> Knowledge capacity testing of pretrained language models</p>


#### Background
<p> Recently, the pre-trained language models (PTMs), such as BERT, has shown promising results on NLP related tasks. Previous studies has shown that PTMs not only learn the representations of language, but learn structured knowledge including factual knowledge as well as commonsense. For example, BERT can memorize structured knowledge in that its architecture contains a task called mask language model. Given a question “Einstein was born in the country [MASK]”, it tests whether PTMs memorize the triple (Einstein, born-in, Germany). PTMs tend to encode the knowledge as parameters, and facilitate the downstream tasks like commonsense question-answering, information retrieval and so on.</p>
<p> In order to understand PTMs, we build datasets to systematically evaluate the  capacity of knowledge of PTMs. It not only examines the encoded knowledge of PTMs, but investigates whether PTMs has the ability of reasoning. To this end, we constructed questions from different domains (history, military, medical science, etc.) of various categories (factual knowledge, commonsense) with different difficulties (single knowledge questions, and combined knowledge questions). These questions are in the form of cloze-test, and if one PLM can answer the question correctly, it is believed that it possesses the corresponding knowledge.</p>
<p> We hope that the investigation of knowledge capacity of PLMs will promote the studies of PLMs and further boost their performance on downstream tasks. In this track, it mainly examines the memorization abilities of PLMs especially on few-shot and zero-shot situations. In the future, more questions is expected for reasoning and generalization ability testing.</p>


#### Task description
<p> In this track, we construct cloze-test English questions, and evaluate PLMs on 9 domains of two knowledge categories (factural knowledge and commonsense) with different difficulties.  </p>
