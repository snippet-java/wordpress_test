---
ID: 1380
post_title: DashDBAdmin
author: snippet java
post_date: 2016-10-21 03:32:25
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/services/dashdb/dashdbadmin/
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

*   *dashDB *

**Lab Duration :** 15 minutes

1.  Managing instances of dashDB

In this section you’ll go through the basics of managing the dashDB service in IBM Bluemix.

## 1\.1 Launch the dashDB Dashboard

1.  In your browser go to the Bluemix URL [http://bluemix.net][1] and login is necessary.
2.  Make sure you're in the Dashboard tab (if not click on the Dashboard link at the top of the page to take you there)
3.  Click on **USE SERVICES OR APIS**
4.  Scroll down to the **Big Data ** section and click on **dashDB**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-247.png" class="wp-image-1503" />

1.  Under **App **select **Leave unbound**
2.  Click on **CREATE** to create a new instance of dashDB
3.  Click on **Launch** when the service’s landing page appears to bring up the dashDB console

## 2\.2 Create a new table

1.  From the dashDB console click on **Tables   
    **

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-248.png" class="wp-image-1504" />

1.  Click on **Add Table**.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-249.png" class="wp-image-1505" />

1.  Some sample DDL to create a table is generated for you.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-250.png" class="wp-image-1506" />

1.  Let’s use the sample DDL to keep things simple. Click **Run DDL**
2.  Click **OK** in the dialog that indicates the DDL ran successfully and then click **Cancel** to exit the dialog with the sample DDL.

## 1\.3 Browse an existing table

1.  In the dashDB console select **GOSALES **as the **Schema** and **BRANCH** as the **Table Name** and then click on **Browse Data**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-251.png" class="wp-image-1507" />**  
**

1.  Verify that the data in the BRANCH table is displayed

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-252.png" class="wp-image-1508" />

1.  Verify that you can click on a row to see all the data for the row

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-253.png" class="wp-image-1509" />

## 1\.4 Run SQL Scripts

1.  In the dashDB console click on **Run SQL** in the navigation area on the left

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-254.png" class="wp-image-1510" />

1.  A sample script is preloaded that runs against the sample data in dashDB . Click **Run** to run the sample script
2.  Navigate through the results to see the data returned

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-255.png" class="wp-image-1511" />

## 1\.5 Import CSV data

1.  Download the file ***IDS_CSV.zip ***to your local machine*** ***from <http://databank.worldbank.org/data/download/IDS_CSV.zip> This is maintained by the World Bank and has data about each country’s external debt.
2.  Unzip the contents of the file into a folder of your choice
3.  In the dashDB console select ***Load->Load from Desktop***

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-256.png" class="wp-image-1512" />

1.  Click on **Browse files**, select ***IDS_Series.csv ***(this is one of the files in the zip file downloaded in Step 1) and click on*** *Load File**

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-257.png" class="wp-image-1513" />**

1.  Click **Next**
2.  Select **Create a new table and load**

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-258.png" class="wp-image-1514" />

1.  Click **Next**
2.  Accept the defaults for the new table definition and click Finish
3.  A preview of the data in the new table will appear as well as the number of rows imported   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-259.png" class="wp-image-1515" />

 [1]: http://bluemix.net/