---
ID: 2382
post_title: NodeJs MySQL API Sample
author: snippet java
post_date: 2016-11-04 10:00:48
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/student-sample/mysql/nodejs-mysql-api-sample/
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
This is an example MySQL API enabled application that can be deployed into Bluemix with only a couple clicks. Try it out for yourself right now by clicking:   
[![Deploy to Bluemix][1]][2] </br> 
**How does this work?**

When you click the button, you are taken to Bluemix where you get a pick a name for your application at which point the platform takes over, grabs the code from this repository and gets it deployed. </br> It will automatically create an instance of the ClearDB service, call it sample-cleardb and bind it to your app. This is where your app will store its data. If you deploy multiple instances of app from this repository, they will share the same ClearDB instance. 

**Create, Read, Update, Delete (CRUD)**

This repository includes examples on the CRUD operations as APIs. It support GET request. You should be able to create database, create row, list all rows, read single row, update single row, delete single row, and delete database using the APIs.   
If you want to change the name of the ClearDB instance that gets created, the memory allocated to the application or other deploy-time options, have a look in \`manifest.yml\` and \`.bluemix/pipeline.yml\`.   
The method used in \`.bluemix/pipeline.yml\` will create an actual pipeline in DevOps. Where else the method used in the \`manifest.yml\` is a previous way to create a service.  [playground edit_mode="yes" show_deploy="yes" repo="nodejs-mysql-api-example" filename="manifest.yml" height="210"][/playground] [playground edit_mode="yes" repo="nodejs-mysql-api-example" filename=".bluemix/pipeline.yml" height="210"][/playground] 

Below are the files for CRUD Operations

1.  Create Table [playground edit_mode="yes" repo="nodejs-mysql-api-example" filename="lib/mysql/createTable.js" height="210"][/playground] 
2.  Create data [playground edit_mode="yes" repo="nodejs-mysql-api-example" filename="lib/mysql/create.js" height="210"][/playground] 
3.  List all data [playground edit_mode="yes" repo="nodejs-mysql-api-example" filename="lib/mysql/list.js" height="210"][/playground] 
4.  Retrieve data by specific ID [playground edit_mode="yes" repo="nodejs-mysql-api-example" filename="lib/mysql/read.js" height="210"][/playground] 
5.  Update data by specific ID and updated value [playground edit_mode="yes" repo="nodejs-mysql-api-example" filename="lib/mysql/update.js" height="210"][/playground] 
6.  Delete data [playground edit_mode="yes" repo="nodejs-mysql-api-example" filename="lib/mysql/delete.js" height="210"][/playground] 
7.  Delete Table [playground edit_mode="yes" repo="nodejs-mysql-api-example" filename="lib/mysql/deleteTable.js" height="210"][/playground] 

To configure the connection to MySQL service
[playground edit_mode="yes" repo="nodejs-mysql-api-example" filename="app.js" height="210"][/playground]

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/nodejs-mysql-api-example