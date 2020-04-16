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
- [Preprocessing](#Preprocessing)
- [Modelling](#Modelling)
- [Model Evaluation](#Model-Evaluation)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [Sources](#Sources)

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

# ![EDA 1]
(https://camo.githubusercontent.com/6ce15b81c1f06d716d753a61f5db22375fa684da/68747470733a2f2f67612d646173682e73332e616d617a6f6e6177732e636f6d2f70726f64756374696f6e2f6173736574732f6c6f676f2d39663838616536633963333837313639306533333238306663663535376633332e706e67)
