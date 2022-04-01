# Part 1 
## Objective: 
Build an NLP classification model to predict which brand a new product should be assigned.

## Procedure:

1. Preprocessing: lemmatization; regex cleaning (remove punctuaion, stopwords)
2. Feature engineering: 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a. Combine all the files: product, brand and two tags and form a full table: product_tag_brand; drop unnecessary columns
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b. Create new features by extracting strings from 'brand value' and description'

3. Vectorization: we have tried different methods: 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a. count vectorization 
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b. tf-idf
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; c. word embedding 

4. Train/test split and modeling 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
<br> The idea in this part is that we would like to try various models with different inputs and to see which one returns the highest accuarcy. We chose to take top 50 brands and group everything else as other. And the Baseline performance accuracy for this model should be the largest value ~14.7%.

## A. Count Vectorization: 
For the following models, we used count vectorization for feature extraction.
1. The mean accuracy with 10-fold cross-validation for logistic regression with only 'description' as predictor variable is 0.865. 
2. The accuracy for random forest with only 'description' as input is 0.877. 
3. The accuracy for neural network with only 'description' as input is 0.883. 
4. The accuracy for logistic regression with 'description','details', 'name', 'category' and 'attribute_pair' as inputs is 0.948
5. The accuracy for logistic regression withuse 'description','details', 'name', 'category', 'attribute_pair' and created features as inputs is 0.952. 

The highest accuracy we find when we employ count vectorization is 0.952. 

## B. TF-IDF: 

- We have tried both bigram and unigram, and they do not predict well. We use 'description','details', 'name', 'category', 'attribute_pair' and created features as predictors. The accuracy given by logistic regression with OneVsRestClassifier (multiclass strategy) is 0.922. 

## C. Word Embedding:
1. The accuracy for RNN with only 'description' as input is 0.770. 
2. The accuracy for LSTM with only 'description' as input is 0.844.
3. The accuracy for deep learning Neural Network with 'description','details', 'name', 'category' and 'attribute_pair' as inputs is 0.870. 
4. The accuracy for RNN with 'description','details', 'name', 'category' and 'attribute_pair' as inputs is 0.803. 
5. The accuracy for LSTM with 'description','details', 'name', 'category' and 'attribute_pair' as inputs is 0.928

## Compiled Model after word embeding

- For the next model, we used 'description','details', 'name', 'category', 'attribute_pair' and created features. 
- We first combined the data, then preprocess the text input and categorical input separately. We put both inputs into the deep learning LSTM model. This complied model reached a test accuracy of 0.843.

## Winner Model 
- Based on the multiple attempts presented previously, we found that the DNN model performed the best after word-embedding. 
- We used 'description', 'name', 'details', 'attribute_pair', 'brand_category' as our predictor variables. 
- This model returns an accuracy of ~0.964. 
