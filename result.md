---
layout: page
title: Result
subtitle: Findings!!!!
---
After understanding the basic data statistics, exploring all the information in columns, we gained a basic understanding of the data. Trackable name , trackable type and trackable value are the main information columns in our current data. We narrowed down on Conditions, Treatments and Symptoms contained within the trackable type columns to figure out unique insights from the data.
Some of the insights which we derived from the data revolved around the various methods we tried. Mainly, We tried to obtain correlations between treatments, conditions and symptoms. In the process if doing so we applied various data mining techniques, used visualization tools to see the results and identified some of the best insights from them.

# Association Rule Mining

Each patient experiences a set of different conditions and symptoms, and takes different medications. If we consider each user as a basket with conditions, symptoms, and treatments as items, we may be able to find interesting rules between them and also within themselves.  Since we have about 22000 subjects(baskets), chose 0.001 for minimum support value to drop any itemsets occurring in less than 20 users.
Since the frequency of different trackables are not the same, it seemed important to choose a rather small support so that the common symptoms or conditions don’t overwhelm the lower frequent ones in which we may find interesting information.
Following information and rules were obtained using association mining algorithm.

## Side Effects

We specified baskets with symptoms and treatments of each subject as items. With min_support of 0.001, we get around 60000 frequent itemsets. This big number make sense since we’re using a small support. Beside, some of the symptoms and medications are very frequent as it was shown in the data analysis section e.g. ‘fatigue’. These items produce unimportant frequent itemsets and association rules, since their prior probability of existence is very high. 
Hence, we generated the association rules based on min_lift = 1 and min_confidence = 0.4.
Using lift as a criteria helped rule out those frequent items.
Also, since we are interested in finding the side effects of the treatments, filtered the rules in which the antecedents are only treatments.
Finally, we got 88 rules. 

The below results explain some examples of the side effects we found after applying association rule mining in the way mentioned above.
![Table](/img/data/assoc_table.png){:class="img-responsive"}

A graphical visualization for this rules would be.
![Table](/img/data/assoc_graph.png){:class="img-responsive"}

Blue Nodes indicate the Rules and the nodes connected to the directed edges coming in and out are the left and right side items of the rules respectively.
After fine tuning the parameters, we found that for a Support of 0.001,C=0.4 and lift = 2 most of the rules contained side effects.

![Association](/img/data/assoc_pie.jpg){:class="img-responsive"}

If we pick a particular treatment/drug like Fludrocortisone. It was prescribed to a total of 62 users and out of them 53 people suffered from nausea and headache which we identified as side effects. So in Conclusion a lot of people suffered from the side effects which we discovered from the rules.


# Recommender System
### Effectiveness Metric Computation For Recommender System
To recommend effective treatments for conditions and to know how effective treatments were, we used the effectiveness as the measure.
To compute effectiveness:
* We extracted the unique conditions, computed the minimum start date for that condition among all users.
* Then we averages out the severity scores for the start data to compute value before.
* Same thing we followed for the end data ( we took max in this case ) to compute value after.
* Then we again to the mean of these two to get the effectiveness score. 
* We treated positive score as effective and negative as not effective and the value indicates the extent of it.
Recommender system predicts this effectiveness using SVD++ to recommend effective treatments for conditions. 
Also using this metric , we came up with the following indirect insights from the data.
For all the conditions recommended treatments like ( ocular migrane, gag reflex etc )  did not work out and they were extremely hard to manage .The effectiveness score for these conditions for the treatments in general was pretty low.


![Recommender](/img/data/cond_top10.png){:class="img-responsive"}
![Recommender](/img/data/sym_top10.jpeg.jpg){:class="img-responsive"}

The analysis on a symptom level on the positive side indicated that for common symptoms like splitting, sore hands ( etc) the treatments recommended were generally effective ( indicating high curablility).
RMSE for the SVD ++ recommender system – 0.97 ( effectiveness metric )

# Prediction of Condition Based on Symptoms
Using the Decision tree based prediction ( XGBoost ) we represented each condition experienced by different users as a vector of symptoms. So for the prediction model these symptoms were features. So we handpicked most common conditions converting this problem into a multi-class classification( one vs another). We got an F1-Score of 74% as the final result.
* Precistion = 0.97
* Recall = 0.59
* F-1 = 0.74
Final parameters used are max_depth = 4, booster = gbtree, eta = 0.3, max_bin = 256.

# Data Insight
![Insight](/img/data/common_by_family.jpg){:class="img-responsive"}
For all the conditions present the data, the above figure represents the count of the conditional families present in the data. The families were obtained from another data source??? and we combined the two datasets to categorize the conditions by families. We found that among all chronic illnesses Neural conditions are the ones experienced mostly by the users.

![Insight](/img/data/weather_sev_corr.jpeg){:class="img-responsive"}
Analysing the weather tags in the data we found another interesting insight as reflected in the figure above. The weather stability has an impact on severity conditions and in general we observe that the average severity of all conditions is pretty low when the weather conditions are stable.

![Insight](/img/data/sev_count_plot_grouped.jpeg){:class="img-responsive"}
Exploring on the severity index alone we found that around 23.2% of the users suffer from chronic condition giving them high severity. So Majority of the users suffer severely.