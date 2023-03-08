# Masterthesis-Disinformation-NLP
A study comparing the robustness to MT induced noise of NLP based Disinformation Classification architectures (focussing on vectorization methods and  classification algorithm combinations).  
<br>
## About this project
This study uses a 6 x 7 x 4 design in terms of embeddings, models and test sets. Resulting in 42 NLP architectures, each tested on 4 noise<sup>1</sup> levels.   
It is focussed around [this notebook](https://github.com/StevenPeutz/Masterthesis-Disinformation-NLP/tree/master/CODE) -TODO: replace with link- that runs the 6 x 7 x 4 design in one single environment for easy use and direct comparison. (Unreduced 'embedding dedicated' notebooks can be found in the 'CODE/Unreduced' folder. These notebooks use the full (no PCA reduction) embeddings and full unsampled datasets to obtain the most accuracte results).
<br>
<br>
**Embeddings:**
- CountVectorizer (BoW)
- HashingVector (HV)
- TF-IDF
- GloVe<sup>3</sup>
- Word2Vec<sup>4</sup> (w2v)
- FastText<sup>5</sup> (ft)
<br>
Pretrained Embeddings (<sup>3, 4, 5</sup>):


|                Embedding               | Dims | Size (gzipped) |  Storage   |                                                 Download link                                                 |
| :------------------------------------|:----:|:--------------:|:----------:|:---------------------------------------------------------------------------------------------------------: |
|           <sup>3  </sup>GloVe  (50dim version)          | 50   |   66 MB        |   Kaggle   |         https://www.kaggle.com/datasets/stevenpeutz/tinypretrainedembeddings         |
|      <sup>4  </sup>FastText - Reduced (PCA from 300)     | 50   |   240 MB       |   Kaggle   |         https://www.kaggle.com/datasets/stevenpeutz/tinypretrainedembeddings         |
|     <sup>5  </sup>Word2Vec - Reduced (PCA from 300)       | 50   |   958 MB       |   Kaggle   |         https://www.kaggle.com/datasets/stevenpeutz/tinypretrainedembeddings         |


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
Datasets:  

| Name                          | Rows   | Size (gzipped) | Storage | Download link (use raw version if directly in notebook)                                                   |
| -----------------------------|-------|----------------|---------| -------------------------------------------------------------------------------------------------------------|
| fake_train                    | 20.387| 38.4MB         | Github  | https://github.com/StevenPeutz/Masterthesis-Disinformation-NLP/blob/master/DATA/21k_Chendra/fake_train.csv.gz |
| fake_or_real_news             | 6.060 | 11.9MB         | Github  | https://github.com/StevenPeutz/Masterthesis-Disinformation-NLP/blob/master/DATA/6k_Jillani/fake_or_real_news.csv.gz |
| data                          | 6.241 | 4.7MB          | Github  | https://github.com/StevenPeutz/Masterthesis-Disinformation-NLP/blob/master/DATA/EUvsDisinfo.eu/data.csv.gz |
| monkeypox                     | 4.000 | 7.8MB          | Github  | https://github.com/StevenPeutz/Masterthesis-Disinformation-NLP/blob/master/DATA/MonkeyPoxMisinfo/monkeypox.csv.gz |
| Fake                          | 20.000| 23.7MB         | Github  | https://github.com/StevenPeutz/Masterthesis-Disinformation-NLP/blob/master/DATA/UVIC-ISOT/Fake.csv.gz |
| True                          | 20.000| 18.7MB         | Github  | https://github.com/StevenPeutz/Masterthesis-Disinformation-NLP/blob/master/DATA/UVIC-ISOT/True.csv.gz |
| CompiledDisinfo_74k<sup>2  </sup>          | 73.900| 75.1MB         | Github  | https://github.com/StevenPeutz/Masterthesis-Disinformation-NLP/blob/master/DATA/CompiledDisinfo_74k/CompiledDisinfo_74k.csv.gz | 

<br>
<sup>2  </sup> *'CompiledDisinfo_74K' is not a separately sourced dataset, but is the compiled version of the above 6 datasets. This can be directly downloaded form the given link).*

<br>

<br>
<sup>1  </sup> *Noise levels as introduced by machine backtranslations. 'N0' being the original testset (the version similar to training), 'N1' (1 level of backtranslation (EN -> RU -> EN), continuing to 'N3'.
For rough assessment of noise in a purely lexical sense, the Jaro-Winkler Distances (normalized) have been calculated and imported before and are imported in this notebook*  
<br>
<br>

