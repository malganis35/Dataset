# Data quality impact on the dataset

## We look at the different aspects of data quality that impact on the dimensions of our dataset, and the importance of data quality in the organization that produces it.

![img](https://miro.medium.com/max/700/0*FZlraFqhG8n_jZDg)

Photo by [Carlos Muza](https://unsplash.com/@kmuza?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

# Background

For the last year, my introduction in the machine learning field has been the focus on learning how to solve regression or classification problems on a given dataset.
When we started working on real use cases, we found that the dataset we received is the result of an organization that has developed a work to be able to elaborate it.
The quality of that dataset is directly related to the organization that manufactures it and how that organization works on data quality.
The sustainability of our model could also be related to the quality of data in the organization.
Beyond data engineering, the accuracy of the model itself, and the performance in its production, if the organization it serves does not have data quality as a priority, probably the model will not be sustained over time.

## Then, what is data quality?

First, the data represents real-world objects, to talk about data quality in this article, we will work on a dataset format. Each column is a “dataset” of the dataset, and each cell is the particular value that that dataset acquires for a row.
Usually, when we think about data quality, we think about the value of the data and its accuracy. However, data quality encompasses multiple aspects, which are called dimensions and which we will discuss in more detail later, but are common dimensions of data: accuracy, uniqueness, completeness, validity, consistency.
The most common definition of data quality is that which determines that the data can fulfill the function for which it was collecting.

## Importance and benefits

> Maintaining data quality is a difficult but necessary task. In order to achieve consistent and reliable data, businesses must constantly manage data quality so that they build trust and enable quicker, more knowledgeable decisions*.¹*

Poor data quality has a direct impact on the effectiveness and efficiency of the organization, especially over the entire life cycle of a task, and errors in different dimensions of the data can lead to financial losses or serious errors.
In contrast, an organization that works on the quality of the data it collects and produces, benefits on different levels:

- Incomplete or duplicated information is avoided.
- Saves on communications and quality of service
- Saves the cost of non-quality data, which leads to the cost of data quality paying for itself
- Significantly improves the quality of results and inputs for future models or organizational decision making

Undoubtedly the importance of data quality; the severity of the impact of errors and benefits vary from one use case to another, so it is difficult to cover these concepts conceptually without applying them directly on an example

# Types of errors in a dataset

To develop the content of this case study article to help us affirm the concepts, we will use the well-known Kaggle dataset for learning: [Housing Prices Competition for Kaggle Learn Users](https://www.kaggle.com/c/home-data-for-ml-course/overview)²

![img](https://miro.medium.com/max/700/1*JACi9AS5DmyQn8V4NtxiUg.png)

![img](https://miro.medium.com/max/700/1*P2ZJvyjj5Dk-kEnV_V0UtQ.png)

## Errors due to incomplete information

They can refer to missing cells within a datum (for example, the Alley field contains only 91 of the 1460 records, or worse, the “PoolQC” field). These are the famous “null” or “NaN” fields.

![img](https://miro.medium.com/max/494/1*guOSzwZ67hYVuTEw0vUJNQ.png)

But they can also be errors due to the omission of some data that may be relevant to a study.

Specifically, for the exercise of predicting sales prices, if in the dataset designed the “Neighborhood” or “LotArea” column was omitting, the quality of the predictions would be strongly affected.

![img](https://miro.medium.com/max/700/1*3bWF47Qls3a-rq8P4faogQ.png)

Null values visualization using missingno

![img](https://miro.medium.com/max/700/1*4ANpLlkHgNFX2IMKOx8gwg.png)

Correlation matrix about the location of missing values

## Syntax errors

Syntax errors are related to the format of the data and how its value is representing. For example, in the YearBuilt field, we could not find values lowers than in 1700, or higher than the current year (2020).

In other hands, the Street data can support the following values:
Grvl — Gravel
Pave — Paved
If we found a value different from these and different from null, we would be facing a syntactic error.

![img](https://miro.medium.com/max/278/1*aUFFskz851d3BpO58ypxZg.png)

If a date field is expecting to be in the format MM-DD-YYYY and some cells are YYYY-MM-DD or DD/MM/YYYY, we are also facing a syntax error.
As it is a dataset for educational use, it is challenging to find syntactic errors in the data. Still, we could look for outliers values, taking, for example, column GrLivArea, a data that appears in the last quintile that could be wrong entered data.

![img](https://miro.medium.com/max/326/1*Ymp_T8vIumUZo1aPMqiYCg.png)

## Semantic errors

Semantics conveys the meaning of data.
If in building year we input the sale year, we will have correct data from the syntactic (a valid year), but not from the semantic point of view.

![img](https://miro.medium.com/max/354/1*1qL2kDaaNoOCC3DweIgXow.png)

No houses with YearBuilt greater than YearSold

However, if we look at the renovation year, data should indicate whether there was remodeling after construction and before sold. But we found a row in which the year of reconstruction is after the sale:

![img](https://miro.medium.com/max/383/1*4RsIVUyh0xRPlrBcDCZFmw.png)

*YearRemodAdd: Remodel date (same as construction date if no remodeling or additions)*

In this case, we faced with an error that can be syntactic and semantic:

- If there is no remodeling, it is syntactic since according to the definition the year if there is no remodeling, it must be equal to the year of construction
- If remodeling was 2008, it is a semantic error since it does not represent a remodeling in the period between building and sale.

A clear semantic error would be that the data “sale price” contains the area of the land (data entry error) or that the sale price corresponds to a partial commercial transaction, for example, a partial ground sale.

# Data quality dimensions

At the beginning of this article, we mentioned some dimensions of quality: accuracy, uniqueness, completeness, validity, consistency.
One **dimension** is a set of quality factors with the same purpose; accuracy as a dimension is composed of semantic accuracy (closeness of the value to reality), syntactic, and precision (adequate scale of the data), among others.
A **metric** is a mechanism we use to measure one of the factors of the dimension, for example, the semantic correctness in the dimension accuracy of the LotArea data, we are going to measure it in the difference of square feet between the real value, and the one entered to the dataset.
The **measurement** is the process that implements the metric to obtain the value on the dimension factor. In the same example of the LotArea data, the dimension accuracy, the precision factor, the “difference in square feet” metric can be measured by a professional, estimated by an evaluator, using computer tools such as GoogleMaps®, etc.

![img](https://miro.medium.com/max/700/0*dgPAkeJEEUqRcamR)

Photo by [Linda Perez Johannessen](https://unsplash.com/@linper?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

Over time, measurement processes evolve, or by characteristics of the type of problem, the same metric applied to a dimension can be measure in different ways, even as a way to validate or improve the measurement.
Dimensional factors can be related to their value (e.g. accuracy) as well as their intention and scheme (e.g. syntactic and semantic correctness).

## Main dimensions of data quality

The names and approaches to defining dimensions corresponding and applying to each data of our dataset can vary given the context, as well as the theoretical and conceptual framework with which they are analyzed and defined.

## Accuracy

> The proximity between a data value v and a data value v’, considered as the correct representation of the real-world phenomenon that v tries to represent.³

**Semantic correctness**: Proximity between the value *v* of an attribute and its real value *v’*.
If we have the LotArea data that represents the square footage of the land and in a cell, but if the price of the transaction is registered here by mistake, we will have a very weak correction (unless by chance the price and area data are similar!).
If, on the other hand, the square footage of the land is inputting in the data, the semantic correction is strong.

**Syntactic correctness**: It represents the proximity between the value *v* of an attribute and the elements of the domain of definition of this attribute. If the YrSold data is representing, years of sales after today, or before the beginning of the dataset records, cannot be included.

**Accuracy**: Captures the degree of detail that a data has that makes it useful for a specific use or that allows it to be discriminating from other data that are not the same.
If the LotArea data is in hectares without decimals, it would not be handy for estimation in urban datasets.
If you want to measure the time of production processes and you do not store the “Hour, minute, second”; if you only save the starting and finish day, you will not be able to access the calculation of hours, minutes, and seconds.

## Consistency

> It captures the violation of semantic rules defined over a set of business entities or their attributes. In a relational model, integrity constraints are an example of such semantic rules.³

**Inter-entity integrity:** It captures rule satisfaction between attributes of different business entities. Also known as referential integrity refers to an attribute of an entity consistency with other entities.
For example, in a list of items of a recipe, the product code is related to a “products” entity, it is a violation of that rule if the recipe has an item with a non-existent product code, or that was removed from the products entity.

**Intra-entity integrity:** Captures the satisfaction of rules between attributes of the same entity. Also known as relational integrity, it refers to the integrity within an entity.
For example, one address with the zone belongs to the state.
Or in the recipe example, where the item is from another recipe or one procedure does not apply to one thing (e.g., beating the flour).

**Domain integrity:** Captures the satisfaction of rules about the possible values that an attribute can take
Examples of domain integrity violations are if the identity document types admitted on an input-form can be passport or DNI, and a civic credential is registering.

## Completeness

> Captures the satisfaction of rules about the possible values that an attribute can take³

**Coverage:** Captures the ratio of the number of entities in a given data collection to the total number of entities that should exist in that collection.
Coverage measurement can be on a closed domain or an open domain.
The coverage ratio is the proportion of covered items over the total items in the domain.

**Density:** Captures the ratio of the number of attribute instances with non-zero values to the total number of instances of that attribute
The density ratio will depend on the criterion assumed about the null values of a certain data.

## Uniqueness

> It captures the degree to which a piece of real-world data is uniquely representing.³

**Non-duplication**: Captures the degree of duplication (or repetition) of the same data. It refers to the possibility of a tuple being duplicated in the dataset representing the same entity.
In the case of the housing dataset, each tuple represents a transaction, so the definition of uniqueness is not given by having two tuples referring to the same property, but yes to the same transaction on the same property.
In a club roll, for example, a case of duplication would be two rows representing the same person.

**Non-contradiction:** Captures the degree of duplication (or repetition) of the same instance of the real-world entity that is represented with contradictory data.
For example, it refers to a club’s membership that has two tuples with similar identifiers (for example, DNI 1971449–3 and 1971449–8) referring to people with similar names but different addresses or contradictory data (different genders).

## Timeliness

> Captures how quickly real-world changes are reflecting in updated data³

**Freshness** is a type of non-structural accuracy dependent on the time variable, which means that data that is correct at one time may not be correct at another time.

**Actuality:** Captures the time delay between a change in the real world and the corresponding data update.
If age is represented in its numerical value without referring to the date of birth, it systematically presents a problem of actuality.
The same applies to any measurement of a living organism.

Could exist some exogenous changes to the nature of the data; for example, the telephone company decides to add a prefix to all phones in such an area as of March 1. If no update is applying to the data, it automatically becomes out of date on that day.

**Timeliness:** Captures the delay between the update of data and the moment it is available for use.
For example, if we carry out a study on the evolution of sales in the last year, and the meeting delayed by six months, we will inevitably face a problem of the opportunity of the validity of the data.

# What to do in the organization?

![img](https://miro.medium.com/max/700/0*nbgLtHyog-Ewx8sB)

Photo by [Maximilian Weisbecker](https://unsplash.com/@maximilianweisbecker?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

## Data Governance

> A large amount of data that company’s business processes are delivering is a source of information that can help generate value by supporting decision making with quantitative, reliable, and timely elements. This need to use data to generate relevant information requires the establishment of a set of definitions, rules, and processes that regulate how the data will be treated, this set is called Data Governance.⁴

Data governance affects different aspects of the organization, such structure, rules, decision making, responsibilities, and the entire operation of data management.

The organization data governance programs, then, are aimed at improving some or all of the above aspects.

Usually, we work with one of the following frameworks:

- DMBOK — Data Management Book of Knowledge. It provides specific details to define, implement, and operate the Management and Use of Data.⁵
- TOGAF — The Open Group Architecture Framework. Defines the process for creating a data architecture as part of the overall architecture of an enterprise. It can be a precursor to implementing Data Management.⁶
- COBIT — Control Objectives for Information and related Technology. It delivers Data Governance as a part of the overall Governance of the Information Technology area. It has a model to determine the degree of maturity of the Data Management processes in use in an organization.⁷
- DGI Data Governance Framework. It is a simple reference framework to generate Data Governance. It provides a logical structure to classify, organize, and communicate complex decision-making activities and the execution of actions related to the data of an enterprise.⁸

## Six-sigma methodology

> The method applied, which is called DMAIC (Define, Measure, Analyze, Improve, Control), uses statistical tools, as well as devices that observe process variables and their relationships, which help manage their characteristics.
> In short, it is a data-based method for taking Quality to near-perfect levels, different from other approaches because it also corrects problems before they occur. More specifically, it is a disciplined effort to examine companies’ repetitive processes.⁹

e c

# Summary

We have tried to develop some definitions linked to data quality, to introduce the concept within artificial intelligence, machine learning, or data scientists enthusiast.

In the different courses and tutorials focused on these disciplines, we rarely think about the origin of the dataset and the work that the organization that delivers it does to generate it.

When we work on real-life use cases and models that must be fed back and retrained with the new information, we will find that the level of data quality of the organization can make our work fail in the long term.

We must be attentive to all these elements before putting the work in production and help organizations to improve it.

## References

[1] https://www.edq.com/glossary/data-quality-importance/

[2] https://www.kaggle.com/c/home-data-for-ml-course/overview

[3] [https://www.gub.uy/agencia-gobierno-electronico-sociedad-informacion-conocimiento/sites/agencia-gobierno-electronico-sociedad-informacion-conocimiento/files/documentos/publicaciones/Framework%20para%20la%20Gesti%C3%B3n%20de%20la%20Calidad%20de%20Datos%20v1.0.pdf](https://www.gub.uy/agencia-gobierno-electronico-sociedad-informacion-conocimiento/sites/agencia-gobierno-electronico-sociedad-informacion-conocimiento/files/documentos/publicaciones/Framework para la Gestión de la Calidad de Datos v1.0.pdf)

[4] https://msaffirio.wordpress.com/2017/01/11/gobernabilidad-de-datos/

[5] https://www.dama.org/content/body-knowledge

[6]http://www.opengroup.org/subjectareas/enterprise/togaf

[7] http://www.isaca.org/cobit/pages/default.aspx

[8] http://www.datagovernance.com/the-dgi-framework/

[9] http://triflenew.blogspot.com/2015/03/six-sigma.html

## Sources

[FING: https://www.fing.edu.uy/inco/grupos/gris/wiki/uploads/ProyectosGrado/ValverdeBianchi-ProyGrado.pdf](https://www.fing.edu.uy/inco/grupos/gris/wiki/uploads/ProyectosGrado/ValverdeBianchi-ProyGrado.pdf)

AGESIC: [https://www.gub.uy/agencia-gobierno-electronico-sociedad-informacion-conocimiento/sites/agencia-gobierno-electronico-sociedad-informacion-conocimiento/files/documentos/publicaciones/Framework%20para%20la%20Gesti%C3%B3n%20de%20la%20Calidad%20de%20Datos%20v1.0.pdf](https://www.gub.uy/agencia-gobierno-electronico-sociedad-informacion-conocimiento/sites/agencia-gobierno-electronico-sociedad-informacion-conocimiento/files/documentos/publicaciones/Framework para la Gestión de la Calidad de Datos v1.0.pdf)

Experian: https://www.edq.com/glossary/data-quality-importance/

Sigma: http://sigma-data.com/que-es-la-calidad-de-datos/

CPE — Data quality and machine learning courses