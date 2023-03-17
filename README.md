# **Real World Project**  
### This Project is done on Ubuntu 20.04 LTS

This Docker image runs the latest 2.4 version of MariaDB MaxScale.

-	[Travis CI:  
	![build status badge](https://img.shields.io/travis/mariadb-corporation/maxscale-docker/master.svg)](https://travis-ci.org/mariadb-corporation/maxscale-docker/branches)

## **The initial prerequisites are to install:**
   - Docker
   - Docker-compose
   - MariaDB

## **To install Docker:**
       sudo apt update
       sudo apt install apt-transport-https ca-certificates curl software-properties-                    
       common curl -fsSL) (https://download.docker.com/linux/ubuntu/gpg) |      
       sudo apt-key add – 
       sudo add-apt-repository “deb [arch=amd64]   
       (https://download.docker.com/linux/ubuntu) bionic stable"
       sudo apt update
       sudo apt install docker-ce 

### The next command is to verify the Docker status:
         sudo systemctl status docker
### **To install Docker Compose:**
        sudo apt install docker-compose
### **To install MariaDB:**
       sudo apt install mariadb-client
### Next is to start cloning maxscale-docker repository by running the following command in Ubuntu terminal:       
     [git clone] (https://github.com/gdltosea/maxscale-docker)
### Next is to navigate to maxscale-docker/maxscale/ directory by running the following command:  
     cd maxscale-docker/maxscale/
     To make sure you bring the containers up type the next command:
     docker-compose up -d 
### Now you should have created 3 containers and, the cluster is configured to utilize automatic failover.        
        In this case when you stop the master container 
        you can see that one of the slaves becomes the master when the master goes    
        down. As shown in the following picture:  

![image](https://user-images.githubusercontent.com/105324256/225800147-c860975f-97a1-485f-b0cb-4b21573354fb.png)



 

### Now you can run the next command to make sure your servers are up and running: 
       docker-compose exec maxscale maxctrl list servers
       You should see the following output:  

![image](https://user-images.githubusercontent.com/105324256/225800214-3f6b794b-6e98-4bb4-91fb-8533da54f024.png)


 

Run this command to connect to mariadb using the username: maxuser, maxpwd as a password and that will be on the port 4000:
mariadb -umaxuser -pmaxpwd -h 192.168.0.18 -P 4000
**It will give you the next output:**
Welcome to the MariaDB monitor.  Commands end with; or \g.
Your MariaDB connection id is 1
Server version: 10.5.8-MariaDB-1:10.5.8+maria~focal-log mariadb.org binary distribution
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
MariaDB [(none)]>

### Next type this command to check that zipcodes_one and zipcodes_two are in the database:      
   MariaDB [(none)]> show databases;
   You’ll be able to see the next output:  

![image](https://user-images.githubusercontent.com/105324256/225800289-32476b6a-3ae7-4edc-9c4e-2cf19236f7be.png)


 

### Now we are about to execute SQL queries:
     Use the following command:
     SELECT * FROM zipcodes_one.zipcodes_one LIMIT 9990,10;
     to query the last 10 rows of zipcodes_one

The last 10 rows of zipcodes_one are:
(40843, 'STANDARD', 'HOLMES MILL', 'KY', 'PRIMARY', '36.86', '-83', 'NA-US-KY-HOLMES MILL', 'FALSE', '', '', '')
(41425, 'STANDARD', 'EZEL', 'KY', 'PRIMARY', '37.89', '-83.44', 'NA-US-KY-EZEL', 'FALSE', '390', '801', '10204009')
(40118, 'STANDARD', 'FAIRDALE', 'KY', 'PRIMARY', '38.11', '-85.75', 'NA-US-KY-FAIRDALE', 'FALSE', '4398', '7635', '122449930')
(40020, 'PO BOX', 'FAIRFIELD', 'KY', 'PRIMARY', '37.93', '-85.38', 'NA-US-KY-FAIRFIELD', 'FALSE', '', '', '')
(42221, 'PO BOX', 'FAIRVIEW', 'KY', 'PRIMARY', '36.84', '-87.31', 'NA-US-KY-FAIRVIEW', 'FALSE', '', '', '')
(41426, 'PO BOX', 'FALCON', 'KY', 'PRIMARY', '37.78', '-83', 'NA-US-KY-FALCON', 'FALSE', '', '', '')
(40932, 'PO BOX', 'FALL ROCK', 'KY', 'PRIMARY', '37.22', '-83.78', 'NA-US-KY-FALL ROCK', 'FALSE', '', '', '')
(40119, 'STANDARD', 'FALLS OF ROUGH', 'KY', 'PRIMARY', '37.6', '-86.55', 'NA-US-KY-FALLS OF ROUGH', 'FALSE', '760', '1468', '20771670')
(42039, 'STANDARD', 'FANCY FARM', 'KY', 'PRIMARY', '36.75', '-88.79', 'NA-US-KY-FANCY FARM', 'FALSE', '696', '1317', '20643485')
(40319, 'PO BOX', 'FARMERS', 'KY', 'PRIMARY', '38.14', '-83.54', 'NA-US-KY-FARMERS', 'FALSE', '', '', '')

Use the following command:
SELECT * FROM zipcodes_two.zipcodes_two LIMIT 10;
To query the first 10 rows of zipcodes_two

The first 10 rows of zipcodes_two of zipcodes_two are:
(42040, 'STANDARD', 'FARMINGTON', 'KY', 'PRIMARY', '36.67', '-88.53', 'NA-US-KY-FARMINGTON', 'FALSE', '465', '896', '11562973')
(41524, 'STANDARD', 'FEDSCREEK', 'KY', 'PRIMARY', '37.4', '-82.24', 'NA-US-KY-FEDSCREEK', 'FALSE', '', '', '')
(42533, 'STANDARD', 'FERGUSON', 'KY', 'PRIMARY', '37.06', '-84.59', 'NA-US-KY-FERGUSON', 'FALSE', '429', '761', '9555412')
(40022, 'STANDARD', 'FINCHVILLE', 'KY', 'PRIMARY', '38.15', '-85.31', 'NA-US-KY-FINCHVILLE', 'FALSE', '437', '839', '19909942')
(40023, 'STANDARD', 'FISHERVILLE', 'KY', 'PRIMARY', '38.16', '-85.42', 'NA-US-KY-FISHERVILLE', 'FALSE', '1884', '3733', '113020684')
(41743, 'PO BOX', 'FISTY', 'KY', 'PRIMARY', '37.33', '-83.1', 'NA-US-KY-FISTY', 'FALSE', '', '', '')
(41219, 'STANDARD', 'FLATGAP', 'KY', 'PRIMARY', '37.93', '-82.88', 'NA-US-KY-FLATGAP', 'FALSE', '708', '1397', '20395667')
(40935, 'STANDARD', 'FLAT LICK', 'KY', 'PRIMARY', '36.82', '-83.76', 'NA-US-KY-FLAT LICK', 'FALSE', '752', '1477', '14267237')
(40997, 'STANDARD', 'WALKER', 'KY', 'PRIMARY', '36.88', '-83.71', 'NA-US-KY-WALKER', 'FALSE', '', '', '')
(41139, 'STANDARD', 'FLATWOODS', 'KY', 'PRIMARY', '38.51', '-82.72', 'NA-US-KY-FLATWOODS', 'FALSE', '3692', '6748', '121902277')

Use this command:
SELECT Zipcode FROM zipcodes_one.zipcodes_one ORDER BY Zipcode DESC LIMIT 1;  To view the largest zipcode number in zipcodes_one
The largest zipcode number in zipcodes_one is:
(47750,)

Use the following command:
SELECT Zipcode FROM zipcodes_two.zipcodes_two ORDER BY Zipcode ASC LIMIT 1;  To view the smallest zipcode number in zipcodes_two
The smallest zipcode number in zipcodes_two is:
(38257,)

    Once complete, to remove the cluster and maxscale containers:
    docker-compose down -v


Juan Flores  

jfloreshernandez@student.rtc.edu  

03/16/2023  

CNE370  

This code will print:  

The last 10 rows of zipcodes_one  

The first 10 rows of zipcodes_two  

The largest zipcode in zipcodes_one  

The smallest zipcode in zipcodes_two

import pymysql
db = pymysql.connect(host="192.168.0.18", port=4000, user="maxuser", passwd="maxpwd")
cursor = db.cursor()  

print('The last 10 rows of zipcodes_one are:')
cursor = db.cursor()
cursor.execute("SELECT * FROM zipcodes_one.zipcodes_one LIMIT 9990,10;")
results = cursor.fetchall()
for result in results:
    print(result)  
    
print('The first 10 rows of zipcodes_two are:')
cursor = db.cursor()
cursor.execute("SELECT * FROM zipcodes_two.zipcodes_two LIMIT 10;")
results = cursor.fetchall()
for result in results:
    print(result)  
    
print('The largest zipcode number in zipcodes_one is:')
cursor = db.cursor()
cursor.execute("SELECT Zipcode FROM zipcodes_one.zipcodes_one ORDER BY Zipcode DESC LIMIT 1;")
results = cursor.fetchall()
for result in results:
    print(result)

print('The smallest zipcode number in zipcodes_two is:')
cursor = db.cursor()
cursor.execute("SELECT Zipcode FROM zipcodes_two.zipcodes_two ORDER BY Zipcode ASC LIMIT 1")
results = cursor.fetchall()
for result in results:
    print(result)


Sources:

https://severalnines.com/blog/mariadb-maxscale-load-balancing-docker-deployment-part-one/

https://mariadb.com/kb/en/mariadb-maxscale-2208-mariadb-maxscale-configuration-guide/

I also want to especially thank Abdirizak Kulmiye for helping me with this assignment.



