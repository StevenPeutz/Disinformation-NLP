# Disinformation-NLP project
A study comparing the robustness to MT induced noise of NLP based Disinformation Classification architectures (focussing on vectorization methods and  classification algorithms).  
An online, reader-friendly, version of this project can be found on [stevenpeutz.com/disinformation](https://stevenpeutz.com/disinformation/)
<br>
## About this project
This study uses a 6 x 7 x 4 design in terms of embeddings, models and test sets. Resulting in 42 NLP architectures, each tested on 4 noise<sup>1</sup> levels.   It is focussed around the ['MAIN'](https://github.com/StevenPeutz/Disinformation-NLP/blob/master/MAIN.ipynb) notebook. <br>
The primary 0 hypothesis was tested and rejected using simple t-tests as detailed in the accompanying paper, but further statistical analysis related to the secondary hypotheses (Friedman tests with Nemenyi post-hoc tests) can be found [here](https://github.com/StevenPeutz/Disinformation-NLP/blob/master/Friedman%26Nemenyi_posthoc.ipynb).<br>
(Larger 'embedding dedicated' notebooks can be found in the 'Emb_DedicatedModels' folder. These notebooks use longer (less reduction) texts and the full unsampled datasets to obtain the most accuracte results if needed).<br>
<br>
<br>
**Embeddings:**
- CountVectorizer (BoW)
- HashingVector (HV)
- TF-IDF
- GloVe<sup>3</sup>
- Word2Vec<sup>4</sup>
- FastText<sup>5</sup>
<br>
Pretrained Embeddings (<sup>3, 4, 5</sup>):


|                Embedding               | Dims | Size (gzipped) |  Storage   |                                                 Download link                                                 |
| :------------------------------------|:----:|:--------------:|:----------:|:---------------------------------------------------------------------------------------------------------: |
|           <sup>3  </sup>GloVe  (50d version)          | 50   |   66 MB        |   Kaggle   |         https://www.kaggle.com/datasets/stevenpeutz/tinypretrainedembeddings         |
|      <sup>4  </sup>FastText - PCA Reduced (300)     | 50   |   240 MB       |   Kaggle   |         https://www.kaggle.com/datasets/stevenpeutz/tinypretrainedembeddings         |
|     <sup>5  </sup>Word2Vec - PCA Reduced (300)       | 50   |   958 MB       |   Kaggle   |         https://www.kaggle.com/datasets/stevenpeutz/tinypretrainedembeddings         |


<br>
<br>

**General Purpose Classification Models**
- Logistic Regression (LR)
- Naive Bayes (NB)
- Random Forest (RF)
- Support Vector Machine (SVM)
- K-Nearest Neighbour (KNN)
- GradientBoosting (GB)
- Extreme Gradient Boosting (XGB)   
  
<br>
<br>

**Datasets:**   

| Name                          | Rows   | Size (gzipped) | Storage | Download link (use raw version if directly in notebook)                                                   |
| -----------------------------|-------|----------------|---------| -------------------------------------------------------------------------------------------------------------|
| Chendra - fake_train                    | 20.387| 38.4MB         | Github  | https://github.com/StevenPeutz/Disinformation-NLP/blob/master/DATA/21k_Chendra/fake_train.csv.gz |
| Jillani - fake_or_real_news             | 6.060 | 11.9MB         | Github  | https://github.com/StevenPeutz/Disinformation-NLP/blob/master/DATA/6k_Jillani/fake_or_real_news.csv.gz |
| EUvsDisinfo - data                          | 6.241 | 4.7MB          | Github  | https://github.com/StevenPeutz/Disinformation-NLP/blob/master/DATA/EUvsDisinfo.eu/data.csv.gz |
| Crone - monkeypox                     | 4.000 | 7.8MB          | Github  | https://github.com/StevenPeutz/Disinformation-NLP/blob/master/DATA/MonkeyPoxMisinfo/monkeypox.csv.gz |
| UVIC-ISOT - Fake                          | 20.000| 23.7MB         | Github  | https://github.com/StevenPeutz/Disinformation-NLP/blob/master/DATA/UVIC-ISOT/Fake.csv.gz |
| UVIC-ISOT - True                          | 20.000| 18.7MB         | Github  | https://github.com/StevenPeutz/Disinformation-NLP/blob/master/DATA/UVIC-ISOT/True.csv.gz |
| CompiledDisinfo_74k<sup>2  </sup>          | 73.900| 75.1MB         | Github  | https://github.com/StevenPeutz/Disinformation-NLP/blob/master/DATA/CompiledDisinfo_74k/CompiledDisinfo_74k.csv.gz | 

<br>


<br>

<sup>1  </sup> *Noise levels as introduced by machine backtranslations. 'N0' being the original testset (the version similar to training), 'N1' (1 level of backtranslation (EN -> RU -> EN), continuing to 'N3'.
For rough assessment of noise in a purely lexical sense, the Jaro-Winkler Distances (normalized) have been calculated before and are imported in this notebook*   
<br>

<sup>2  </sup> *'CompiledDisinfo_74K' is not a separately sourced dataset, but is the compiled version of the above 6 datasets. This can be directly downloaded form the given link).* 

<br>
<br>


<br>
**AUC ROC's can be seen to decrease as MT noise (operationalized as back-translation levels, as well as by Jaro Winkler Distance (Lexical)) increases.**  
<br> 



| Model/Alg              | Embedding/vectorizer  | N0 (JWD=0.000)      | N1 (JWD=0.137)      | N2 (JWD=0.141)     | N3 (JWD=0.142)      |
|------------------------|-----------------------|---------|---------|---------|---------|
| Logistic Regression    | BoW                   | .9077   | .8506   | .8487   | .8479   |
|                        | HV                    | .8891   | .8505   | .8481   | .8482   |
|                        | TFIDF                 | .9131   | .8705   | .8690   | .8679   |
|                        | GloVe                 | .7374   | .6985   | .7006   | .7005   |
|                        | Word2Vec (PCA_red)    | .7475   | .6997   | .6977   | .6962   |
|                        | FastText (PCA_red)    | .7649   | .7260   | .7269   | .7288   |
| Naive Bayes            | BoW                   | .8313   | .7936   | .7912   | .7905   |
|                        | HV                    | .8249   | .7800   | .7784   | .7787   |
|                        | TFIDF                 | .8484   | .8052   | .8041   | .8033   |
|                        | GloVe*                | .6221   | .6043   | .6026   | .6022   |
|                        | Word2Vec (PCA_red)*   | .6107   | .5827   | .5817   | .5813   |
|                        | FastText (PCA_red)*   | .5629   | .5434   | .5423   | .5429   |
| Random Forest          | BoW                   | .8102   | .7570   | .7572   | .7563   |
|                        | HV*                   | .7892   | .7492   | .7488   | .7457   |
|                        | TFIDF                 | .8086   | .7762   | .7746   | .7747   |
|                        | GloVe*                | .7226   | .6762   | .6696   | .6696   |
|                        | Word2Vec (PCA_red)    | .7247   | .6710   | .6659   | .6631   |
|                        | FastText (PCA_red)    | .7262   | .6659   | .6626   | .6582   |
| SVM                    | BoW                   | .9180   | .8604   | .8576   | .8574   |
|                        | HV                    | .9202   | .8610   | .8591   | .8571   |
|                        | TFIDF                 | .8767   | .8447   | .8437   | .8437   |
|                        | GloVe                 | .6839   | .6639   | .6627   | .6648   |
|                        | Word2Vec (PCA_red)    | .7791   | .7164   | .7163   | .7191   |
|                        | FastText (PCA_red)    | .7907   | .7429   | .7430   | .7452   |
| KNN                    | BoW                   | .7226   | .6921   | .6866   | .6869   |
|                        | HV                    | .7612   | .7357   | .7369   | .7374   |
|                        | TFIDF                 | .7962   | .7693   | .7683   | .7684   |
|                        | GloVe                 | .5971   | .5725   | .5723   | .5723   |
|                        | Word2Vec (PCA_red)    | .4992   | .4939   | .4931   | .4920   |
|                        | FastText (PCA_red)    | .5922   | .5689   | .5697   | .5681   |
| GradientBoosting       | BoW                   | .8947   | .8287   | .8258   | .8247   |
|                        | HV                    | .8956   | .8349   | .8340   | .8329   |       
|                        | TFIDF                 | .8948   | .8349   | .8321   | .8321   |       
|                        | GloVe                 | .7865   | .7313   | .7315   | .7300   |       
|                        | Word2Vec (PCA_red)    | .7862   | .7261   | .7238   | .7250   |
|                        | FastText (PCA_red)    | .7878   | .7338   | .7321   | .7307   |       |
| XGB                    | BoW                   | .8973   | .8357   | .8340   | .8337   |
|                        | HV                    | .8982   | .8424   | .8405   | .8386   |       
|                        | TFIDF                 | .8980   | .8383   | .8361  | .8350    |       
|                        | GloVe                 | .8010   | .7540   | .7490  | .7481    |       
|                        | Word2Vec (PCA_red)    | .8072   | .7475   | .7418   | .7413   |
|                        | FastText (PCA_red)    | .8057   | .7526   | .7476   | .7459   |       |


<br>
<br>

*(trained model instances (parameters and weights) can be found as pickled files (.pkl) in the 'PickledModels' folder)* 
