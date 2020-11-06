# Demo Group5 Hive Vs Impala

## Team Members - Group-5

### Name: Sushmita Rudra

GitHub profile: [Sushmita-Rudra](https://github.com/Sushmita-Rudra)

<img src="./IMG_2139.jpg" width="250"/>

Subtopics:
1. Load data from local to table using Hive.
1. Perform HiveQL queries for data retrieval and insertion of data manually.

#### Pre-requisites:
     - 
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
   - Create file named 'Demo.txt' on your local(I have created it on my desktop).
   - Once the file is created update the file with content as per your requirement delimeted with special symbol.
     Example: ``` S537360,Manisha,ComputerScience,NorthwestMissouriStateUniversity. ```
   - Once the file with data is ready, lets move the file from local file system to HDFS.
     - open the terminal window by clicking on the small black screen located at the middle on the cloudera welcome screen.
     - When the terminal is open you are prompted with the host name followed with "$" symbol.
     - Now follow the below commands.
     - To know about the current directory type the command ```pwd```.
     - To list all the files present in the director ```ls```.
     - Using ```cd ``` command move to the directory where data file is created.
     - Once you are in correct directory (check with pwd command) type ``` ls ``` which will list all the available files(Check for the data file ie Demo.txt)
     - ``` scp filename root@ip-address: ``` this will prompt with password enter the cloudera password.(file name - Demo.txt)
     - ip address of the vm can be know by typing the command ``` ifconfig ``` inet address from the result is the ipaddress.
     - To check the file content give the command ``` cat file-name ```.This is display all the data present in the file.
     - To put the file in to HDFS ``` hadoop fs -put Demo / user/cloudera ```
     - file is now in HDFS.
     
     
   
   
###### 2.Use the loaded Data in hive tables.

### Name: Shravani Jaidi 

GitHub profile: [Sravani Jaidi](https://github.com/Sravani537520)

<img src="./Shrvni.jpeg" width="250">

### subtopic
##### Interacting with Hive and Impala
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
- https://stackoverflow.com/questions/20500221/impala-cant-access-all-hive-table
- https://docs.cloudera.com/machine-learning/1.0/import-data/topics/ml-loading-csv-data-into-an-impala-table.html
- https://informationit27.medium.com/hive-and-impala-for-managing-structured-data-3ff020a3fbff
- https://medium.com/@mmas/loading-data-into-hive-6f9d9b8d0b8f
- http://www.javachain.com/load-data-into-hive-table-from-hdfs/

