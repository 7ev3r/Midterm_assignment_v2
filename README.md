# **BoozePal**
for ![image](https://www.whiskybase.com/images/logos/default@2x.png)
## Overview

Goal of this project is to build **BoozePal** (assistant in choosing) and help to pick best "drink" for you.
Using [Whiskeybase.com](https://www.whiskybase.com) for [top 1000](https://www.whiskybase.com/whiskies/top1000) rated whiskies and [released/bottled in 2022](https://www.whiskybase.com/whiskies/new-releases) to get : user ratings, user names, and the whiskeys to build df for **BoozePal**

*Please see below for how **BoozePal** works.

## Scraper:

[scraper.ipynb](//github.com/7ev3r/Midterm_assignment_v2/blob/742bc3a1980443d46c188bf2093d426414c8c162/scraper.ipynb)

Using Selenium and BeautifulSoup to log in and to grab the necessary data :
- the users
- the ratings provided by the users
- the price from a specific whiskey product webpage
- the url links for each whiskey page

Adding the data to a dataframe and moving to a csv's

Result :  
**Whiskey_Released_in_2022_Data.csv**  
**Whiskey_Top_1000_Data.csv**

## Data clean :

[cleaning_data.ipynb](https://github.com/7ev3r/Midterm_assignment_v2/blob/742bc3a1980443d46c188bf2093d426414c8c162/cleaning_data%20.ipynb)

Consolidating the datasets and remove NaN values/duplicates ,
filterirn users with more than 5 reviews,
moving to a csv

![image](Images/Rating_count.png)

Result :  
**Clean_whiskey_data.csv**

Mostly with only highly rated whiskeys

*looks good , moving forward

## Running local MySQL server and uploading data from .csv to created db

![image](https://github.com/7ev3r/Midterm_assignment_v2/blob/742bc3a1980443d46c188bf2093d426414c8c162/Images/XAMMP_mysql_server.jpeg)

Checking with MySQL Workbech table content

![image](https://github.com/7ev3r/Midterm_assignment_v2/blob/742bc3a1980443d46c188bf2093d426414c8c162/Images/View%20table%20contents%20in%20Mysql%20workbench.jpeg)

*looks good , moving forward

## Connecting to local MySQL server and getting data from db

[connect_to_db.ipynb](https://github.com/7ev3r/Midterm_assignment_v2/blob/956eae7ea01389d105892228d439c7204b0cece5/connect_to_db.ipynb)

![image](https://github.com/7ev3r/Midterm_assignment_v2/blob/9e119b5f0a6458b92636a6191704eac63f4f909d/Images/connected_to_db.png)

## Initial EDA

After consolidation the datasets and removing duplicates, checking how the users were rating the whiskies :

[EDA.ipynb](https://github.com/7ev3r/Midterm_assignment_v2/blob/742bc3a1980443d46c188bf2093d426414c8c162/EDA.ipynb)

*dataframe has : 
Reviews : 33304  
Unique Users count : 2519  
Unique Whiskey_ID's : 2294  

![image width="500" height="400"](https://github.com/7ev3r/Midterm_assignment_v2/blob/742bc3a1980443d46c188bf2093d426414c8c162/Images/df_screen.jpeg)

Most of the users rated the whiskies prety high ,reviews range from mid 80's to 100. 
*whiskies are part of the top rated whiskies list

![image](Images/Ratings.png)

Most of users reviewed many different types of whiskies , *very active ppl :)

![image]Images/Num_of_Reviews_by_IDs.png)

To have enough data points to leverage, checking ones who have over 5 reviews in total

![image](Images/Num_of_Reviews_by_WID.png)
![image](Images/Num_of_Reviews_by_count_IDs.png)

Price range allows to find something for "every pocket"

![image](Images/Price_range.png)

## Initial Models

Using [Google Colab](https://colab.research.google.com/drive/1ePdNEIjuDbF8JMM9RPl9X-yOfEBSdxp0#scrollTo=t7MW5F3WghyP) notebook :

[Train_ML_model.ipynb](https://github.com/7ev3r/Midterm_assignment_v2/blob/d6806a113699a518bcd3b0573d9b4a3cc8263724/Train_ML_model.ipynb)

*somehow cant use Surprise as Python scikit for building and analyzing recommender systems that deal with explicit rating data in VS Code

- Compared different models with Surprise : SVD, KNN_Basic,KNN_Baseline
*Results of all 3 models were close with a RMSE around 2.8
- Testing the model
- Getting result : not perfect but working! **BoozePal**   

![image](https://github.com/7ev3r/Midterm_assignment_v2/blob/807fde58d774d3384a94881c29f911ee2babab40/Images/Recomendation_1.png)

## Conclusion

- **BoozePal**  Selects whiskey for you ! according to the specified budget and after your evaluation of the proposed options from the list of highly rated drinks by site visitors
- **BoozePal** also provides URL links to give additional information , in case you decide to get more detailed information about recomendet drink
