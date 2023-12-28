# Hive

### run `jps` and check if hadoop services are active. If NOT active, then only run:
stop-all.sh  
hadoop namenode -format  
start-all.sh  

### Create Hive directories in HDFS (ONE TIME only)
hdfs dfs -mkdir /tmp  
hdfs dfs -chmod g+w /tmp  
hdfs dfs -mkdir -p /user/hive/warehouse  
hdfs dfs -chmod g+w /user/hive/warehouse  

### Initialize Derby and hive (ONE TIME only)
schematool -initSchema -dbType derby  

### To start Hive
hive  


## Full Hive Configuration 
#Hive Installation  
wget https://downloads.apache.org/hive/hive-3.1.2/apache-hive-3.1.2-bin.tar.gz  
tar xzf apache-hive-3.1.2-bin.tar.gz  
rm apache-hive-3.1.2-bin.tar.gz  
sudo mv apache-hive-3.1.2-bin/ /opt/hive  


#Set up Hive profile(when doing manually)  
#instead of changing at .bashrc we create script under profile.d  
sudo tee /etc/profile.d/hive.sh <<'EOF'    
export HIVE_HOME=/opt/hive  
export PATH=$PATH:$HIVE_HOME/bin  
EOF  

#Set up Hive profile(for script we  need like below)  
#cat >/etc/profile.d/hive.sh <<'EOF'  
#export HIVE_HOME=/opt/hive  
#export PATH=$PATH:$HIVE_HOME/bin  
#EOF  

#Edit hive-config.sh file  
echo "export HADOOP_HOME=/usr/local/hadoop" >> $HIVE_HOME/bin/hive-config.sh  

#Fixing guava problem:  
rm $HIVE_HOME/lib/guava-19.0.jar  
cp $HADOOP_HOME/share/hadoop/hdfs/lib/guava-27.0-jre.jar $HIVE_HOME/lib/  

#run jps and check if hadoop services are active. If NOT active, then only run:  
stop-all.sh  
hadoop namenode -format  
start-all.sh  

#Create Hive directories in HDFS (ONE TIME only)  
hdfs dfs -mkdir /tmp  
hdfs dfs -chmod g+w /tmp  
hdfs dfs -mkdir -p /user/hive/warehouse  
hdfs dfs -chmod g+w /user/hive/warehouse  

#Initialize Derby and hive (ONE TIME only)  
schematool -initSchema -dbType derby  



## Check HDFS on browser
http://localhost:9870/

# Question
![HW4-Hive](https://github.com/saadesh71/Hive/assets/43541169/7964196a-b8c3-4fdc-9419-9f96147522f8)


Dataset: [Drive Link](https://nam02.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdrive.google.com%2Ffile%2Fd%2F1RA5B6SXSFMmL_908W8Tmqz6BWH3E2ANC%2Fview%3Fusp%3Dshare_link&data=05%7C01%7Cecmhzg%40mst.edu%7C319a06c3da6e4fd5d12e08dbd26096cc%7Ce3fefdbef7e9401ba51a355e01b05a89%7C0%7C0%7C638335084520843293%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=MlKIutzj2JZgQ61oj%2FWsF7LOKTutnUkj60VNoxnT1%2BA%3D&reserved=0)

Steps - Insert dataset to HDFS before executing the code use hadoop fs -mkdir, copyFromLocal
          
Part 1:
- Download the dataset and insert it into a table named 'GameTable'. Based on
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
