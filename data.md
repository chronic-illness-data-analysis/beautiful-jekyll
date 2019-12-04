---
layout: page
title: Data
subtitle: Let's Explore!!!!
---
# Introduction
Flaredown is an app that helps patients of chronic autoimmune and invisible illnesses improve their symptoms by avoiding triggers and evaluating their treatments. Each day, patients track their symptom severity, treatments and doses, and any potential environmental triggers (foods, stress, allergens, etc) they encounter.

# About the Data
The data is collected with the main intention of tracking a set of trackable values over a period of time. Each row in the dataset represents what a user logs for his current condition. The user can log anything, like

1. Symptom
2. Treatment
3. Tag (like “tired”)
4. Weather
5. Food

etc…

The user logs the data in mainly three fields trackable name, trackable type and trackable value. For a symptom, trackable type = “symptom”, trackable name = “joint pain” , trackable value = “2” (severity of symptom).  
Along with this information we also have the user profile information like:
1. Age
2. Sex
3. Country
4. Check-in Date ( The day user logs the trackable values)

# User Profile Information
## Sex

![Sex](/img/data/sex.jpg){:class="img-responsive"}

Currently majority of the data has more females than men. So if we consider sex information in our models , we need to be careful about this bias.

## Country

![Country](/img/data/country.png){:class="img-responsive"}

Here we see that the majority of people who have logged are from US.

**Conclusion: The attributes sex and country have huge bias and using them in our models will not add any new information.**


## Conditions
There are total 5191 unique conditions in the entire dataset and 505461 reported measures. Please check the below plot to understand the overall distribution.
![Condition](/img/data/condition_counts.png){:class="img-responsive"}

Each of the conditions are associated with severity measure. This value range from 0 to 4, where 0 is least severe and 4 is most severe.
![Condition](/img/data/sev_count_plot.jpeg){:class="img-responsive"}

We grouped the severity in 0,1 to low, 2 to medium, 3,4 to very high. This help us to get an overall understading of the suffering a normal patient and importance of our project. 23.2% reported very high severity was very shocking to us also.
![Condition](/img/data/sev_count_plot_grouped.jpeg){:class="img-responsive"}

Let's look at the condition tag cloud.
![Condition](/img/data/wc_condition.jpeg){:class="img-responsive"}

## Symptoms
There are total 11547 unique conditions in the entire dataset and 1571134 reported measures. Please check the below plot to find the overall distribution.
![Symptoms](/img/data/Symptom_countts.png){:class="img-responsive"}

Let's look at the symptom tag cloud.
![Symptoms](/img/data/wc_symptom.jpeg){:class="img-responsive"}


## Treatment
There are total 4649 unique conditions in the entire dataset and 383201 reported measures. Please check the below plot to find the overall distribution.
![Treatment](/img/data/treatment_counts.png){:class="img-responsive"}
