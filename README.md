# CryptoGDelt2022

Event studies in general rely on having a high-quality curated database of events, which is especially important in volatile markets like cryptocurrencies. GDELT's quarter billion georeferenced records covering the entire world over 30 years and over 100 languages presents itself as the perfect starting point and source for event news as it lacks of any selection criteria, therefore no selection bias. 

This is the repository of __CryptoGDelt2022.csv__, a GDELT news event dataset extraction containing more than 243 thousands cryptocurrency related news events from 31st of March 2021 to the 30th of April 2022 enriched with relevance, sentiment and strength scores.

File CryptoGDelt2022_EDA_analysis_for_reproducibility_purposes.ipynb holds a simple EDA of the __CryptoGDelt2022.csv__.

In each folder Relevance, Sentiment and Strength a Python Jupyter notebook called ToReproduceStrength.ipynb is available for reproducibility_purposes.

* Relevance folder holds the relevance score model building (target: 1 news from https://finance.yahoo.com/topic/crypto and 0 news from https://news.yahoo.com, method: pipeline of TfidfVectorizer and MultinomialNB), 
* Sentiment folder holds the sentiment score model building (target: manual labelled by IE Business School students / method: retraining FinBERT) and 
* Strength folder holds the strength score model building (target: Fama French Three factor / method: pipeline of TfidfVectorizer and MultinomialNB).