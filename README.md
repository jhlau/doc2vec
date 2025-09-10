The repository contains some python scripts for training and inferring test document vectors using paragraph vectors or doc2vec.

Requirements
============
* Python2: Pre-trained models and scripts all support Python2 only.
* Gensim: Best to use my [forked version](https://github.com/jhlau/gensim) of gensim; the latest gensim has changed its Doc2Vec methods a little and so would not load the pre-trained models.

Pre-Trained Doc2Vec Models
==========================
* All data can be downloaded [here](https://mediaflux.researchsoftware.unimelb.edu.au/mflux/data/mover/index.html?token=kg48rxcqq76v15kvwwsfj2iqkvmijugyydjrqr2jq8gseyh4ojrt1nw0rg3dq2k70l23lv5klxose7z8nrm7eccvx47plvyr84ldj8mi9yfmwoh5nzfdwm8luxw3uupewpzhibyyfz4f2zy6ypsdqxcc9pjm3cf8hndwc7uie27r5cyprp0fxzwwnxd3fsuzk49f6gfbhqbyxwdv31y6k2al97hgww9034vi1oq5) (note: you'll be prompted to download a program called "Mediaflux Data Mover" - after installing it, click the link again and open Mediaflux Daata Mover and you'll be able to download the data via the program).
* English Wikipedia DBOW (1.4GB): 2016-doc2vec/enwiki_dbow.tgz
* Associated Press News DBOW (0.6GB): 2016-doc2vec/apnews_dbow.tgz

Pre-Trained Word2Vec Models
===========================
For reproducibility we also released the pre-trained word2vec skip-gram models on Wikipedia and AP News:
* All data can be downloaded [here](https://mediaflux.researchsoftware.unimelb.edu.au/mflux/data/mover/index.html?token=kg48rxcqq76v15kvwwsfj2iqkvmijugyydjrqr2jq8gseyh4ojrt1nw0rg3dq2k70l23lv5klxose7z8nrm7eccvx47plvyr84ldj8mi9yfmwoh5nzfdwm8luxw3uupewpzhibyyfz4f2zy6ypsdqxcc9pjm3cf8hndwc7uie27r5cyprp0fxzwwnxd3fsuzk49f6gfbhqbyxwdv31y6k2al97hgww9034vi1oq5) (note: you'll be prompted to download a program called "Mediaflux Data Mover" - after installing it, click the link again and open Mediaflux Daata Mover and you'll be able to download the data via the program).
* English Wikipedia Skip-Gram (1.4GB): 2016-doc2vec/enwiki_sg.tgz
* Associated Press News Skip-gram (0.6GB): 2016-doc2vec/apnews_sg.tgz

Directory Structure and Files
=============================
* train_model.py: example python script to train some toy data
* infer_test.py: example python script to infer test document vectors using trained model
* toy_data: directory containing some toy train/test documents and pre-trained word embeddings

Model Hyper-Parameter Explanation
=================================
* __sample__: this is the sub-sampling threshold to downsample frequent words; 10e-5 is usually good for DBOW, and 10e-6 for DMPV
* __hs__: 1 turns on hierarchical sampling; this is rarely turned on as negative sampling is in general better
* __dm__: 0 = DBOW; 1 = DMPV
* __negative__: number of negative samples; 5 is a good value
* __dbow_words__: 1 turns on updating of word embeddings. In DBOW, word embeddings are technically not learnt (only document embeddings are learnt). To learn word vectors, DBOW runs a step of skip-gram before the DBOW step to update the word embeddings. With dbow_words turned off, this means DBOW will randomly initialise word embeddings and keep them randomly initialised. This is rather bad in practice (as the model does not see relationships between words in the embedding space), so it should be turned on
* __dm_concat__: 1 = concatenate input word vectors for DMPV; 0 = sum/average input word vectors. This setting is only used for DMPV since DBOW has only one input word
* __dm_mean__: 1 = average input word vectors; 0 = sum input word vectors. Again, this setting is only used for DMPV. The original paragraph vector paper concatenates input word vectors for DMPV, and that's the setting we used in our paper
* __iter__: number of iterations/epochs to train the model

Publications
------------
* Jey Han Lau and Timothy Baldwin (2016). [An Empirical Evaluation of doc2vec with Practical Insights into Document Embedding Generation](https://arxiv.org/abs/1607.05368). In Proceedings of the 1st Workshop on Representation Learning for NLP, 2016.
