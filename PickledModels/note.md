## Pickled Models

The pickle library was used to save all the models (parameters and weights) and the pkl files are uploaded here.
The files can be directly read using the pickle library (reading them in is done with 'load' and saving them is done with 'dump') as can be seen in the notebooks used here.
<br>
Here is the full list of pickled instances of all model embedding combinations pickled and uploaded here. 
- Logistic Regression (LR) + CountVectorizer (BoW) / HashingVector (HV) / TF-IDF / GloVe3 / Word2Vec / FastText
- Naive Bayes (NB) + CountVectorizer (BoW) / HashingVector (HV) / TF-IDF / GloVe3 / Word2Vec / FastText
- Random Forest (RF) + CountVectorizer (BoW) / HashingVector (HV) / TF-IDF / GloVe3 / Word2Vec / FastText
- Support Vector Machine (SVM) + CountVectorizer (BoW) / HashingVector (HV) / TF-IDF / GloVe3 / Word2Vec / FastText
- GradientBoosting (GB) + CountVectorizer (BoW) / HashingVector (HV) / TF-IDF / GloVe3 / Word2Vec / FastText
- Extreme Gradient Boosting (XGB) + CountVectorizer (BoW) / HashingVector (HV) / TF-IDF / GloVe3 / Word2Vec / FastText

<br>
The K-nearest Neighbours (KNN) model is the only classification algorithm used that does not have a saved (pickled) model file uploaded here. This is because of the size
of the KNN model versus the storage space available in the free tier of github.  

(The pickled KNN instance can be found in my google drive).
