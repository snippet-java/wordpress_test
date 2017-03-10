---
ID: 1321
post_title: CloudantAdmin
author: snippet java
post_date: 2016-10-21 03:23:22
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/services/cloudant/cloudantadmin/
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
Manage instances of the IBM Bluemix Data Services

**Lab Objectives:***  This lab will show you the basics of how to manage the following Data Services in IBM Bluemix*

*   *Cloudant NoSQL Database*

**Lab Duration :** 15 minutes

1.  Manage instances of the Cloudant NoSQL Database Service

 

In this section you’ll go through the basics of managing the Cloudant NoSQL Database service in IBM Bluemix.

## 1\.1 Launch the Cloudant Dashboard

1.  In your browser go to the Bluemix URL [http://bluemix.net][1] and login is necessary.
2.  Make sure you're in the Dashboard tab (if not click on the Dashboard link at the top of the page to take you there)
3.  Click on **USE SERVICES OR APIS**
4.  Scroll down to the **Data Management ** section and click on **Cloudant NoSQL DB**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-220.png" class="wp-image-1472" />

1.  Under **App **select **Leave unbound**
2.  Click on **CREATE** to create a new instance of Cloudant NoSQL DB
3.  Click **Launch when the service **landing page appears to launch the dashboard

## Create a database

1.  From the dashboard click on **Add New Database**, enter mydatabase as the name and click **Create**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-221.png" class="wp-image-1473" />

1.  You’ll be taken to the administration screen for the new database

## 1\.3 Add data to an existing database

1.  Click on the + icon next to **All Documents** and select **New Doc** from the context menu

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-222.png" class="wp-image-1474" />

1.  A new JSON document will appear with a single attribute named **_id** . This is the unique identifier of your new document. Modify the **_id **and add the fields **field2** and **field3 ** as shown below

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-223.png" class="wp-image-1475" />

1.  Click **Save** to save your changes
2.  Click on the arrow icon shown below to go back to the database view

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-224.png" class="wp-image-1476" />

## 1\.4 Edit documents in a database

1.  From the database view in the dashboard click on **All Documents**, a summary of the documents in the database will appear at the right

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-225.png" class="wp-image-1477" />

1.  Click on the pencil icon of your only document to edit it. Add the field **field4 **as shown below

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-226.png" class="wp-image-1478" />

1.  Click **Save **to save your changes
2.  Click on the arrow icon to go back to the database view

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-227.png" class="wp-image-1479" />

## 1\.5 Clone documents in a database

1.  From the database view in the dashboard click on **All Documents**, a summary of the documents in the database will appear at the right

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-228.png" class="wp-image-1480" />

 

1.  Click on the pencil icon of your only document to edit it.
2.  Click on **Clone Document** in the document editor

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-229.png" class="wp-image-1481" />

1.  You’ll be prompted to accept a system generated unique id for the new clone or to provide your own value. Change the id to myuniqueid2

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-230.png" class="wp-image-1482" />

1.  Click** Clone**. Your clone is added to the database.
2.  Click on the arrow icon to go back to the database view

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-231.png" class="wp-image-1483" />

## 1\.6 Simple query of all documents in a database

1.  From the database view in the dashboard click on **All Documents**, a summary of the documents in the database will appear at the right
2.  Click on **Query Options**, select **Include Docs** and click **Query**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-232.png" class="wp-image-1484" />

1.  Verify that all the fields in your 2 documents appear

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-233.png" class="wp-image-1485" />

 [1]: http://bluemix.net/