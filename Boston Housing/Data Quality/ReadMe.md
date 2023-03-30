# What You Didn’t Know About the Boston Housing Dataset

## We all have been training our machine learning models on incorrect data. Oops!

![img](https://miro.medium.com/max/700/1*sTIyFaSNImGkFSYdriKFZA.jpeg)

Boston at night. Photo by Mohit Singh at Unsplash

If you're studying data science you will probably come accross the Boston housing dataset. Actually, I dare you to try to google how to fit a linear regression model and **not** come accross with it. Scikit-learn even lets you import it directly with `sklearn.datasets`, along with other classic datasets.

The Boston housing dataset is small, especially in today's age of big data. But there was a time where neatly collected and labeled data was extremely hard to access, so a publicly available dataset like this was very valuable to researchers. And although we now have things like Kaggle and open government initiatives which give us plenty of datasets to choose from, this one is a staple to machine learning practice as chocolate is to a break-up.

Each of the 506 rows in the dataset describes a Boston suburb or town, and it has 14 columns with information such as average number of rooms per dwelling, pupil-teacher ratio, and per capita crime rate. The last row describes the median price of owner-occupied homes (this leaves out homes that are rented out), and it's usually the row that we are trying to predict when we use it for regression tasks.

![img](https://miro.medium.com/max/700/1*ZeYXdND4eaYmqrSzKXKKFg.png)

scikit-learn's description of the dataset, including the name and description of the columns. See anything problematic with the language? We'll address that below. [Source](https://scikit-learn.org/stable/datasets/index.html)

# How did it become so ubiquitous?

The data comprised in this dataset was collected by the U.S Census Service, and it first appeared in the history of statistical analysis in a paper by David Harrison Jr. and Daniel L. Rubinfeld, called [Hedonic housing prices and the demand for clean air](https://www.researchgate.net/publication/4974606_Hedonic_housing_prices_and_the_demand_for_clean_air)[1]. Researchers had a hypothesis that people were willing to pay more for clean air —hence the term “hedonic pricing” which in this case is used to describe the monetary value that people assign to factors not inherent to the property but to its surrounding area— but there was debate on how to measure it. Harrison and Rubinfeld were concerned:

> *While several studies have used [the housing market approach] to estimate the demand for air quality improvements, they have paid little attention to the sensitivity of the results to the assumptions embedded in the procedures.*

![img](https://miro.medium.com/max/700/1*CbtxU4C8UA_yy9IMVZ0tVw.png)

Where it all started. [Source](https://www.researchgate.net/publication/4974606_Hedonic_housing_prices_and_the_demand_for_clean_air)

To make their point, they needed a clean database with lots of variables and a precise measure of air pollution. They found this in the “data for census tracts in the Boston Standard Metropolitan Statistical Area (SMSA) in 1970”. They highlighted the quality of the data to fit their purpose:

> *Our data base is superior to others because it contains a large number of neighborhood variables (necessary to isolate the independent influence of air pollution) and more reliable air pollution data.*

This is probably why it became so popular. It was next used in Belsley, Kuh & Welsch (1980), [‘Regression Diagnostics: Identifying Influential Data and Sources of Collinearity’](https://onlinelibrary.wiley.com/doi/book/10.1002/0471725153)[2] and it has been used to benchmark algorithms ever since.

# Some problems with the original dataset and how to fix them

## The language

First of all, a sociological consideration. When we go to the canonical description of the dataset, under column 'B' it says: *'1000(Bk — 0.63)² where Bk is the proportion of* blacks(sic) *by town'*. This language is outdated and might be offensive, so please avoid it when describing this dataset. "African-Americans" or "black people" are more acceptable terms.

## Censored data

As for the quality of the data, the dataset is pretty robust but not perfect. When you do a scatter plot of the data, you quickly notice that prices of homes seem to be capped at 50. This is because the Census Service *censored* the data. Censoring data means restricting the range of possible values of a variable. In this case, they decided to set the maximum value of the price variable to 50k USD, so no price can go beyond that value.

![img](https://miro.medium.com/max/500/1*Pr0-cdzPQtjLd6fdJi6eyg.png)

Source: [my own analysis](https://github.com/martinacantaro/data_science/blob/master/datacamp_machine_learning_scientist_with_python/01_supervised_learning_with_scikit-learn/03_Boston_housing.ipynb)

That’s why, when you visualize the data, you see a sort of ceiling that flattens your datapoints at 50. In reality, these prices were probably higher. Otis W. Gilley listed the 16 cases that fall under this category in his paper [On the Harrison and Rubinfeld Data](https://spatial-statistics.com/pace_manuscripts/jeem_ms_dir/pdf/fin_jeem.pdf)[3].

It's probably impossible to find out, decades later, what the actual prices of these properties were. Although this is a very minor proportion of the total, it's important to note its potential impact in algorithm training results.

## Incorrect data

More importantly, Otis W. Gilley also rechecked all of the data against the original census data and found that eight of the median prices in the median value column were plain and simply wrong!

This is what he found:

![img](https://miro.medium.com/max/700/1*7mJYXdMIsQdTESqsONBLeg.png)

Source: Gilley (1996) [On the Harrison and Rubinfeld Data](https://spatial-statistics.com/pace_manuscripts/jeem_ms_dir/pdf/fin_jeem.pdf)

Gilley proceeded to correct the dataset, run the calculations of the original paper on hedonic pricing and check if the results still held true. Luckily for the history of data science, there were no significant changes.

> *The goodness-of-fit as measured by R2 rises somewhat when employing the corrected observations. However, the magnitudes of the coefficients did not change much and the qualitative results from the original regression still hold.*

Still, it would be best for the data science and research community to use the corrected data from now on, to avoid any potential impact on results. But is there an easy way to do this? Yes!

The good news is Roger Bivand, Jakub Nowosad and Robin Lovelace have published a [Corrected Boston Housing Database](https://nowosad.github.io/spData/reference/boston.html) which includes both the original median prices (under the original column name 'MEDV') and the corrected median prices (called 'CMEDV'). They also included data that was not previously available before, namely, the latitude and longitude of each observation, wich allows for more mapping. I think this should be our new Boston Housing reference dataset for the years to come, that's why I'm doing a pull request on scikit-learn's git repository to fix this. Hopefully it will be available to everybody soon.

# The future of the Boston Housing Dataset

Like "hello world" or "foo, bar, baz", the Boston Housing Dataset has become part of a common vocabulary. And it will remain so, not only because thoroughly labeled datasets for machine learning are still not *that* easy to find, but because using the same dataset for decades to test different algorithms has allowed scientists to control for that variable and highlight the differences in algorithm performance.

With the small improvements and considerations described in this article, this classic dataset still has a place in the future of statistics and data science, and will surely continue to serve as a canvas to hone the skills of novice and experienced practicioners alike for years to come.

![img](https://miro.medium.com/max/700/1*Pwv8MwN2ODyeCf942i1r0w.jpeg)

Acorn Street, Boston. [Source](https://unsplash.com/photos/ZLN2WOVpjCo)

# References:

[1] Harrison, David & Rubinfeld, Daniel, [Hedonic housing prices and the demand for clean air. Journal of Environmental Economics and Management](https://www.researchgate.net/publication/4974606_Hedonic_housing_prices_and_the_demand_for_clean_air) (1978), Journal of Environmental Economics and Management

[2] D. A. Belsley, E. Kuh, R. E. Welsch, [Regression Diagnostics: Identifying Influential Data and Sources of Collinearity](https://onlinelibrary.wiley.com/doi/book/10.1002/0471725153) (1980), Wiley Eds.

[3] O. W. Gilley, [On the Harrison and Rubinfeld Data](https://spatial-statistics.com/pace_manuscripts/jeem_ms_dir/pdf/fin_jeem.pdf) (1996), Journal of Environmental Economics and Management