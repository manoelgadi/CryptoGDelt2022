# CryptoGDelt2022

Event studies in general rely on having a high-quality curated database of events, which is especially important in volatile markets like cryptocurrencies. GDELT's quarter billion georeferenced records covering the entire world over 30 years and over 100 languages presents itself as the perfect starting point and source for event news as it lacks of any selection criteria, therefore no selection bias. 

This is the repository of __CryptoGDelt2022.csv__, a GDELT news event dataset extraction containing more than 243 thousands cryptocurrency related news events from 31st of March 2021 to the 30th of April 2022 enriched with relevance, sentiment and strength scores.

File CryptoGDelt2022_EDA_analysis_for_reproducibility_purposes.ipynb holds a simple EDA of the __CryptoGDelt2022.csv__.

In each folder Relevance, Sentiment and Strength a Python Jupyter notebook called ToReproduceStrength.ipynb is available for reproducibility_purposes.

* Relevance folder holds the relevance score model building (target: 1 news from https://finance.yahoo.com/topic/crypto and 0 news from https://news.yahoo.com, method: pipeline of TfidfVectorizer and MultinomialNB), 
* Sentiment folder holds the sentiment score model building (target: manual labelled by IE Business School students / method: retraining FinBERT) and 
* Strength folder holds the strength score model building (target: Fama French Three factor / method: pipeline of TfidfVectorizer and MultinomialNB).



# How to reproduce the creation of CryptoGDelt2022.csv

* __1st run CryptoGDelt2022_GDELT_initial_download.ipynb:__ this code downloads the whole period of news from Gdelt, it may take more than a week to do so, recommended to skip this part for reproduction 
(development dataset: None; deployment dataset - input: None - output: OneYearNewsDataset.csv)

* __2nd run Relevance/ToReproduceRelevance.ipynb:__ this code train the supervised relevance score using all_score_training.csv dataset and deploy it to the pipe of news downloaded from Gdelt in an addictive manner
(development dataset: Relevance/all_score_training.csv; deployment dataset - input: OneYearNewsDataset.csv - output: OneYearNewsDataset_AfterRelevance.csv)

* __3rd run Sentiment/ToReproduceSentiment.ipynb:__ this code retrain Finbert sentiment score using CryptoLin_IE_v2.csv dataset and deploy it to the pipe of news downloaded from Gdelt in an addictive manner
(development dataset: Sentiment/CryptoLin_IE_v2.csv; deployment dataset - input: OneYearNewsDataset_AfterRelevance.csv - output: OneYearNewsDataset_AfterSentiment.csv)

* __4th run Sentiment/ToReproduceStrength.ipynb:__ this code train the Strength score based on Fama French using CryptoLin_IE_v2.csv dataset and deploy it to the pipe of news downloaded from Gdelt in an addictive manner
(development dataset: Strength/FF3_daily.csv and Strength/news_short.xlsx; deployment dataset - input: OneYearNewsDataset_AfterSentiment.csv - output: OneYearNewsDataset_AfterStrength.csv) OneYearNewsDataset_AfterStrength.csv is similar to CryptoGDelt2022.csv, CryptoGDelt2022.csv contains some extra date fields used for sorting the news by date and time.


* __5th Optionally run CryptoGDelt2022_EDA.ipynb:__ this code outputs an EDA of the dataset (currently CryptoGDelt2022.csv, change it to OneYearNewsDataset_AfterStrength.csv if you want to use the newly created dataset).


