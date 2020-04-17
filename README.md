# Capstone: News Popularity in Multiple Social Media Platforms

## Problem Statement

Analyzing news headline using **Natual Language Processing (NLP)** from various notable publishers and understanding of the underlying sentiment of headlines and predicting it's popularity from social media.

## Executive Summary

The United States itself has numerous news publishers such as **"New York Times"**, **"Washington Post"** and **"ABC News"**. And it is no surprised many of these news publishers will be posting similar articles on their webpage and social media platform. However, each article are written by writers of different views therefore, the article will carry different sentiment. And with different views and sentiments it would also signifies the difference in popularity of the article.

Thus, the purpose of my model is to gather the **number of shares** on respective publishers social media platform and categorise them accordingly to their popularity. And the model would **predict the popularity** of the headline based on features such as **sentiment** and **vector positioning of words**.

The model would be useful to gain an understanding of readers preference based on article sentiment and keywords and provide insight for writers and editors on the ideal format of their articles.

## Contents

- [Data Extraction](#Data-Extraction)
- [Data Cleaning and Exploratory Data Analysis (EDA)](#Data-Cleaning-and-Exploratory-Data-Analysis-(EDA))
- [Modelling](#Modelling)
- [Model Evaluation](#Model-Evaluation)
- [Conclusion & Recommendation](#Conclusion-&-Recommendation)

## Data Extraction

**Data extraction** is done using the UCI Machine Learning Repository and beforehand some headlines are extracted using New York Times API as a reference for this project. The **data set information** are shown in the table below and process such **data cleaning**, **EDA**, **Preprocessing** and **Modelling**. 

### Data Set Information

This data contains news headlines and titles and their respective social feedback on multiple platforms such as Facebook, Google+ and LinkedIn.
These data are collected between the year 2015 and 2016 which accounts for about 100,000 news on the four main topics of **Economy**, **Microsoft**, **Obama**, **Palestine**.

### VARIABLES OF NEWS DATA  

|Variable      |Description      |
|---------    |------    |
|**IDLink (numeric)**| **Unique identifier of news items**| 
|**Title (string)**| **Title of the news item according to the official media sources**| 
|**Headline (string)**|**Headline of the news item according to the official media sources**|
|**Source (string)**|**Original news outlet that published the news item**|  
|**Topic (string)**|**Query topic used to obtain the items in the official media sources**|  
|**PublishDate (timestamp)**|**Date and time of the news items' publication**|  
|**SentimentTitle (numeric)**|**Sentiment score of the text in the news items' title**|  
|**SentimentHeadline (numeric)**|**Sentiment score of the text in the news items' headline**|  
|**Facebook (numeric)**|**Final value of the news items' popularity according to the social media source Facebook**|  
|**GooglePlus (numeric)**|**Final value of the news items' popularity according to the social media source Google+**|  
|**LinkedIn (numeric)**|**Final value of the news items' popularity according to the social media source LinkedIn**|

## Data Cleaning and Exploratory Data Analysis (EDA)

As the data was extracted directly from UCI Machine Learning Repository and New York Times API it is generally clean however, it has to be preprocess before any form of EDA can be done on it. Since the focus of the Capstone would be on Natural Learning Processing (NLP) most of the preprocessing are done on headlines and titles, removing stop words and non-alphabetic words before using it for modelling and EDA.

### Summary of EDA 

A glimpse of some of the EDA that were done based on the word count of headline in the text body. **Unigram**, **Bigrams** and **Trigrams** were evaluated to get a better understanding of the headline and title features. 

![](pictures/Screenshot%202020-04-13%20at%208.40.13%20PM.png)
Fig 1.1

**Fig 1.1** clearly shows the Top 20 words word count of a bigram and it is accurate in showing the most popular pair of words from with the text body of the headline. 

![](pictures/Screenshot%202020-04-16%20at%206.41.44%20PM.png)
Fig 1.2

**Fig 1.2** is a venn diagram showing the common words used between the headlines and titles as well as their individual difference. 

### Tableau Visualization

Using the graphical capability of **Tableau** the remaining EDA were done using the Tableau platform as shown in the figures below:

![](pictures/Topic%20popularity%20across%20each%20social%20media%20platform.png)
Fig 1.3

From Fig 1.3, Facebook has the highest No. of shares among all the other social media platform therefore, for modelling Facebook would be the feature used for creating dummy variables as it is one of the most popular social media platform used for sharing of news article.

![](pictures/Screenshot%202020-04-16%20at%203.59.43%20PM.png)
Fig 1.4

As there were hundreds of source/publisher within the data set it was decided to focus on the **Top 10 source/publisher** in terms of the number of contributed source. It is no surprised that the Top 10 listed source/publisher are big name news publisher such as Bloomberg, New York Times and CNN. 


![](pictures/Screenshot%202020-04-16%20at%204.14.11%20PM.png)
Fig 1.5

Fig 1.5 shows the Avg.share among the Top 10 source/publisher groupby the four main topics within the data set. Beside the difference in the Avg.share among the three social media platform we can notice the followers characteristics among these platform. 
- **User of Facebook** tend to be more interested in the topic related to Obama as compared to other main topics
- **User of GooglePlus** are more incline towards topic related to Microsoft 
- **User of LinkedIn** falls within two main topic of Microsoft and Economy which is logical since LinkedIn is known for   being a professional business oriented social media platform.

![](pictures/Screenshot%202020-04-16%20at%205.15.41%20PM.png)
Fig 1.6

Beside analysing on news popularity on their respective social media platform, analysing on the sentiment of Title across the Top 10 source/publisher were done as well. From Fig 1.6, ABC News has the most positive avg. sentiment while The Guardian has the most negative avg.sentiment. In the notebook more EDA would be done to see if sentiment affects the popularity of the news. 

### Dimentionality Reduction: t-SNE

In order to visualise those word vectors and to spot for any patterns **Dimentionality Reduction with t-SNE** is used here. The t-SNE aids in transforming higher dimensional vector into a lower dimensional vector for ease of visualisation. In this case, the word vectors are transformed into 2D vector.

![](pictures/Screenshot%202020-04-16%20at%207.50.02%20PM.png)
Fig 1.7

Fig 1.7 shows the clustering among the four main topics when the whole text of title were input into t-SNE. However, bearing in mind that t-SNE is not deterministic in density of clusters and distances between each clusters are not always meaningful. It is plainly a exploratory tool rather than a decisive indicator of similarity. 

 ## Modelling 
 
 As this is a classification problem, models that perform relatively efficiently were used. 
 
 ![](pictures/Screenshot%202020-04-16%20at%206.45.42%20PM.png)
 Fig 2.1
 
Among those five machine learning models that were used, Support Vector Machine (SVM) and XGBoost stands out the most in terms of their accuracy of F1-score. There were overall two types of feature engineering model that were implemented to run those models. The two models used were **Word2Vec** and **TFIDF**.

The first method would be the use **Word2Vec** model, using the word vector to accuractely predict the popularity of Titles. 
And the second method would be the use of **TFIDF** model to give weightage to words based on their frequencies appearing in the text. 

## Model Evaluation

### Word2Vec Model 

**Word2Vec & XGBClassifier GridSearch** was the best performing Word2Vec model as it has one of the highest accuracy f1 score and lower type errors as compared to other deployed methods. 


### Data collected from Word2Vec model

|Model      |F1-score      |
|---------    |------    |
|**XGBClassifier Basemodel** |0.46    |
|**XGBClassifier GridSearch**        |**0.77**   |
|**RandomForest Bsemodel** |0.44  |
|**RandomForest GridSearch**    |0.51    |
|**KNN Basemodel**    |0.52    |
|**KNN GridSearch**  |0.63    |
|**SVM Basemodel**    |0.49    |
|**SVM GridSearch**    |0.51    |

**Accuracy:** XGBClassifier GridSearch provided the highest F1-score of **0.77**.  

### TFIDF Model 

**TFIDF & SVM GridSearch** was the best performing TFIDF model as it has one of the highest accuracy based on F1-score and lower type errors as compared to other deployed methods. 


### Data collected from TFIDF model

|Model      |F1-score      |
|---------    |------    |
|**MultinomialNB Basemodel** |0.57    |
|**MultinomialNB GridSearch**        |0.5   |
|**KNN Basemodel**    |0.57    |
|**KNN GridSearch**  |0.55    |
|**SVM Basemodel**    |0.77    |
|**SVM GridSearch**    |**0.83**    |

**Accuracy:** SVM GridSearch provided the highest F1-score of **0.83**.  
 
### Best Word2Vec & TFIDF model

|Model      |F1-score      |
|---------    |------    |
|**XGBClassifier GridSearch (Word2Vec)** |0.77    |
|**SVM GridSearch (TFIDF)**        |0.83   |

## Conclusion & Recommendation

In conclusion, SVM GridSearch (TFIDF) had a better accuracy result as compared to the XGBclassifier GridSearch (Word2Vec). This might be due to the fact that the features input were different for both models. As explained above, Word2Vec model transform words into word vector and using those vector dimensions we tried to predict the target label. From the t-SNE graph it can be clearly seen that individual word vector do not show any clear distinction of clustering or patterns. Thus, putting through those features into the model might not prove to be the most ideal.

As for the TFIDF method, it transforms individual words into frequencies of occurence from within the text and applies weightage to it. The accuracy did improve when TFIDF method was used, it might be due to the weightage that was applied into the model that helps to classify the important and unimportant words from within the text.

Hence, there are ways to improve on the model using Word2Vec which are also the limitation faced while running the model. The full word vector dimensions were not used in this project due to computation limitation from hardware. Thus, if given better hardware or using the AWS services more data could be use to run the Word2Vec model instead of reducing the data. 






