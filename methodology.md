---
layout: page
title: Methodology
subtitle: Findings!!!!
---

# Methodologies
<br/>

#### Techniques Applied

**PCA/Clustering of Symptoms ( Where each condition was represented as a symptom vector ) to figure which symptoms co-occur.**<br/>
50 PCA dimensions and 10 clusters.
<br/><br/>
**Decision Tree based ( XgBoost) prediction of a condition based on a symptom.**<br/>
One vs Rest XGBoost Model with max_depth = 4, booster = gbtree, eta = 0.3, max_bin = 256. 
<br/><br/>
**Recommendation System to recommend effective treatments ( SVD++ ).**<br/>
Effectiveness score computation was one of the key metrics to  measure the effectiveness of a treatment.
* We used 20 latent factors and trained the model for 20 epochs,
* Effectiveness score computation was one of the key metrics to  measure the effectiveness of a treatment
<br/><br/>
 
**Association Rule mining - Treating ( Symptoms + Treatment ) as baskets(items ) and each row/truncations as a user.**<br/>
For a Support of 0.001,C=0.4 and lift = 2 we got an highly indirect and interesting result . When we built the rules, we found the side effects(listed as symptoms) of conditions in the majority part of the result. For eg (nausea,headache) -> 
(fludrocortisone) indicating nausea and headaches are side effects of fludrocortisone.
__Additional data preprocessing and model specfic details can be found in the result section__
<br/><br/>

# Data PreProcessing

## Cleaning Trackables
Since the trackable names are not standardized and probably entered and registered by different persons, there are many synonyms, equivalents, duplicates or simple writing mistakes in them. For any further analysis of the trackables such as association mining, it’s very important that the trackables that are actually the same thing do not be considered different. Below are some examples of such synonyms in different trackables occurred in the database:

##### Symptoms:
‘fatigue’ = ‘tiredness’, ‘drowsiness’ = ‘sleepiness’, ‘aggression’ = ‘hostility’ = ‘aggressiveness’

##### Conditions:

‘anxiety’ = ‘anxiousness’, ‘drowsy’ = ‘yawning’, ‘haemophilia’ = ‘hemophilia’

##### Treatment:

The most important challenge in treatment name is the fact that medications can be mentioned either by their generic name or different brand names:

'advil' = 'ibuprofen' = 'motrin',  'sertraline', 'zoloft', 'ranitidine', 'zantac'

##### Food:

‘h2o’ = ‘water’, ‘chilli’ = ‘chili’, ‘mayo’ = ‘mayonnaise’, ‘booze’ = liquor’

To tackle this challenge, we user NLTK synonym words database. Given each word as input, this library gives different equivalents, synonyms, and also writing methods as outputs. Fortunately, the library also includes the medications generic and brand names. 

Hence, we searched through all different trackable names in the dataset, found the equivalent sets, and replaced all items in each set with one of them.


## Cleaning Age Column
For the age column, we dropped the abnormal age rows in the database. The amount of data dropped was around 0.01 % ( negligible to the total data)

## Cleaning Trackable Tags
Tags represented arbitrary text information for each user. For example “ate food “ , “sleep” etc. We applied standard text pre-processing techniques(Regular Expression) to clean the texts associated with tags. The techniques applied were stemming, lemmatization, punctuation removal etc. We majorly used regexes for this part.


