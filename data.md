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
