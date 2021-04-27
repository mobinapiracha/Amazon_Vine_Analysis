# Amazon Vine Analysis

## Overview 

In this analysis we will examine the Amazon vine program: a paid service that allows manufacturers and publishers to receive reviews for their products. We will analyze the dataset for Video Games reviews. We will perform the ETL process where we extract the data from the url, which is an S3 bucket, we will then transform the data by creating four different tables. The first table is customer data, where we have customer_id and customer_count, to count the number of times a customer has reviewed a video game. Second table is products table which is the product_id and product_title. Third table is the review_id table which shows review_id, customer_id, product_id, product_parent, review_date. Fourth and final table is the vine table which shows review_id, star_rating, helpful_votes, total_votes, vine and verified_purchase. We will load this data into pgadmin by making a connection to Amazon Relational Database Service (RDS) and load the data into the correct tables which we have already created using a schema. In order to determine if there is bias in reviews written by Vine Reviewers, we filter data with greater than 20 votes, and for those observations we create a new column, helpful votes as a fraction of total votes which is greater than 50%. Within than data we divide our data into vine(paid) and non-vine(unpaid) reviewers. For each of these two dataframes we count the number of reviewers, the number of 5-star reviews and the percentage of 5-star reviews. We compare 5-star reviews for vine vs non-vine users to see if there is a bias towards reviews that were written as a part of the vine program. 

## Results

* Count of total paid reviews is 94 while count of total unpaid reviews is 40471
* Total number of paid 5-star reviews is 48 while total number of unpaid 5-star reviews is 15663
* 51.06% of paid reviews are 5-star while only 38.70% of unpaid reviews are 5-star

## Summary 

From the results, there is some evidence that there is a bias in vine reviews to non-vine reviews. 51.06% vine 5-star reviews compared to 38.70% vine 5-star reviews is a significant roughly 13% difference. However, we also notice that total number of vine reviews are only 94 while total non-vine reviews are 40471 so this difference could just be due to chance as there are in total a lot more non-vine reviews than vine reviews. Its often common than when the number of reviews become very large, the number of 5-star reviews as a percentage of total reviews does decrease. Even though there is some evidence of bias, the fact that there are so few vine reviews to non-vine reviews makes the comparison difficult. Another analysis we can do to give us a better idea is to calcuate the average rating for vine and non-vine reviewers and see if the difference is significant. We can also find the rating for each star rating (1,2,3,4,5) for both vine and non-vine reviewers as a proportion of total reviews and compare the difference. 
