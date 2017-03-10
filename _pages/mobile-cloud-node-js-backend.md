---
ID: 2392
post_title: 'Mobile Cloud &#8211; Node.js Backend'
author: snippet java
post_date: 2016-11-04 15:22:28
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/mobile-cloud-node-js-backend/
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
# Node.js backend application for mobile cloud

## Overview This Node.js application acts as a REST API for an Android app. Android app consists of simple login page and it communicates with this Node.js application using REST calls to validate the credentials. 

<img src="https://bluecloudnews.com/wp-content/uploads/2016/11/overview.png" alt="overview" width="975" height="459" class="alignleft size-full wp-image-2574" /> [su_divider] 
### REST API process overview

1.  Actual credentials are stored in the application environment variables
2.  When user try to login though android application an REST call is made to the endpoint `/checklogin` though a POST request. This request holds the credentials passed provided on the screen
3.  Then REST endpoint /checklogin is defined in the backend application. Response is sent after checking the provided credentials with the actual credentials
4.  If the provided credentials matches the actuals one then the success reponse is sent. Else failure response is sent.

<img src="https://bluecloudnews.com/wp-content/uploads/2016/11/rest_api_nodejs.png" alt="rest_api_nodejs" width="1001" height="683" class="alignleft size-full wp-image-2593" /> [![Deploy to Bluemix][1] ][2] [su_divider] 
## Code Explanation: 

### Code overview:  This application uses a express.js to create an endpoint for 

`/checklogin`. In particular , as the user provided credentials are sent using a POST type of http request , the main logic to validate is writte in the method `doPost(..)`. The credentials are sent in JSON format from the client. 
### Application Structure (Edit, Save and Deploy your own version): 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/11/nodejsFolderStrcture.png" alt="nodejsfolderstrcture" width="162" height="138" class="alignleft size-full wp-image-2337" /> **app.js:** Entry point of the application. </br> **api.js:** To describe the routes.</br> **manifest.yml:** Deployment settings.</br> **package.json:** The packages that application is dependent upon</br></br></br></br></br></br> [su_divider] 
#### app.js

`app.js` is the entry point of the application. It get the dependencies like express,body-parser and load's `api.js` which contains the routes. [playground edit_mode="yes" show_deploy="yes" repo="mobile_cloud_nodejs_backend" filename="app.js" height="170"] 
#### api.js

`api.js` is the main file that consists logic for route `/checkLogin`. Express.js is used to define routes. [playground edit_mode="yes" repo="mobile_cloud_nodejs_backend" filename="api.js" height="850"] 
1.  `appRouter` is defined as a function which includes method for POST and GET on endpoint `/checkLogin` 
2.  The `/checklogin` URI GET invocation will trigger `app.get(“/checklogin”,…) `method. This method writes the user friendly string to the response 
3.  The `/checklogin` URI POST invocation will trigger `app.post(“/checklogin”)` method. This method does the following actions: 
*   Parses the JSON data passed in the request. `user_name` and `user_password` parameters are passed through POST request. These parameters are retrieved from body by `req.body.user_nam`e and `req.body_password`. These values are stored in the variables `provided_user_name` and `provided_user_password` 
*   The actual user name and password to be checked against are stored as the environment variables. Thes``e environment variables are mentioned in` manifest.yml` file. `process.env.APP_USER_NA`ME and `process.env.APP_USER_PASSWORD` are used to retrieve the values. These values are stored in `actual_user_name` and `actual_user_password` 
*   If user does not provide `user_name` or `user_password` , then the response is [code language="javascript"]{"result":"error", "description" : "Credential missing" }[/code] 
*   If the user provided credentials does not match the actual credentials retrieved from environment variables ,then the response is [code language="javascript"]{"result":"error", "description" : "Incorrect credentials" }[/code] 
*   If the user provided credentials match the actual credentials retrieved from environment variables ,then the response is [code language="javascript"]{"result":"success","record":"You are outstanding"}[/code]  [su_divider] 

#### manifest.yml [playground edit_mode="yes" repo= "mobile_cloud_nodejs_backend" filename="manifest.yml" height="200"] Some of the important values in manifest.file are 

1.  `command: node app.js`. Specifies the entry path of the application
2.  env variables `APP_USER_NAME,APP_USER_PASSWORD` to provide the environment variables for the node.js application  Note that build pack is not mentioned in the manifest.yml file. Bluemix automatically detects the type and executes the app on Node.js server. 

#### package.json [playground edit_mode="yes" repo= "mobile_cloud_nodejs_backend" filename="package.json" height="200"]

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/mobile_cloud_nodejs_backend