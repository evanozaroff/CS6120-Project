# Evaluation of Large Language Model Sentence Embeddings with SentEval 
(CS6120 Spring 2023) Amritanj Ayush, Evan Ozaroff, Parisa Torshizi

## Overview
The generation of sentence embeddings is essential for a range NLP tasks including semantic textual similarity, semantic search, and paraphrase mining, and is reliant on the model’s ability to extract the unique semantic information of a given sentence. The quality of sentence embeddings can be determined by extrinsic evaluation, which considers the effectiveness of the embeddings on downstream tasks, or intrinsic evaluation, which utilizes pre-determined ground truth labels. Our research compares the performance of numerous large language models such as BERT and GPT-2 on intrinsic probing tasks implemented by the SentEval library. Our analysis found that the BERT family of models outperformed other pre-trained language models such as MPNet and GPT-2 on the SentEval intrinsic probing tasks for sentence embeddings, with the base BERT model performing best.

## Data
The datasets used in this project are derived from the SentEval probing library (https://github.com/facebookresearch/SentEval). The probing tasks attempt to evaluate how much information can be extracted from given embeddings by fitting the predictor models to the embeddings and evaluating the accuracy of these predictors on labeled data. Due to computational constraints, we were forced to work with a subset of about 1/10th of the data for each task. 

## Models
We compare the quality of  sentence embeddings produced by a family of BERT transformers, GPT-2, and MPNet.

## Results
Prior to evaluating our models performance on the SentEval probing tasks, we perform a qualitative analysis of our sentence embeddings using the SentEval datasets. We investigate the models’ ability to encode linguistic information in sentence embeddings by observing the t-SNE projections of two models, BERT and MPNet. 
![Picture2_smaller](https://github.com/evanozaroff/CS6120-Project/assets/31548066/e7ff30a8-edd1-4135-8204-752a0b7fe2d2)
<!-- 
![Picture2](https://github.com/evanozaroff/CS6120-Project/assets/31548066/e75caa86-c1a8-4bca-b424-40156fc9d07f) -->
The above figure displays the comparison of t-SNE projections for BERT and MPNet on two SentEval datasets, *Sentence Length* and *Tense*. Already we can make inferences on these models' varying ability to capture linguistic information in their embeddings. Both models seem to cluster past and present classes well in the Tense projection space, however, separation appears cleaner in the projection of the BERT embeddings. This may suggest that BERT sentence embeddings more effectively capture information regarding tense when compared to MPNet embeddings. Projections of the embeddings for Sentence Length do not exhibit the same clustering behavior. This may indicate that neither BERT nor MPNet sentence embeddings capture sentence length effectively. 


![Average model performance](https://github.com/evanozaroff/CS6120-Project/assets/31548066/3056cb63-7237-4994-b143-0a0eb5e2dbab)
We observe that the BERT family of models all have comparable average performance, an accuracy around 60% on average for the probing tasks, shown above. These models share similar architecture, training corpus’, and pre-training tasks, specifically masked language modeling. These similarities in training may lead to the similarity in embedding performance that we observe here. The original BERT model performs the best of all models.

MPNet performed worst on the probing tasks overall, with an average accuracy of 49%. This finding was surprising, as prior work on evaluation of sentence embeddings notes MPNet as one of the best language models available [1]. There are two possible explanations for the discrepancy we observe between our findings and previous work. The referenced work compares models on a set of downstream tasks, which is a fundamentally different approach to embeddings evaluation than the probing tasks we employ (extrinsic vs. intrinsic). Additionally, our results may differ from previous findings due to our use of a smaller training set. 

![Average task performance](https://github.com/evanozaroff/CS6120-Project/assets/31548066/762e1a3f-68f0-420b-aa2c-a4678dd81577)
Performance of all models on tasks such as Tense and Subject Number was impressive, above 80% accuracy on average. These specific tasks evaluate the embeddings ability to capture grammatical information from the input sentences. This may suggest that these types of large language models more readily encode this type of grammatical information when compared to other types of information, like word content or sentence length.

Performance on the Word Content task was particularly low, at around 15% accuracy on average. This however, was to be expected: due to computational constraints we were forced to make use of only a subset of the labeled data for each probing task, selecting around 10,000 training examples. The Word Content probing task is structured as a classification task over a vocabulary of 1,000 words, and thus would require a larger training set in order to produce accurate predictors using the embeddings from each model.


## References
[1] SBERT.net. (n.d.). Pretrained models¶. Pretrained Models - Sentence-Transformers documentation. Retrieved April 16, 2023, from https://www.sbert.net/docs/pretrained_models.html 
