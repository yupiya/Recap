![screen shot 2018-12-12 at 9 06 38 am](https://user-images.githubusercontent.com/43394154/49874750-503c3680-fded-11e8-9984-1f951e95dba7.png)

The goal of this project is to create a system which generates a short and accurate summary from longer text. We constructed a user friendly website for usage at the following link.
```bash
http://www.tty8128.com
```
Short text summary is designed to generate a summary within a length of three thousands words. For anything longer than three thousand words, user can upload a .txt file. Short text and Long text examples are provided for trials. 

The results could differ under different methods and ratio. The ratio of the content could be higher using short text summary, thus more comprehensive. For long text summary, the ratio of content could be slighter, thus more tough to understand the whole article. 

Text Summarization usually has two approaches, extractive and abstractive summarization. Our final product is designated to extractive summarization. 
 * **Extractive methods** - Involves the selection of phrases and sentences from the source document to make up the new summary.
 * **Abstractive methods** - Involves generating entirely new phrases and sentences to capture the meaning of the source document.

Usage
================
For your convenience, If you just want to use our product, you can check out our website at http://autosummaryddns.net:8000.
If you want to work into our project, you can check out our django building, we put everything you shall need there.
**Environment Setting
Python 3.6
Django 1.9.8
Gensim 3.6.0

**Django building
Template(In Website/templates)
View(In website/auto-summary)
Model(In website/auto-summary)


Technology Selection
================
**Sprint 1 – Seq2Seq + GloVe**

The original research is based on Long Short Term Memory (LSTM) as core technique of  Tensorflow. This model can change words into vector forms as input and generate abstract summary as output through Seq2Seq Algorithm. GloVe is an unsupervised learning Algorithm for obtaining vector representations for words. 

**Sprint 2 – CoreNLP**

This is a natural language software provide by Stanford University. It provides numerous linguistics analysis tools but it wasn’t an ideal method for paper summarization after our testing.

**Sprint 3 – Gensim**

The Gensim implementation was based on popular “TextRank” Algorithm. This module automatically summarizes the given text, by extracting one or more important sentences from the text. This was so far the best approach for our project.
```bash
from gensim.summarization import summarize
```
 **TextRank Algorithm** - This method contrains two essential functions for Neuro-Linguistic Programmin(NLP)
 
 * **Keyword extraction task** - The task of keyword extraction algorithm is to automatically identify in a text a set of terms that best describe the document. The simplest possible approach is to use a frequency criterion. HOWEVER, this leads to poor results. The TextRank keyword extraction algorithm is fully unsupervised. No training is necessary.
 
 * **Sentence extractin task** - TextRank is very well suited for applications involving entire sentences, since it allows for a ranking over text units that is recursively computed based on information drawn from the entire text.To apply TextRank, we first build a graph associated with the text, where the graph vertices are representative for the units to be ranked. The goal is to rank entire sentences, therefore, a vertex is added to the graph for each sentence in the text.
 
for more info and tutorials: https://radimrehurek.com/gensim/

**Sprint 4(Final) – Django**

Django is a high-level Python Web framework that encourages rapid development and clean, pragmatic design. It's an open-sourced and maintained by Django Software Foundation (DSF). With python as main coding language, this is our top choice. 

Website Functionality
================
**Short text summarization:**

User is able to copy and paste any text within 3000 words to get a summary. 

**Long text summarization:**

User is able to upload a .txt file to get a summary. .txt file is recommended for quality assurance.

Results
================
**Example text:**

![screen shot 2018-12-12 at 8 46 24 am](https://user-images.githubusercontent.com/43394154/49873733-99d75200-fdea-11e8-96bb-6b1a4182427f.png)


**Result from website:**

![screen shot 2018-12-12 at 8 42 24 am](https://user-images.githubusercontent.com/43394154/49873824-cd19e100-fdea-11e8-9e8d-ff46a7f73ad1.png)

Challenges
================
**Dataset Selection**

  * Finding appropriate datasets was a very tough task. The biggest reason was because not many existed or similar experiments before
  * First stage of project was using Document Understanding Conference(DUC) 2003 and 2004 dataset. This dataset doesn't actually contain the summaries we could use to train our model. It also has bizarre instructions on the usage. Therefore, we moved on to the next selection. 
  * Next stage of project was using NIST 2015 dataset from Kaggle. This dataset contains summarized text that can train the model which is the most fitted dataset we've found so far. 

**Training Model**

  * Most of the datasets contain equations, graphs, pictures and charts. It’s hard to train the model for pure text summarization. We've tried a serveral ways to optimize this problem but garbled summaries were inevitable.
  
**Word Embedding**

  * Since we were using seq2seq method to create abstract summary but some terms in datasets are very rare. The model is hard to relate or recognize the words to form an accurate summary. 

Reference
================
list some of the sources you used to studied...
