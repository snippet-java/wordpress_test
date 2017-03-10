---
ID: 2389
post_title: 'Mobile Cloud &#8211; Java Backend'
author: snippet java
post_date: 2016-11-04 15:21:46
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/mobile-cloud-java-backend/
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
# Java backend application for mobile cloud

## Overview This Java application acts as a REST API for an Android app. Android app consists of simple login page and it communicates with this Java application using REST calls to validate the credentials. 

<img src="https://bluecloudnews.com/wp-content/uploads/2016/11/overview.png" alt="overview" width="975" height="459" class="alignleft size-full wp-image-2574" /> [su_divider] 
### REST API process overview

1.  Actual credentials are stored in the application environment variables
2.  When user try to login though android application an REST call is made to the endpoint `/checklogin` though a POST request. This request holds the credentials passed provided on the screen
3.  Then REST endpoint /checklogin is defined in the backend application. Response is sent after checking the provided credentials with the actual credentials
4.  If the provided credentials matches the actuals one then the success reponse is sent. Else failure response is sent.

<img src="https://bluecloudnews.com/wp-content/uploads/2016/11/rest_api.png" alt="rest_api" width="972" height="685" class="alignleft size-full wp-image-2575" /> [![Deploy to Bluemix][1] ][2] [su_divider] 
## Code Explanation: 

### Code overview:  This application uses a Servlet to create an endpoint for 

`/checklogin`. In particular , as the user provided credentials are sent using a POST type of http request , the main logic to validate is writte in the method `doPost(..)`. The credentials are sent in JSON format from the client. GSON package is used to parse this JSON. Maven is used to get the GSON dependency and also to build a war file to be deployed. 
### Application Structure:  The servlet class in named 

`CheckLogin.java` and resides in the folder `src/main/java`. `manifest.yml` file is contains the deployment settings for bluemix. Environment variables mentioned earlier for actual credentails are provided as part of `manifest.yml` file. The contents of `CheckLogin.java` and manifest.yml are explained in detail below. </br></br> <img src="http://bluecloudnews.com/wp-content/uploads/2016/11/javaFolderStrcuture.png" alt="javafolderstrcuture" width="188" height="136" class="alignleft size-full wp-image-2342" /> **CheckLogin.java:** Java servlet for the route /checklogin</br> **manifest.yml:** Deployment settings</br> </br></br></br></br> [su_divider] 
#### CheckLogin.java

`CheckLogin `class inherits HttpServlet. The method` doGet(..)` and `doPost(..`) are defined. All the process to validate credentails is part of `doPost(..)`. The method `doGet(..)` is just to display the readable message when you try to preform a GET request to /checkLogin using a browser. [playground edit_mode="yes" show_deploy="yes" repo="mobile_cloud_j``ava_backend" filename="src/main/java/CheckLogin.java" height="1150"] 
1.  The `@WebServlet("/checklogin")` annotation is provided for the class `CheckLogin`. This annotations maps the endpoint `/checklogin` with this class 
2.  The `/checklogin` GET invocation will trigger `doGet(…)` method. This method just sends user-friendly message as response
3.  The `/checklogin` URI POST invocation will trigger `doPost(…)` method. This method does the following actions:
*   Parses the credentails sent in JSON format through the POST request. GSON library is used to parse the received JSON data and convert it to a Map httpRequestData.
*   The Map `httpRequestData` holds the provided credentials in the key's `provided_user_name` and `provided_user_password`
*   Actual credentials are retrieved from environment variables through the method `System.getenv("APP_USER_NAME")` and `System.getenv("APP_USER_PASSWORD")` and saved in the variables `actual_user_name` and `acutal_user_password`. Note that these actual credentails are part of `manifest.yml` file
*   if checks for three possible cases of credentials not entered, correct credentials are provided and the credentails provided are valid 
*   If user does not provide `user_name` or `user_password` , then the response is [code language="javascript"] {"result":"error", "description" : "Credential missing" } [/code] 
*   If the user provided credentials does not match the actual credentials retrieved from environment variables ,then the response is [code language="javascript"] {"result":"error", "description" : "Incorrect credentials" } [/code] 
*   If the user provided credentials match the actual credentials retrieved from environment variables ,then the response is [code language="javascript"]{"result":"success","record":"You are outstanding"}[/code] [su_divider] 

#### manifest.yml [playground edit_mode="yes" repo="mobile_cloud_java_backend" filename="manifest.yml" height="220"] Some of the important values in manifest.file are 

1.  `path: target/MobileCloudJavaBackendDemo-0.0.1-SNAPSHOT.war`. Path variable is used to point to the war file
2.  `buildpack: liberty-for-java` . This build pack is used to deploy the war file mentioned in path varible on a liberty application server
3.  env variables `APP_USER_NAME,APP_USER_PASSWORD` to provide the environment variables for the java application

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/mobile_cloud_java_backend