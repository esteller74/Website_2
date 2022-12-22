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

{% include repartition_of_pageviews_19_20.html %}

# 2. Does the week make sense pre-covid?

The purpose of this part is to find out if people had habits in the way they consulted wikipedia before Covid, and what those habits were, always by keeping in mind that we are interested in the change of pace during the week in this project.

## 2.1. Is the week a pattern?

Our intuition was that we could find a weekly pattern in the pageviews of Wikipedia, as we think it is not consulted in the same way by the population on working days and on days off. On the graphs below, the number of pageviews for each category and for each country are displayed from January, 1st of 2019 to July, 31st of 2020 for both desktop devices and mobile devices. **A weekly pattern is clearly identified**, for both desktop and mobile devices. For desktop devices, we can see a decrease, for all categories, of the number of Wikipedia pageviews from Friday to Saturday or Sunday for the majority of the countries. We can also notice that the number of pageviews for all the categories decreases during the summer holidays compared to the rest of the year, except for Japan, as people tend to be less on their computer during holidays. The weekly pattern is less pronounced but is still here when looking at the numbers. For both interfaces, an increase of the number of pageviews for all categories is visible for some languages due to the restrictions imposed by the government because of the Covid-19 pandemic from, in general, around March 2020, depending again on the considered language. The rise is very pronounced for Italy, Japan and Serbia. Note that both countries, Serbia and Italy, were lockdowned. 

{% include evolution_of_views_desktop.html %}
{% include evolution_of_views_mobile.html %}

This intuition has been confirmed, for most of the country, in a more formal way through the use of the **autocorrelation** to identify patterns. Except for South Korea, we get peaks at lags k = 7xn, meaning that we see a **repetitive pattern every week**. Thus, for the rest of our analysis, we decide to discard South Korea and to keep all the others.

## 2.2 How can it be grouped within the week?

As we know now that a week pattern exists, we would like to see if some days of the week can be grouped together and if we can distinguish, through the way wikipedia is consulted, some days that are similar within the week. Our intuition was that workweek days should form a first group and that week-end days should form another one. 
In reality,  the distribution of the week days depends on the studied country and also on the studied period. 
However, our intuition has been partially confirmed by computing a first approach ​which consists in **computing t-tests** between each day of the week in 2019 and looking at the p-value result.

{% include pvalues.html %}

The heatmaps above reflect the results of the p-value between each day of the week for each language and for 2019 year obtained from t-tests. Dark green cells means that we do not reject the null hypothesis of equal population means between the 2 different days (p-value greater than or equal to 0.05). By bearing in mind that these results could be biased by the presence of cofounders, we can see that some languages have groups of days within the week. This pattern within the week depends on the languages. 

Please, note that the p-value do not reflect any notion of similarity between days and that we can't really get more out of these results.

Thus, to get a notion of similarity between days of the week and also between days within a group of days, we decided to calculate **attention vectors and similarity matrices**. The latter will allow us to see inside each group which day is similar to which day and if the similarity is repeated among groups.



# 3. Does the week change with Covid?

{% include most_read_topics.html %}

# 4. References

[1] [M. Ribeiro, K. Gligoric, M. Peyrard, F. Lemmerich, M. Strohmaier, R. West, *"Sudden Attention Shifts on Wikipedia During the COVID-19 Crisis"*, 2020](https://arxiv.org/pdf/2005.08505.pdf)

[2] [Steven Goodman, *"A Dirty Dozen: Twelve P-Value Misconceptions"*, 2008](https://sixsigmadsi.com/wp-content/uploads/2020/10/A-Dirty-Dozen-Twelve-P-Value-Misconceptions.pdf)

[3] [K. Gligorić, A. Chiolero, E. Kıcıman, R. W. White, R. West, *"Population-scale dietary interests during the COVID-19 pandemic"*](https://www.nature.com/articles/s41467-022-28498-z)




[![Wikipedia-logo-en-big.png](https://i.postimg.cc/BZrzMTbt/Wikipedia-logo-en-big.png)](https://postimg.cc/SjGVKzWp)
