---
ID: 2532
post_title: NodeJS Cloudant GeoJson API Sample
author: snippet java
post_date: 2016-11-11 10:13:11
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/student-sample/cloudant-geojson/nodejs-cloudant-geojson-api-sample/
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
This is an example Cloudant API enabled application that can be deployed into Bluemix with only a couple clicks. Try it out for yourself right now by clicking:   
[![Deploy to Bluemix][1]][2] </br> 
**How does this work?**

When you click the button, you are taken to Bluemix where you get a pick a name for your application at which point the platform takes over, grabs the code from this repository and gets it deployed. </br> It will automatically create an instance of the Cloudant service, call it sample-cloudantNoSQLDB and bind it to your app. This is where your app will store its data. If you deploy multiple instances of app from this repository, they will share the same Cloudant instance. </br> During success deployment, browse to http://HOSTNAME.mybluemix.net, and you should see something similar as below: </br> <img src="http://bluecloudnews.com/wp-content/uploads/2016/11/geojson.jpg" alt="geojson" class="alignnone size-full" /> 

**Using Google Map API**

To properly use Google Map, you will have to include the API key on the script included in the index.html </br> [playground edit_mode="yes" show_deploy="yes" repo="nodejs-cloudant-form-geojson-example" filename="public/index.html" height="210"][/playground] **API_KEY** needs to be obtained from Google. For more info, please refer to the following link: [Google API Key][3] 

**Create, Read, Update, Delete (CRUD)**

This repository includes examples on the CRUD operations as APIs. It support both GET and POST requests. You should be able to create database, create row, list all rows, read single row, update single row, delete single row, and delete database using the APIs.   
If you want to change the name of the Cloudant instance that gets created, the memory allocated to the application or other deploy-time options, have a look in \`manifest.yml\` and \`.bluemix/pipeline.yml\`.   
The method used in \`.bluemix/pipeline.yml\` will create an actual pipeline in DevOps. Where else the method used in the \`manifest.yml\` is a previous way to create a service.  [playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename="manifest.yml" height="210"][/playground] [playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename=".bluemix/pipeline.yml" height="210"][/playground] 

Below are the files for CRUD Operations

1.  Create Database [playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename="lib/cloudant/createDb.js" height="210"][/playground] 
2.  Create data [playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename="lib/cloudant/set.js" height="210"][/playground] 
3.  List all data [playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename="lib/cloudant/list.js" height="210"][/playground] 
4.  Retrieve data by specific ID [playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename="lib/cloudant/get.js" height="210"][/playground] 
5.  Update data by specific ID and updated value [playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename="lib/cloudant/update.js" height="210"][/playground] 
6.  Delete data [playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename="lib/cloudant/destroy.js" height="210"][/playground] 
7.  Delete Database [playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename="lib/cloudant/destroyDb.js" height="210"][/playground] 

To configure the connection to Cloudant
[playground edit_mode="yes" repo="nodejs-cloudant-form-geojson-example" filename="app.js" height="210"][/playground]

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/nodejs-cloudant-api-example
 [3]: https://developers.google.com/maps/documentation/javascript/get-api-key