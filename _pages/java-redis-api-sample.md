---
ID: 2474
post_title: Java Redis API Sample
author: snippet java
post_date: 2016-11-09 03:52:17
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/student-sample/redis/java-redis-api-sample/
published: true
inkblot_avatar:
  - "0"
inkblot_webcomic_group:
  - ""
inkblot_webcomic_image:
  - ""
inkblot_webcomic_order:
  - ""
inkblot_webcomic_comments:
  - ""
inkblot_webcomic_term_image:
  - ""
---
This is an example Redis API enabled application that can be deployed into Bluemix with only a couple clicks. Try it out for yourself right now by clicking:   
[![Deploy to Bluemix][1]][2] </br> 
**How does this work?**

When you click the button, you are taken to Bluemix where you get a pick a name for your application at which point the platform takes over, grabs the code from this repository and gets it deployed. </br> It will automatically create an instance of the Rediscloud service, call it sample-rediscloud and bind it to your app. This is where your app will store its data. If you deploy multiple instances of app from this repository, they will share the same Rediscloud instance. 

**Create, Read, Update, Delete (CRUD)**

This repository includes examples on the CRUD operations as APIs. It support GET request. You should be able to set, get, and del using the APIs.   
If you want to change the name of the Rediscloud instance that gets created, the memory allocated to the application or other deploy-time options, have a look in \`manifest.yml\` and \`.bluemix/pipeline.yml\`.   
The method used in \`.bluemix/pipeline.yml\` will create an actual pipeline in DevOps. Where else the method used in the \`manifest.yml\` is a previous way to create a service.  [playground edit_mode="yes" show_deploy="yes" repo="java-redis-api-example" filename="manifest.yml" height="210"][/playground] [playground edit_mode="yes" repo="java-redis-api-example" filename=".bluemix/pipeline.yml" height="210"][/playground] 

Below are the files for CRUD Operations

1.  Create/Update by Set Key and Value [playground edit_mode="yes" repo="java-redis-api-example" filename="src/main/java/com/ibm/sample/student/redis/Set.java" height="210"][/playground] 
2.  Create/Update by Set Key with hashed Field and Value [playground edit_mode="yes" repo="java-redis-api-example" filename="src/main/java/com/ibm/sample/student/redis/HSet.java" height="210"][/playground] 
3.  List all keys [playground edit_mode="yes" repo="java-redis-api-example" filename="src/main/java/com/ibm/sample/student/redis/Keys.java" height="210"][/playground] 
4.  Get Value by specific Key [playground edit_mode="yes" repo="java-redis-api-example" filename="src/main/java/com/ibm/sample/student/redis/Get.java" height="210"][/playground] 
5.  Get all Hashed Field and Value by specific Key or Get Value by Specific Key and Hashed Field [playground edit_mode="yes" repo="java-redis-api-example" filename="src/main/java/com/ibm/sample/student/redis/HGet.java" height="210"][/playground] 
6.  Delete by specific Key [playground edit_mode="yes" repo="java-redis-api-example" filename="src/main/java/com/ibm/sample/student/redis/Delete.java" height="210"][/playground] 
7.  Delete all data [playground edit_mode="yes" repo="java-redis-api-example" filename="src/main/java/com/ibm/sample/student/redis/FlushDB.java" height="210"][/playground] 

To configure the connection to Rediscloud service
[playground edit_mode="yes" repo="java-redis-api-example" filename="src/main/java/com/ibm/sample/student/redis/RedisConnectionService.java" height="210"][/playground]

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/java-redis-api-example