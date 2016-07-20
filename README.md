The repository contains some python scripts for training and inferring test document vectors using paragraph vectors or doc2vec.

Requirements
============
* Gensim: If you need to load pre-trained word embeddings when training doc2vec, check out my [forked version](https://github.com/jhlau/gensim) of Gensim; if not feel free to use the [canonical one](https://github.com/RaRe-Technologies/gensim)

Pre-Trained Doc2Vec Models
==========================
* [English Wikipedia DBOW (1.4GB)](https://ibm.box.com/s/3f160t4xpuya9an935k84ig465gvymm2)
* [Associated Press News DBOW (0.6GB)](https://ibm.box.com/s/9ebs3c759qqo1d8i7ed323i6shv2js7e)

Directory Structure and Files
=============================
* train_model.py: example python script to train some toy data
* infer_test.py: example python script to infer test document vectors using trained model
* toy_data: directory containing some toy train/test documents and pre-trained word embeddings

Publications
------------
* Jey Han Lau and Timothy Baldwin (2016). [An Empirical Evaluation of doc2vec with Practical Insights into Document Embedding Generation](https://arxiv.org/abs/1607.05368). In Proceedings of the 1st Workshop on Representation Learning for NLP, 2016.
