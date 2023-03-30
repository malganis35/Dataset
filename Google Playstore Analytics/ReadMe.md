# Description







Use Case Overview


Company Name:

AlphaTech Investments

Background:

AlphaTech Investments is a well-established investment fund that specializes in identifying and investing in high-potential technology companies and products. With the growing demand for mobile applications in various industries, AlphaTech aims to expand its portfolio by investing in paid apps on the Google Playstore.

Objective:

The primary objective of this Power BI report is to analyse data from the Google Analytics Playstore to identify profitable opportunities and trends in the paid apps market. The report will help AlphaTech Investments make informed decisions on which types of apps to explore and invest in to maximize their returns.


Dataset Overview:

Data cleaning difficulty: This dataset needs a fair amount of data cleaning however, that should be quite an easy task using Power Query.


Table 1: googleplaystore.csv

    App: The name of the mobile application
    Category: The primary category in which the app is classified on the Google Playstore
    Rating: The average rating of the app, given by users (on a scale of 1 to 5)
    Reviews: The total number of user reviews for the app.
    Size: The size of the app in M (megabytes), k (kilobytes) or as 'Varies with device'
    Installs: The approximate number of times the app has been installed by users
    Type: Indicates whether the app is 'Free' or 'Paid'
    Price: The price of the app in US dollars (only applicable for paid apps)
    Content Rating: The target audience for the app based on age restrictions (e.g., Everyone, Teen, Mature 17+, Adults only 18+)
    Genres: The subcategories or genres that the app belongs to (can have multiple values separated by a semicolon)
    Last Updated: The date when the app was last updated on the Google Playstore
    Current Ver: The current version of the app available on the Google Playstore
    Android Ver: The minimum required Android version to run the app


Table 2: googleplaystore_user_reviews.csv

    App: The name of the mobile application (matches the 'App' column in the 'googleplaystore.csv' table)
    Translated_Review: The text of the user review, translated to English if originally in another language
    Sentiment: The overall sentiment of the user review, categorized as 'Positive', 'Neutral', or 'Negative'
    Sentiment_Polarity: A continuous numeric value representing the sentiment polarity, ranging from -1 (most negative) to 1 (most positive)
    Sentiment_Subjectivity: A continuous numeric value representing the sentiment subjectivity, ranging from 0 (most objective) to 1 (most subjective)


Scope:

The Power BI report can be focused on one or more of following key aspects:

    App Category Analysis: Identifying top-performing and emerging app categories based on factors such as total installs, average ratings, and revenue generation (derived from the 'googleplaystore.csv' table).
    User Sentiment Analysis: Analysing user sentiments and their polarity from the 'googleplaystore_user_reviews.csv' table to gauge user satisfaction and uncover potential areas of improvement in the paid apps.
    Demographic Insights: Utilizing the 'Content Rating' column in the 'googleplaystore.csv' table to analyze target markets and identify potential growth opportunities based on user preferences.
    Pricing Strategies: Evaluating pricing trends and revenue models by examining the 'Price' and 'Type' columns in the 'googleplaystore.csv' table to determine the most effective pricing strategies for paid apps.
    Competitive Landscape: Assessing the competitive environment by comparing app ratings, reviews, and installs in each category to identify top players and growth trends.
    App Update Analysis: Examining the 'Last Updated', 'Current Ver', and 'Android Ver' columns in the 'googleplaystore.csv' table to evaluate the impact of app updates on user engagement and retention.


Expected Outcome:

Upon completion of the Power BI report, AlphaTech Investments will have a comprehensive understanding of the paid app market on the Google Playstore. The insights gained from the report will enable the company to identify high-potential app categories and make well-informed investment decisions to maximize their returns in the paid app market.
