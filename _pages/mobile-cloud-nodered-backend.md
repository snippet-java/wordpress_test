---
ID: 2395
post_title: 'Mobile Cloud &#8211; Nodered Backend'
author: snippet java
post_date: 2016-11-04 15:23:10
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/mobile-cloud-nodered-backend/
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
**Node-Red Backend Flow – Overview** 

This flow act’s as a back end for the Android front end application. Two end points are defined for GET and POST of the URI /checklogin. user_name and user_password are expected to be passed in the POST request body. These credentials are check against the actual credentials and appropriate response is passed as JSON. 

<a href="https://gist.githubusercontent.com/snippet-java/228262095751e852b3ebb927264d064c/raw/9417271bc5dbc7196fb2f3096e3f89cb73f35857/Flow%2520JSON" target="_blank"> <button style="background-color:#719ce2">Get the flow</button> </a> 
**Node-Red Backend Flow – Create ** 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-508.png" class="wp-image-2148" /> 
**Sub Flow A: Details: ** 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-509.png" class="wp-image-2149" /> 

1\. *HTTP Request GET/checklogin* is a is the input node for http GET requests to the path <you-node-red-app>/checklogin. 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-510.png" class="wp-image-2150" /> 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-511.png" class="wp-image-2151" /> 

2\. *Create a response for GET *is a function node. The HTTP in node that accepts GET requests for the endpoint /checklogin mentioned above sends the request data to this function node. 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-512.png" class="wp-image-2152" /> 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-513.png" class="wp-image-2153" /> 

Note that, msg.payload is passed to HTTP Response node. 

3\. Connect this node to HTTP Response node. 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-514.png" class="wp-image-2154" /> 

**Sub Flow B: Details:** 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-515.png" class="wp-image-2155" /> 

1.  *HTTP Request POST/checklogin* is a is the input node for http POST requests to the path <you-node-red-app>/checklogin. 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-516.png" class="wp-image-2156" /> 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-517.png" class="wp-image-2157" /> 

2\. *Create a response for POST *is a function node. The HTTP in node that accepts POST requests for the endpoint /checklogin mentioned above sends the request data to this function node. 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-518.png" class="wp-image-2158" /> 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-519.png" class="wp-image-2159" /> 

The credentials that are provided in HTTP requests are extracted from the msg object by providing` msg.req.body.user_name` and `msg.req.body_user_password`. These credentials are checked against the `test_username` and `test_password`. Msg.payload is set with an appropriate message based and passed to a HTTP Response node. 

3\. Connect this node to HTTP Response node. 

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-520.png" class="wp-image-2160" />