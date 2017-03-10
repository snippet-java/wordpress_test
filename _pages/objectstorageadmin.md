---
ID: 1588
post_title: ObjectStorageAdmin
author: snippet java
post_date: 2016-10-21 05:42:23
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/services/objectstorage/objectstorageadmin/
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
Object Storage Services in IBM Bluemix

**Lab Objectives:***  This lab will demonstrate the  use the IBM Softlayer Object Storage Services in IBM Bluemix as a cloud based permanent storage repository accessible via a REST API*

**Prerequisities:** *The Google Chrome browser with the free Postman application (for testing the Swift API in the Object Storage Service). Postman is available here: https://www.getpostman.com*

**Lab Duration :** 30 minutes

1.  Creating an app and an Object Storage V1 instance in Bluemix

 

In this section you’ll create an app and an instance of the Object Storage V1 service in IBM Bluemix.

1.  In your browser go to the Bluemix URL [http://bluemix.net][1] and login is necessary.
2.  Make sure you're in the Dashboard tab (if not click on the Dashboard link at the top of the page to take you there)
3.  Scroll down to the **Applications** section and click on **CREATE APP**
4.  Click on** WEB**
5.  Click on **SDK for Node.js** and then click **CONTINUE**
6.  Give your app a unique name using alphanumeric characters only and click **FINISH **
7.  Wait for the message that says** ***Your app is running  
      
    * <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-351.png" class="wp-image-1627" />
8.  Click on the **Dashboard **link at the top of the page again
9.  Click on **USE SERVICES OR APIS**
10. Scroll down to the **Data** **& Analytics** section and click on **Object Storage **(Note: select** Object Storage **not **Object Storage (v2)**)** **

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-352.png" class="wp-image-1628" />

1.  Under **App **select the app you just created
2.  Click on **CREATE** to create a new instance of Object Storage
3.  Click **RESTAGE **when prompted to restage your app.
4.  Get the credentials required to access the Object storage Service via REST

In this section you’ll get the credentials required to access your Object Storage Service instance via its REST API.

1.  Click on the Dashboard link at the top of the page again
2.  Scroll down to the **Applications **section and click on the icon for the application use just created

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-353.png" class="wp-image-1629" />

1.  On the left select **Environment Variables** to show the access information for your instance of the Object Storage Service   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-354.png" class="wp-image-1630" />
2.  Copy the values of the following fields (without the double quotes) to an open file on your system so you can cut and paste this information in subsequent steps.   
      
    auth_uri username password

 

1.  Authenticate against your Object Storage Service instance using POSTMAN

In this section you’ll use the POSTMAN Chrome application to authenticate against your Object Storage Service instance

1.  If it’s not already running bring up your Chrome browser.
2.  Click on the Apps icon

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-355.png" class="wp-image-1631" />

1.  Click on the icon to launch POSTMAN. A new window should appear
2.  Go back to the file where you saved the access credentials and copy the **auth_url** to the field that has the text **Enter request URL here**

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-356.png" class="wp-image-1632" />**

1.  Append / to the URL you just pasted , go back to the file where you saved the access credentials, copy the **username **and paste it after the** / **so your URL is now in the form ** auth_url/username**
2.  Under Authorization select Basic Auth and copy in the username and password from your saved credentials in the corresponding fields

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-357.png" class="wp-image-1633" />

1.  Click **Update request**
2.  Click on **Send** to send the request
3.  Verify that the Status indicates **200 OK** and then click on **Headers**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-358.png" class="wp-image-1634" />

1.  Save the values of **X-Auth-Token** and **X-Storage-Url** from the returned header in your credentials file so you can copy and paste these values in the next section
2.  Using the Swift API to manage containers and objects

In this section you’ll run through some typical Swift API operations using the POSTMAN Chrome application.

1.  In POSTMAN click on the + icon to start a new tab

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-359.png" class="wp-image-1635" />

1.  Copy the **X-Storage-Url** value you saved in the previous section into the URL field
2.  Append /mycontainer to the URL
3.  Change the HTTP verb from **GET** to **PUT **to create a new container** **
4.  Click on **Headers(0)** and create a header with label **X-Auth-Token** and value set to the value of the returned token you saved in the previous section

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-360.png" class="wp-image-1636" />

1.  Click **Send** – verify that the returned Status is **201 Created **

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-361.png" class="wp-image-1637" />

1.  Change the HTTP Verb from **PUT** to **HEAD** to get the metadata for the new container. Click **Send** (note you’re reusing the same header value from the previous request )
2.  Verify that returned Status is** 204 No Content **and that several metadata values are in the returned HTTP header

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-362.png" class="wp-image-1638" />

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-363.png" class="wp-image-1639" />

1.  Change the HTTP Verb from **HEAD** to **PUT** in order to perform an upload operation
2.  Click on the **Body** tab and then select **binary**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-364.png" class="wp-image-1640" />

1.  Click **Choose File** and select a file on your local system
2.  Go back to the URL field and append /filename to the URL , where **filename** is the name of the file you selected. For example if you selected **foo.txt** then you would append /foo.txt to the URL

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-365.png" class="wp-image-1641" />

1.  Click **Send **and verify that **Status 201 Created** is returned
2.  Change the HTTP Verb from **PUT **to **GET** so you can send a list request for the container
3.  Remove the filename suffix from the URL
4.  Click** Send** and verify that the name of the file you just uploaded is returned

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-366.png" class="wp-image-1642" />

1.  Append ?format=json to the URL and send the **GET** request again. Verify that info about the file you uploaded is returned in JSON format
2.  Remove the ?format=json suffix from the URL and append /filename to the URL , where **filename** is the name of the file you uploaded earlier
3.  Click **Send** and verify that the content of the file is returned and that the Status is **200 OK**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-367.png" class="wp-image-1643" />

1.  Change the HTTP Verb from **GET **to **DELETE** to delete the file you uploaded earlier
2.  Click **Send** and verify that **Status 204 No content** is returned
3.  Change the HTTP Verb from **DELETE **to **GET** so you can send a list request for the container
4.  Remove the filename suffix from the URL
5.  Click **Send **and verify that **Status 204 No content** is returned (note: there is no content because the container has no files)

Congratulations ! You successfully created an instance of the Object Storage Service in Bluemix and executed the most common REST API calls.

 [1]: http://bluemix.net/