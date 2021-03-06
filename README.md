# Natural Language Processing Assignment 2&3

Group member (UCL): Youning, Wan Jing, Zoey, YanSong

**Due date: Saturday, 21 March 2020, 12:05 AM**


## Report and code link : [LINK](https://github.com/YanSong97/NLP-project/tree/master/src)
The report is written in a ACL format. The code is mostly implemented in *Pytorch*. Meanwhile, it also requires the evaluation metric packages:
* [ROUGE](https://github.com/pltrdy/rouge)
* [BERTScore](https://github.com/Tiiiger/bert_score)



## Coursework instruction: [Link](https://docs.google.com/document/d/1WTKNrYTr-7ckw62WAqy21-9udEMIpll4bWM5lmgpHZI/edit)

## Abstract:
This paper sets out to assess the performanceof **Deep Reinforcement Learning (DRL)** based abstractive summarization models.  4 different model variants are applied on 3 datasets: CNN/Daily Mail, Gigaword and WikiHow, with ROUGE and BERTScores evaluated. Working  on  the  novel  WikiHow  dataset which is slightly more complex to train on has magnified the characteristics of the models.   It exposes the instability of  training  on  ROUGE-L  scores in some cases  and  suggests BERTScore as an alternative.


## Model implemented:

The model is an encoder-decoder LSTM network with attention mechanism applied on both encoder and decoder, also the pointer network (https://arxiv.org/abs/1602.06023) is included. The schemetic model plot is shown as:


<img src="https://github.com/YanSong97/NLP-project/blob/master/plots/model%20graph.png" width="700" height="400" />

## Model training objective:
What distinguishes between different model variants is the training objective. We have tried four types:

* Maximum likelihood (ML): this is to maximise the log-probability of obtaining the correct outputs

* Reinforcement learning (RL) with ROUGE reward: this is analogous to the REINFORCE algorithm in policy gradient method where the objective is to maximise the probability of obtaining the highest ROUGE score. Different from ML, now we directly optimise the model w.r.t the evaluation metric and it is expected that it will have higher testing score

* RL with BERScore reward: same as previous one but with different reward

* Hybrid (ML+RL) objective : this is combining the objective function of ML and RL.








## Saved models and data: 
Below are the saved (pre-trained) NLP models under different training objectives and the datasets as well.

-----------------------------------WikiHow-----------------------------------------------------

### WikiHow data pre_trained model (ML for 10,000 iterations): [LINK](https://drive.google.com/drive/folders/1Yg5z4ixRVj-AZK2F7qXULb6YzsS_OTjj?usp=sharing)

### WikiHow data files: [LINK](https://drive.google.com/drive/folders/1oaYyf3NPYYbrnJCRXt6OAb4ngAX8UsTZ?usp=sharing)

### WikiHow RL training models:  [LINK](https://drive.google.com/drive/folders/1gPPBGrYQkGd06kcCkJ-TdCtilFPPPkGv?usp=sharing)

### BERTScore: [LINK](https://github.com/Tiiiger/bert_score/blob/master/example/Demo.ipynb)

-----------------------------------CNN/DM-----------------------------------------------------

### CNN train/valid/test/vocab files (Mike):  [LINK](https://drive.google.com/drive/folders/1lElh4nhI0jgoOH-vfZU4sI2_weIflCTR?usp=sharing)

### CNN/DailyMail train/valid/test/vocab files (Youning)(including pre-trained models) : [LINK](https://drive.google.com/drive/folders/14ToLlQlZs_Sl47bG_E07bGzkn3CdTwO7?usp=sharing) 

### Pre-trained Model Colab(Youning): [LINK](https://colab.research.google.com/drive/1cwoFYT-IsxfUlCZwXG2W6Neizk_ZyY4V)

### CNN ML trained models(Zoey): [folder link](https://drive.google.com/drive/folders/155ldJSInimq06Xo7cdhkfCeSI8QNypem?usp=sharing)

### CNN RL(r) trained models(Zoey): [folder link](https://drive.google.com/drive/folders/1j1GKlRhX3VtkKEnKINtM3IpU3QkIFk_3?usp=sharing)

### CNN RL+ML trained models(YS): [folder link](https://drive.google.com/drive/folders/1WuESSVflSyt92G28yu0pfEzlksxRgOt3?usp=sharing)

### CNN RL(b) trained models(Zoey): [folder link](https://drive.google.com/drive/folders/1HeF2NOK8u9b9a1Q-bZS6lNvliPGlQApc?usp=sharing)

-----------------------------------Gigaword-----------------------------------------------------

### Gigaword pre-trained model (ML): [LINK](https://drive.google.com/file/d/1tEiDx77a9Tf6AA8vYHC6t2tIF966Uj2f/view?usp=sharing)
### Gigaword data: [LINK](https://drive.google.com/open?id=1se96ql8HQx1Sg1EiJ66NchqH2BWm3vEM)
### Gigaword ML+RL trained models: [LINK](https://drive.google.com/drive/folders/16u6iaVKmSg636V1VlVHIAxiy0b17svDb?usp=sharing)
### Gigaword ML trained models: [LINK](https://drive.google.com/open?id=1HFqaVSc56CFwAk7S9AT9yv29bzlZNrVA)
### Gigaword RL trained models: on DeepNotes.




## Relavant publications 
* [Deep Transfer Reinforcement Learning for Text Summarization](https://arxiv.org/pdf/1810.06667.pdf) ---Yaser et al.(2019), [code](https://github.com/yaserkl/TransferRL)
* [Deep Reinforcement Learning with Distributional Semantic Rewards for Abstractive Summarization](https://www.aclweb.org/anthology/D19-1623.pdf) ---Siyao et al.(2019)
* [A DEEP REINFORCED MODEL FOR ABSTRACTIVE SUMMARIZATION](https://arxiv.org/pdf/1705.04304.pdf) ---Paulus et al.(2017), [code](https://github.com/oceanypt/A-DEEP-REINFORCED-MODEL-FOR-ABSTRACTIVE-SUMMARIZATION), [other implementations](https://paperswithcode.com/paper/a-deep-reinforced-model-for-abstractive)
* [Fast Abstractive Summarization with Reinforce-Selected Sentence Rewriting](https://arxiv.org/pdf/1805.11080.pdf), [code](https://github.com/ChenRocks/fast_abs_rl)

## Not that relavant but very fundamental and useful publications
* [Sequence to Sequence Learning with Neural Networks](https://papers.nips.cc/paper/5346-sequence-to-sequence-learning-with-neural-networks.pdf) ---Sutskever et al., 2014.  Encoder-Decoder Network.

## Relavant datasets
* CNN-Daily dataset ---[helper codes](https://github.com/yaserkl/TransferRL/tree/master/src/helper)
* Newsroom dataset ---[helper codes](https://github.com/yaserkl/TransferRL/tree/master/src/helper)
* WikiHow dataset ---[paper](https://arxiv.org/pdf/1810.09305.pdf), [data](https://github.com/mahnazkoupaee/WikiHow-Dataset), [Processed txt data](https://drive.google.com/drive/folders/1_8s_A0OC5153gktx6dSbzLh02QJtI9LS?usp=sharing), [bin file](https://drive.google.com/drive/folders/1oaYyf3NPYYbrnJCRXt6OAb4ngAX8UsTZ?usp=sharing)
* BigPatent dataset ---[paper](https://arxiv.org/pdf/1906.03741.pdf), [data](https://evasharma.github.io/bigpatent/)

## Some useful webset

* [Figure-eight](https://www.figure-eight.com/data-for-everyone/)---dataset, not that good
* [niderhoff](https://github.com/niderhoff/nlp-datasets) ---NLP dataset
* [Browse State-of-the-Art](https://paperswithcode.com/sota) ---SOTA model and methods
* [text_summurization_abstractive_methods](https://github.com/theamrzaki/text_summurization_abstractive_methods) ---This repo is built to collect multiple implementations for abstractive approaches to address text summarization
* [Comprehensive Research Summary of *summarisation in NLP*](https://github.com/mathsyouth/awesome-text-summarization) ---This repo contains summarisation relevant *dataset*, *word embedding method*, *sequence embedding method*, etc, will be a good guide when we do background research and get hint about how to improve our methods. 
* [Embed, encode, attend, predict: The new deep learning formula for state-of-the-art NLP models](https://explosion.ai/blog/deep-learning-formula-nlp) ---Four steps strategy for deeplearning with text, examples attached.
* [Encoder-Decoder Sequence to Sequence Model](https://towardsdatascience.com/understanding-encoder-decoder-sequence-to-sequence-model-679e04af4346) ---An explaination of Encoder-Decoder model in machine translation.


## Advices from Jiang, Minqi

* [Basic RL algorithm](https://eur01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fspinningup.openai.com%2Fen%2Flatest%2Fspinningup%2Frl_intro2.html&data=02%7C01%7C%7Ca9283f0035d84c5f253408d7b5809c2c%7C1faf88fea9984c5b93c9210a11d9a5c2%7C0%7C0%7C637177436287831455&sdata=rejITU1AhX1g9WGSruzZq%2FicFEu3nBINpy6Xy9nnIX8%3D&reserved=0)
* [Policy Gradient Algorithms](https://lilianweng.github.io/lil-log/2018/04/08/policy-gradient-algorithms.html)

## Useful Recource for Experiment

* [ROUGE evaluation](https://rxnlp.com/how-rouge-works-for-evaluation-of-summarization-tasks/#.Xk54bRP7RQI) ---sets of metric for evaluating Abstrative Summarisation result.
* [Code for attention-based summarisation](https://github.com/facebookarchive/NAMAS) ----[Neural Attention Model for Abstractive Summarization](https://arxiv.org/pdf/1509.00685.pdf), Github.
* [Text Summarization models](https://github.com/theamrzaki/text_summurization_abstractive_methods) ---With tutorials!
* [Text-Summarizer-Pytorch](https://github.com/rohithreddy024/Text-Summarizer-Pytorch) ---I tried this one but failed to write the data into binary file.
* [Ocean!](https://github.com/oceanypt/A-DEEP-REINFORCED-MODEL-FOR-ABSTRACTIVE-SUMMARIZATION) ---NMT means Neural Machine Translation...
* [einops](https://github.com/arogozhnikov/einops) ---useful package for tensor operation.

## Useful Resource for Writing Paper

* [Styling plots for publication with matplotlib](https://jonchar.net/notebooks/matplotlib-styling/) - how to use matplotlib much cooler



