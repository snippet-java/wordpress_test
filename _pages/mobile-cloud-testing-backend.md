---
ID: 2398
post_title: 'Mobile Cloud &#8211; Testing Backend'
author: snippet java
post_date: 2016-11-04 15:24:44
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/mobile-cloud-testing-backend/
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
**Mobile Cloud Backend REST Commands testing** 

**Using CURL:** 

Download and install <a href="https://curl.haxx.se/download.html" target="_blank">CURL</a> 

Perform post request to the endpoint by providing username and password. 

`curl --data "user_name=test_username&user_password=test_password" <url>/path` 

The result will be a JSON String. 

**Using Postman:** 

Download post man for chrome at [getpostman][1] 

1.  Open the postman and make the POST request to your app with these details.
    1.  Make the request type as POST 
    2.  Endpoint is <yourappurl>/checklogin 
    3.  In the body, select ‘raw’,’JSON’ and pass the JSON as the body for the post request. The JSON should include user_name and user_password. 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/11/word-image-50.png" class="wp-image-2363" /> 

If the user_name and user_password provided are correct ,then the response is a JSON object with the values result and record </li>

 [1]: https://www.getpostman.com/