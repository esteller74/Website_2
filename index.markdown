---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

**Abstract:**
The whole world suffered the consequences of the covid-19 pandemic. The daily life of people and their habits were changed abruptly by the (mobility restricting) sanitary measures put in place in different countries. Before covid, work and leisure defined the different days of the week, creating a certain pattern, which, as we’ll find out, had a periodicity of a week. Now, the interesting question is whether the covid-19 pandemic made us lose sense of this typical week. In other words, what we want to see is if there was a pattern initially, how did it change during covid. Wikipedia is known to be a relatively good measure of people’s search queries and computers and phones are increasingly defining people’s lives. Wikipedia viewership thus has the potential to enlighten us on the changing habits of people as mobility restrictions due to covid happened. We all have a feeling that our routines changed but can we prove it? And can we quantify it? 


[![31045677.jpg](https://i.postimg.cc/FshFqWbr/31045677.jpg)](https://postimg.cc/K4sy35sw)

# 1. Goal of the study

In this datastory, we will try to answer the 2 following questions:
* **Are there Wikipedia viewing habits (patterns) during a normal year (year without covid)?**
* **Considering viewing habits vary from work week to weekends, did this pattern change during covid? And if so, how?**


## 1.1 Dataset
We will work with one principal dataset that comes from a paper called “Sudden Attention Shifts on Wikipedia During the COVID-19 Crisis”, published by Manoel Horta Ribeiro, Kristina Gligoric, Maxime Peyrard, Florian Lemmerich, Markus Strohmaier, and Robert West in 2020. It contains aggregated time-series of wikipedia pageviews for 12 languages and for each of them, there are pageviews from mobile and desktop devices separately.
Among the 12 languages, we decided to study only 9 of them that you can find in the following table containing the mobility change point date, the return to normalcy date for each language and if the origin country of the language has undergone a lockdown.


| **Country**          | Danemark `da`| Finland `fi`|Italy `it`| Japan `ja`| Netherlands `nl`|Norway `no`| Serbia `sr` |South Korea `ko` | Sweden `sv`|
|:---------------------:|:-----------:|:----------:|:---------:|:--------------:|:---------:|:--------------:|:------------:|:----------:|:---------:|
| **Mobility Change Point**| 2020-03-11 |2020-03-16|2020-03-11| 2020-03-31| 2020-03-16|2020-03-11|2020-03-16 |2020-02-25|2020-03-11|
| **Normalcy Change Point**| 2020-06-05 |2020-05-21|2020-06-26| 2020-06-14| 2020-05-29|2020-06-04|2020-05-02 |2020-04-15|2020-06-05|
| **Lockdown**| Yes|No|Yes| No| No|Yes|Yes |No|No|

**Note:** In our case “change due to covid”, is actually a “change due to the mobility change caused by covid”. The beginning of the covid period and the beginning of mobility restrictions for each country will be considered to be the same in this study.

**Note 2:** In our study, we will associate a language with the country where it is primarily spoken. For example, this means that we assume that the readers of Wikipedia in Swedish are representative of all the citizens of Sweden. You can note that we have retained only languages that are the mother tongue of one unique country.

The pageviews are distributed among 64 topics which can be grouped into 4 categories: 
* Geography, 
* History and Society,
* Culture and, 
* STEM (Science, Technology, Engineering, Maths). 

{% include most_read_topics.html %}


# 2. Does the week make sense pre-covid?

The purpose of this part is to find out if people had habits in the way they consulted wikipedia before Covid, and what those habits were, always by keeping in mind that we are interested in the change of pace during the week in this project.

## 2.1. Is the week a pattern?

Our intuition was that we could find a weekly pattern in the pageviews of Wikipedia, as we think it is not consulted in the same way by the population on working days and on days off. On the graphs below, the number of pageviews for each category and for each country are displayed from January, 1st of 2019 to July, 31st of 2020 for both desktop devices and mobile devices. A weekly pattern is clearly identified, where we can see a decrease, for all categories, of the number of Wikipedia pageviews from Friday to Saturday or Sunday.

{% include evolution_of_views_desktop.html %}

This intuition has been confirmed in a more formal way through the use of the autocorrelation.

## 2.2 How can it be grouped within the week?

# 3. Does the week change with Covid?

# 4. References

{% include repartitions_of_topics.html %}

{% include repartition_of_pageviews_19_20.html %}

[![Wikipedia-logo-en-big.png](https://i.postimg.cc/BZrzMTbt/Wikipedia-logo-en-big.png)](https://postimg.cc/SjGVKzWp)
