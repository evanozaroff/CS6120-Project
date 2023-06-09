# Evaluation of Large Language Model Sentence Embeddings with SentEval, (CS6120 Spring 2023) Amritanj Ayush, Evan Ozaroff, Parisa Torshizi

## Overview
The generation of sentence embeddings is essential for a range NLP tasks including semantic textual similarity, semantic search, and paraphrase mining, and is reliant on the model’s ability to extract the unique semantic information of a given sentence. The quality of sentence embeddings can be determined by extrinsic evaluation, which considers the effectiveness of the embeddings on downstream tasks, or intrinsic evaluation, which utilizes pre-determined ground truth labels. Our research compares the performance of numerous large language models such as BERT and GPT-2 on intrinsic probing tasks implemented by the SentEval library. Our analysis found that the BERT family of models outperformed other pre-trained language models such as MPNet and GPT-2 on the SentEval intrinsic probing tasks for sentence embeddings, with the base BERT model performing best.

## Data
The datasets used in this project are derived from the SentEval probing library (https://github.com/facebookresearch/SentEval). The probing tasks attempt to evaluate how much information can be extracted from given embeddings by fitting the predictor models to the embeddings and evaluating the accuracy of these predictors on labeled data. Due to computational constraints, we were forced to work with a subset of about 1/10th of the data for each task. 

## Models
We compare the quality of  sentence embeddings produced by a family of BERT transformers, GPT-2, and MPNet.

## Results
Prior to evaluating our models performance on the SentEval probing tasks, we perform a qualitative analysis of our sentence embeddings using the SentEval datasets. We investigate the models’ ability to encode linguistic information in sentence embeddings by observing the t-SNE projections of two models, BERT and MPNet. 
![Picture2](https://github.com/evanozaroff/CS6120-Project/assets/31548066/e75caa86-c1a8-4bca-b424-40156fc9d07f)
The above figure displays the comparison of t-SNE projections for BERT and MPNet on two SentEval datasets, *Sentence Length* and *Tense*. Already we can make inferences on these models' varying ability to capture linguistic information in their embeddings. Both models seem to cluster past and present classes well in the Tense projection space, however, separation appears cleaner in the projection of the BERT embeddings. This may suggest that BERT sentence embeddings more effectively capture information regarding tense when compared to MPNet embeddings. Projections of the embeddings for Sentence Length do not exhibit the same clustering behavior. This may indicate that neither BERT nor MPNet sentence embeddings capture sentence length effectively. 


