# Demo Group5 Hive Vs Impala

## Team Members - Group-5

### Name: Sushmita Rudra

GitHub profile: [Sushmita-Rudra](https://github.com/Sushmita-Rudra)

<img src="./IMG_2139.jpg" width="250"/>

#### Subtopics:
1. Load local data file into table using Hive commands.
1. Perform HiveQL queries for data retrieval and insertion of data manually.

#### Prerequisites:
 -  Install [Oracle Virtual box](https://www.virtualbox.org/wiki/Downloads)
 -  Install and set up [Cloudera Virtual VM](https://www.cloudera.com/)

### Step-by-step process and commands:
#### 1. How to insert into a table manually:
  1. Open terminal in Cloudera VM and press ```hive```, which will open up the Hive CLI.
  1. Create a table 'user_details' inside the database by using the following command.
  
	  ```
     
	    create table if not exists user_details (
	       id int,
	       age int,
	       gender string,
	       profession string,
	       reviews int
	    );
      
	  ```
	
  1. Now, insert the data into that table using the below command.
 
	 ```
	   insert into table user_details values (1,24,'F',Doctor,234455);
      ```
This is how we can manually insert a row data inside a table using Hive command.
We can verify the  data insertion by typing in the below command
  ```
    select * from user_details; 
  ```

#### 2. How to load data from a local file into a table:
More often than not , we will have large data files that needs to be dumped into a table, we can achieve that by using Hive.
 1. Inside the terminal, create another table 'user_info' inside the database by using the following command.
  ```
   create table if not exists user_info (id int, profession string, age int, gender string, reviews int) row format delimited fields terminated by '|'
  lines terminated by '\n' stored as textfile ; 
  ```
 1. Have the data file which you want to load into the table saved in your local machine. In my case, my local data file is at location "/home/cloudera/Documents/u.user".
    "u.user" data file is added in the repo files.
    Use the  destination path of the local file in your machine in the below command to load the data into the table 'user_info'.
	
	```
	load data local inpath '/home/cloudera/Documents/u.user' into table user_info;
	```
	
1. Verify the successful loading of data by querying out the table.
	
	```select * from user_info; ```
     
  ### References:
  - https://data-flair.training/blogs/hive-dml-commands/
  - https://drive.google.com/file/d/1uJ3Vg-CNc-DPFxMrjnHSeigvvzrdlZDz/view
  - https://www.virtualbox.org/wiki/Downloads
  - https://www.youtube.com/watch?v=HP4g2BU7-xU&feature=youtu.be&ab_channel=Simplilearn
  - https://cwiki.apache.org/confluence/display/Hive/LanguageManual+DML
  - http://www.hadooplessons.info/2014/12/loading-data-into-hive-table.html
    
### Name: Manisha Mengani

GitHub profile: [Manisha-Mengani](https://github.com/Manisha-Mengani)

<img src="./mengani.jpeg" width="250"/>


### subtopics
#### To Load data From Local to HDFS create tables and update them using hive
##### Prerequisites:
  - Install cloudera virtual Machine into the local.[Cloudera](https://www.cloudera.com/)
  - Install oracle virtual box.[Virtual Box](https://www.virtualbox.org/)
      
##### Process and Commands:
###### 1. How to load data from Local to HDFS.
   - In the cloudera Virtual Machine follow below steps
   - Create file named 'sales_demo' in local
   - Once the file is created update the file with content as per your requirement delimeted with special symbol.
     Example:
     ```
     1-Anu-boxes-18
     
     ```
   - Once the file with data is ready, lets move the file from local file system to HDFS
   - To check the file content give the command ``` cat sales_demo ```.This is display all the data present in the file.
   - To put the file in to HDFS 
     ```   
     hadoop fs -cat  /user/cloudera/sales_demo 
   
     ```
   - file is now in HDFS.
   
###### 2.Use the loaded Data in hive tables
   - In the hive terminal 
      ```
      show databases
      
      ```
   - use database and create table.
     
   - To create table :
     create a table as per the data loaded in hdfs 
      ```
      create table sales_demo(id int, 
                       name string,
                       product string,
                       num_sales int)
                       row format delimited fields terminated by '-';
      ```
   - To load the data into the sales_demo table
      ```
      load data inpath '/user/cloudera/sales_demo' overwrite into table sales_demo;
      
      ```
   - View the content of the table
      ```
      select * from sales_demo;
     
     ```
###### References:
   - https://www.youtube.com/watch?v=8rsNXdvFqBc
   - https://www.virtualbox.org/wiki/Downloads
   - https://www.tutorialspoint.com/hive/index.htm
   - http://www.javachain.com/load-data-into-hive-table-from-hdfs/
   

### Name: Shravani Jaidi 

GitHub profile: [Sravani Jaidi](https://github.com/Sravani537520)

<img src="./Shrvni.jpeg" width="250">

### subtopic
##### Interacting with Hive and Impala

##### Prerequisites:
 -  Download and Install [Oracle Virtual box](https://www.virtualbox.org/wiki/Downloads)
 -  Download and Install [Cloudera Virtual VM](https://www.cloudera.com/)
 
 ##### Process and commands
 
Steps for creating and loading data using Impala
===================================================

- Craeted data file on the desktop inorder to load into hadoop.
- Open cloudera terminal and using impala-shell command logged into impala cli where I can execute commands.
- create database using `create database hive_impala` 
- verify database using `show databases`
- create table using `create table customer_orders (store String,category String,cost double,paymenttype String)ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS TEXTFILE; `
- Load data using `LOAD DATA LOCAL INPATH '/home/cloudera/Desktop/RawData.txt' OVERWRITE INTO TABLE customer_orders;` 
- The above command results analysisexception beacuse we cannot load data using impala, since it doesn't have any own metadata structure it will use hive-metatdata structure.
- Now let's load data by connecting to hive-cli, open new terminal and enter hive in terminal.
- Load the data using same command `LOAD DATA LOCAL INPATH '/home/cloudera/Desktop/RawData.txt' OVERWRITE INTO TABLE customer_orders;`
- Let's verify the data is loaded or not using some basic command.


### References

- https://docs.cloudera.com/documentation/enterprise/latest/topics/impala_create_table.html
- https://stackoverflow.com/questions/20500221/impala-cant-access-all-hive-table
- https://docs.cloudera.com/machine-learning/1.0/import-data/topics/ml-loading-csv-data-into-an-impala-table.html
- https://docs.cloudera.com/runtime/7.2.1/impala-sql-reference/topics/impala-load-data.html
- https://www.youtube.com/watch?v=HP4g2BU7-xU

### Name: Anil Bomma

GitHub profile: [Anil Bomma](https://github.com/anil-bomma)


<img src="./bomma.jpeg" width="250">

### subtopic:
 ## Implementation of aggregate queries using Impala and exploring web interface for impala and hive
 
 ### Prerequisites:
      - Install oracle virtual box.[Virtual Box](https://www.virtualbox.org/)
      - Install cloudera virtual Machine into the local.[Cloudera](https://www.cloudera.com/)
 
 ### TODO list:
 - Lets verify database, tables and data which is already loaded using impala shell
 - Let's calculate the maximum cost for each category using groupby clause on the loaded data 
 - `select category, max(cost) from customer_orders group by category;`
 - Let's try to execute the above command in both hive and impala and calculate the execution time using Hue.
 - As we all know Impala sit's directly on the hdfs whereas hive sit's on the hdfs -> map-reducer. So the execution will be faster using impala when compared to the hive.
 

### References:

- https://www.simplilearn.com/basics-of-hive-and-impala-tutorial
- https://informationit27.medium.com/hive-and-impala-for-managing-structured-data-3ff020a3fbff
- https://medium.com/@mmas/loading-data-into-hive-6f9d9b8d0b8f
- http://www.javachain.com/load-data-into-hive-table-from-hdfs/

