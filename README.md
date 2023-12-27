# Hive

Dataset - https://nam02.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdrive.google.com%2Ffile%2Fd%2F1RA5B6SXSFMmL_908W8Tmqz6BWH3E2ANC%2Fview%3Fusp%3Dshare_link&data=05%7C01%7Cecmhzg%40mst.edu%7C319a06c3da6e4fd5d12e08dbd26096cc%7Ce3fefdbef7e9401ba51a355e01b05a89%7C0%7C0%7C638335084520843293%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=MlKIutzj2JZgQ61oj%2FWsF7LOKTutnUkj60VNoxnT1%2BA%3D&reserved=0

Steps - Insert dataset to hdfs before executing the code use hadoop fs -mkdir, copyFromLocal
          
Part 1:
- Download the dataset and insert into a table named 'GameTable'. Based on
the data, design the fields of your table with appropriate data types.
-  For each ‘marketplace’ & ‘product category’, find the total number of
‘review_id’ & average ‘star_rating’ where ‘marketplace’ does not include ‘US’.

Part 2:
- Create a table 'GameTablePart' that supports partitioning on 'star_rating' field.
Fill up data for partitions 'star_rating=1' and 'star_rating=2' from the
'GameTable'.
- For each ‘star_rating’ from 'GameTablePart' table, find sum of ‘helpful_votes’
and sum of ‘total_votes’ ordered by sum of 'total_votes' descending.

Part 3: 
- Create a table 'GameTableBuck' that supports bucketing on 'review_date'
field. Consider 3 buckets. For each bucket, find the minimum and maximum
'review_date'.
- For each ‘product_id’, find the average ‘helpful_votes’ and average
‘total_votes’ where average 'helpful_votes' is greater than 1.
