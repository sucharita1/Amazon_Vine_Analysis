# Amazon_Vine_Analysis
Analyzing Amazon reviews written by members of the paid Amazon Vine program versus the unpaid reviews for dataset based on camera and related products stored in Amazon AWS using postgres RDS and analysed using PySpark on Google Colab Notebooks.

## Overview of the analysis: 
The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review. Being a Data Analyst at BigMarket, whose client is Sellby, our job is to use PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next,  use PySpark to determine if there is any bias toward favorable reviews from Vine members in your dataset and write a summary of the analysis to submit to the SellBy stakeholders.

## Resources:
Google Colab Notebook, Pyspark 3.0.3, Amazon AWS RDS-Postgresql

## Results: 
#### Perform ETL on Amazon Product Reviews
The coding for the ETL as well as analysis can be found on [Amazon_Reviews_ETL.ipynb](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/Amazon_Reviews_ETL.ipynb) and the schema for the sql tables can be found in [challenge_schema.sql](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/challenge_schema.sql)

* Install spark and Java and start a Spark session
![install_spark](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/install_spark.png?raw=True)

* Download postgres driver
![postgres](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/postgres.png?raw=True)

* Start an app session and create app name
![app_name](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/app_name.png?raw=True)

* Load amazon data into Spark Data frame.
![load_data](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/load_data.png?raw=True)

* Clean the data
![clean_df](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/clean_df.png?raw=True)

* Create cutomers_df Dataframe.
![cutomers_df](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/customers_df.png?raw=True)


* Create products_df Dataframe.
![products_df](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/products_df.png?raw=True)


* Create review_id_df Dataframe.
![review_id_df](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/review_id_df.png?raw=True)


* Create vine_df Dataframe.
![vine_df](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/vine_df.png?raw=True)

* All four DataFrames are loaded into their respective tables in pgAdmin.
![aws_rds](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/aws_rds.png?raw=True)

* The data in the tables can be viewed using select query 

![customers_table](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/customers_table.png?raw=True)

![products_table](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/products_table.png?raw=True)

![review_id_table](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/review_id_table.png?raw=True)

![vine_table](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/vine_table.png?raw=True)

#### Determine Bias of Vine Reviews
 The coding for vine_df analysis to determine bias can be found in [Vine_Review_Analysis](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/Vine_Review_Analysis.ipynb)
* Recreate the vine_df from Amazon_Reviews_ETL
![vine_df](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/vine_df.png?raw=True)
* The data is filtered to create a total_votes_df DataFrame where there are 20 or more total votes
![total_votes_df](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/total_votes_df.png?raw=True)

* The data is filtered to create a helpful_votes_df DataFrame where percentage of helpful_votes is equal to or greater than 50%

![helpful_votes_df](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/helpful_votes_df.png?raw=True)

* The data is filtered to create a paid_df DataFrame  where there is a Vine review(vine == 'Y')
![paid_df](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/paid_df.png?raw=True)

* The data is filtered to create an unpaid_df DataFrame  where there isn't a Vine review or unpaid review(vine == 'N')

![unpaid](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/unpaid_df.png?raw=True)

* The total number of reviews, the number of 5-star reviews, and the percentage 5-star reviews are calculated for all Vine reviews.

![vine](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/vine.png?raw=True)

* The total number of reviews, the number of 5-star reviews, and the percentage 5-star reviews are calculated for all non-Vine reviews.

![non_vine](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/non_vine.png?raw=True)


## Summary: 
After performing the analysis on the vine_df for both the paid that is Vine members review as well as the unpaid that is non-Vine reviews the following can be inferred:
1. The Number of paid reviews is very less 607 compared to unpaid reviews that i.e. 50522. So, paid reviews form a very small percentage of the total reviews i.e. 607/51129 * 100 =1.18 % 
2. The number of 5-star reviews for Vine members is only 257. So, the percentage 5-star reviews is 42.34 %
but for non-Vine or unpaid reviews, number of 5-star reviews is 25220. So, the percentage 5-star reviews is on49.92 %, which is higher than that of Vine members or paid members.

So, there doesn't seem to be a positive bias for reviews made by Vine members for this particular product. In fact, in seems like the paid reviewers take their job quiet seriously and review the product critically. As can be seen below by the ratio of 5-star review to non 5-star review for both Vine and non-Vine members.

![additonal](https://github.com/sucharita1/Amazon_Vine_Analysis/blob/657278ba77419eb2549cc3fda5318dc77cc4583c/images/additional.png?raw=True)

We also need to keep in mind out of the thousands of products available to review only Camera related products have been reviewed in this case and unless many more random products are analysed in the similar manner and similar results are achieved we cannot ensure that a positive bias truly doesn't exists.
