---
layout: page
title: Conclusion
subtitle: Winding Up!!
---

# Challenges We Faced
![Winding Up](/img/data/Challenge.jpg){:class="img-responsive"}
* The dataset contained very large number of unique values for the columns conditions, symptoms and foods. Although we processed these columns to remove synonyms and equivalents, we still have around 6000 unique symptoms and 5000 conditions. Logically, we cannot have that many different values. It’s a very time-consuming task to look through them and find out what is making the list that big. With a quick skimming through the dataset, it seemed many of the entries just give additional unnecessary information about a common symptom. E.g. left knee pain and right knee pain.
* The dataset is very unbalanced with respect of some columns. For instance, looking at the frequency bar plot of the symptoms and conditions shows the first few ones contain the majority of the records. This unbalance is a very big obstacle for many of the methods and models, pushing the analysis towards only a few of the values.
* There is not enough diversity in the subjects at least with respect of their country of origin. Indeed, there’s no more information about the subjects that just their sex and country. More biographical and physiological information could be very helpful in clustering the subjects or relating some information to inter-subject differences.
  

# Future Works
![Winding Up](/img/data/future-of-work-remote.png){:class="img-responsive"}
* Since the dataset includes continuous measurements of different trackables, it is very likely that there are important information within the time-series data that could be extracted using recurrent models such as LSTM, rather than just looking at the initial and final values.
* More advanced text processing on trackable names could merge them into a much smaller list that could open a window into more reliable models and analysis. Specifically, the column named ‘tags’ contained a huge amount of information which would be usable if processed and classified.
* As we stated before, there are many different unique food names. As far as it’s related to the medical side, only major ingredients of the food matter not their name. For instance, steaks and hamburgers can be interpreted the same thing from a medical point of view. Processing of the food names and  Joining them with an additional database classifying the foods based on their major ingredients makes it possible to use food as an additional trackable in the analysis. 

# Refernces
*  Rakesh Agrawal and Ramakrishnan Srikant Fast algorithms for mining association rules. Proceedings of the 20th International Conference on Very Large Data Bases, VLDB, pages 487-499, Santiago, Chile, September 1994.
*  Jia, Yancheng (September 2014). Users' brands preference based on SVD++ in recommender systems. 2014 IEEE Workshop on Advanced Research and Technology in Industry Applications (WARTIA). IEEE. pp. 1175–1178. 
*  Chen, Tianqi; Guestrin, Carlos (2016). "XGBoost: A Scalable Tree Boosting System". In Krishnapuram, Balaji; Shah, Mohak; Smola, Alexander J.; Aggarwal, Charu C.; Shen, Dou; Rastogi, Rajeev (eds.). Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, San Francisco, CA, USA, August 13-17, 2016. ACM. pp. 785–794. arXiv:1603.02754. doi:10.1145/2939672.2939785.
*  FlareDown dataset https://www.kaggle.com/flaredown/flaredown-autoimmune-symptom-tracker