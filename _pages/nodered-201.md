---
ID: 1867
post_title: NodeRed 201
author: snippet java
post_date: 2016-10-21 06:08:31
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/node-red/nodered-201/
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
### Before you Begin:

<span>Node-RED is a tool for wiring together hardware devices, APIs and online services in new and interesting ways.Node-RED provides a browser-based flow editor that makes it easy to wire together flows using the wide range nodes in the palette. Flows can be then deployed to the runtime in a single-click.JavaScript functions can be created within the editor using a rich text editor.A built-in library allows you to save useful functions, templates or flows for re-use. </span>  
  
<span>Find more about node-red</span><a href="http://nodered.org/" target="_blank">here</a>  
  
<span>Deploy your node-red on bluemix by clicking on this button. This instance of node red is pre loaded with sample flow to make your learning journey easier. </span>  
  
<a href="https://bluemix.net/deploy?repository=https://github.com/snippet-java/node-red-playground-bluemix-starter.git" target="_blank"><img src="https://bluemix.net/deploy/button.png" alt="Deploy to Bluemix" /></a><span>[su_divider]</span>
# **Twitter Sentiment Analysis**

**Description:**

Node-red flow to analyze the tweets based on the sentiment. The tweets can be classified as positive, negative or neutral.

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/11_main_twitter_sentiment-1.png" class="wp-image-1276" alt="11_main_twitter_sentiment" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/11_twitter.json" target="_blank">Get the flow</a>

**Things you can learn: **Working with Twitter API, Understanding sentiment analysis

# **Flow A: Details**

Twitter node need to be configured with credentials and a keyword need to be mentioned in the field named “for”. The tweets having this keyword will be captured and sent as output form this node.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-67.png" class="wp-image-1277" />

These tweets are fed to the sentiment node. Sentiment node analyses the tweets and outputs a number.

If the number is less than zero, then the tweet’s sentiment is negative.

If the number is greater than zero, then the tweet’s sentiment is positive.

If the number is equal than zero, then the tweet’s sentiment is neutral.

Switch node gets the values from the previous sentiment node and directs to suitable debug node based on the value.

Debug nodes print the tweets to debug tab

# **Flickr photo of the day**

**Description:**

Node-Red flow to pick the image from Dropbox every morning and upload to Flickr. 

The images are stored in the Dropbox with corresponding dates. Every morning, an image from Dropbox is picked by calling the API and uploaded it to Flickr.

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-68.png" class="wp-image-1278" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/11_twitter.json" target="_blank">Get the flow</a>

**Things you can learn: **Creating triggers to fire the flow, Using Dropbox API, Using Flickr API, Extract information from EXIF

# **Flow B: Details**

“Fire Every Morning” is an inject node to trigger the flow every morning at the scheduled time.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/2_snip-1.png" class="wp-image-1279" alt="2_snip" />

“Pick File” is a function node to build the name of the file.

It is built by getting the current date and the name is sent to dropbox node as input.

Format of file-name used here is : yyyy-mm-dd.jpg

Example file name : 2016-3-15.jpg.

The details of Dropbox need to be configured in the Drop Box Node. App Key , Secret and Token can be obtained by getting access to the drop box API. More details are provided in the node.For more details regarding Dropbox API visit <https://www.dropbox.com/developers>

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/2_dropbox-2.png" class="wp-image-1280" alt="2_dropbox" />

The Dropbox node gets the file name as the input and fetches the image and send to output.

If the image has the EXIF data, it is extracted and sent to the “Parse EXIF” function node.

“Parse EXIF” node extracts the Image Description and returns it as the title for the image in flickr.

Flickr node need to be configured with the user details. After flickr node get the image from drop box node and title from function node the image is uploaded to flickr. For more details regarding Flickr API visit <https://www.flickr.com/services/api/>

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/2_flickr_config-1.png" class="wp-image-1281" alt="2_flickr_config" />

# **C.MySQL Table Backup to Box.com**

**Description:**

Node-Red flow to query data from MySQL table every day and store the data as CSV in box.com folder.

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/3_main_mysql_to_box-1.png" class="wp-image-1282" alt="3_main_mysql_to_box" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/03_mysql.json" target="_blank">Get the flow</a>

**Things you can learn: **Working with MySQL Database, Scheduling the trigger every day, working with Box.com, Converting the data formats

# **Flow C: Details**

Inject node fires every morning at the scheduled time.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/3_inject-2.png" class="wp-image-1283" alt="3_inject" />

Function node builds the SQL query to fetch the data from the MySQL table.

MySQL node connects to the DB using credentials and extracts the data from table based on the SQL query that was provided as an input form the function node. The extracted data is in the format of Java Script object and sent as output.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-69.png" class="wp-image-1284" />

CSV node converts the data to CSV file.

Box.com credentials need to be configured in box.com node. The CSV file provided as an input is stored in specific folder of box.com

# **D. Translate text from source to destination language**

**Description:**

Node-red flow to convert the text from source language to destination language.

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/14_main_translatoin-1.png" class="wp-image-1285" alt="14_main_translatoin" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/14_LanguageTranslation" target="_blank">Get the flow</a>

**Things you can learn: **Working with Watson Language Translation

# **Flow D: Details-1**

The text need to be provided as the input through inject node. [Refer left image]

Language translation node need to be configured with credentials and also source and destination languages. [Refer right image]

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/14_inject-1.png" class="wp-image-1286" alt="14_inject" />

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/14_watson_config-1.png" class="wp-image-1287" alt="14_Watson_config" />

Debug nodes print the text in destination language.

The details of Dropbox need to be configured in the Drop Box Node. App Key, Secret and Token can be obtained by getting access to the drop box API. More details are provided in the node. For more details regarding Dropbox API visit https://www.dropbox.com/developers

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/2_dropbox-3.png" class="wp-image-1288" alt="2_dropbox" />

The Dropbox node gets the file name as the input and fetches the image and send to output.

If the image has the EXIF data, it is extracted and sent to the “Parse EXIF” function node.

“Parse EXIF” node extracts the Image Description and returns it as the title for the image in Flickr.

# **E. Convert Text to Speech**

**Description:**

Node-Red flow to convert the text into speech. The text can be in any of the four languages in English, German, French, Spanish. Also the voice can be configured to either male or female 

Specifically, this flow adds an HTTP endpoint called /mapstations to your Node-RED instance that when hit returns a Google Map with pins for all the BART stations in San Francisco. The location details of all BART stations are fetched from API by making an HTTP request.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/13_main_speech_to_text-1.png" class="wp-image-1289" alt="13_Main_Speech_To_Text" />

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/13_TextToSpeech.json" target="_blank">Get the flow</a>

# **Flow E: Details**

Inject node fires the flow during deployment. The text to be converted into speech need to be provided as input in this node.

Text to Speech node need to be configured with credentials and language options.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/13_watson_config-1.png" class="wp-image-1290" alt="13_watson_config" />

The function node receives the speech buffer as input and pipes it to web socket ws/audio

The web socket ws/audio is configured to listen continuously.

HTTP node defines the endpoint /audio.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/13_web_socket-1.png" class="wp-image-1291" alt="13_web_socket" />

Template node contains the web page format and code to play the audio using JavaScript. The template node listens to the web socket /ws/audio mentioned in the main flow.

When data is present in web socket, it is played using HTTP response

# **F. Alchemy Image Analysis**

**Description:**

Node-red flow to analyze the image. Input image is provided as the URL using a web form and result is displayed back. Alchemy API identifies the objects in the image.

Example: When an URL of the image containing iPhone is provided as the input, the result would contain the term “iPhone”

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/10_main_edit_alchemy-1.png" class="wp-image-1292" alt="10_main_edit_alchemy" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/12_AlchemyImage.json" target="_blank">Get the flow</a>

# **Flow F: Details:**

HTTP endpoint /findproduct with GET is defined.

Template node has the HTML to accept input from the user using textbox and a submit button.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/10_web_page_input-1.png" class="wp-image-1293" alt="10_web_page_input" />

The URL of image need to be provided in the “Title” text field and then “Analyse Image!!!” button need to be clicked.

The button calls for POST on HTTP Endpoint /image result and below Sub Flow is fired

HTTP endpoint /imageresult is defined with POST method.

The image URL is extracted by the function node and passed to Alchemy Image node.

Alchemy image node analyses the image and returns the result in JSON format to the HTTP Response node.

The result is displayed on the webpage as JSON.

Sample Output:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/10_web_page_output-1.png" class="wp-image-1294" alt="10_web_page_output" />

# **H. Convert Speech to Text**

**Description:**

Node-red flow to convert the speech to text. In this sample flow the audio is provided as a link

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/12_main_speech_to_text-1.png" class="wp-image-1295" alt="12_main_speech_to_text" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/12_SpeechToText.json" target="_blank">Get the flow</a>

**Things you can **Working with Watson Speech to Text

# **Flow G: Details:**

URL of the audio file is provided as the input for inject node. [Refer left Image]

“Speech to text node need to be configured with credentials and language.[Refer Right image]

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/12_watson_config-1.png" class="wp-image-1296" alt="12_watson_config" /> <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-70.png" class="wp-image-1297" />

Debug nodes print the text for the corresponding speech in the debug tab.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/12_debug-1.png" class="wp-image-1298" alt="12_debug" />

# **H.Plot Locations on Google Maps**

**Description:**

Node-Red flow to plot the locations based on co-ordinates on google maps.

Specifically, this flow adds an HTTP endpoint called /mapstations to your Node-RED instance that when hit returns a Google Map with pins for all the BART stations in San Francisco. The location details of all BART stations are fetched from API by making an HTTP request.

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-71.png" class="wp-image-1299" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/01_Plot_Locations_on_Google_Maps.json" target="_blank">Get the flow</a>

**Things you can learn: **Making HTTP Requests, Working with API’S, Working with Web Sockets, Converting Data Formats

# **Flow H: Details - 1**

HTTP Endpoint /mapstations is created with GET method using the node “Map Stations HTTP End point”

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-72.png" class="wp-image-1300" />

Now, a request made to this endpoint will trigger the template node “Plot Locations”

Endpoint Format: http://url-of-node-red-instance/end-point

Example: http://noderedexample.mybluemix.net/mapstations

“Plot Locations” is a template node with HTML code. Calls to Google Maps API and web socket /ws/stations is made in the code. This node makes request to Google API , calls the web socket to fetch data related to BART stations and presents to used.

Call to google API is made to initialize the map and add animation effects.

Request to web socket ws/stations is made to the data related to BART stations

ws/stations provided the information of all the BART stations as a java script object. (View the Sub-Process for more details)

The obtained stations are plotted on the map.

The HTTP Response node get the HTML code form the template node and builds the response.

“Web Socket” node listens to the /ws/stations. [Refer Left Image]

This web socket node triggers the HTTP request node to call the API of BART. [Refer Right image]

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/1_bart_api_call-1.png" class="wp-image-1301" alt="1_bart_api_call" /><img src="http://bluecloudnews.com/wp-content/uploads/2016/10/1_web_socket-1.png" class="wp-image-1302" alt="1_web_socket" />

The HTTP node returns the data in the form of XML.

The XML data is converted to java script object by the node “XML to JavaScript Object” Node.

Converted data is returned by the web socket.

# **I. Website Availability**

**Description:**

Node-red flow to check the status of website in isup.me and sends a SMS using Twillio if the website is done. Messages are configured periodically.

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/8_main_website_up_twilip-1.png" class="wp-image-1303" alt="8_main_website_up_twilip" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/08_website.json" target="_blank">Get the flow</a>

# **Flow I: Details**

Isup.com is used to check the website availability. Inject nde is used to check trigger the flow for every 30 min

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/8_inject-1.png" class="wp-image-1304" alt="8_inject" />

HTTP node “Website Availability” requests isup.com to get the current status of the website.

HTML node “Extract Status” extract the data in the HTML class with ID as #Container. If this text contains the word isup , then the website is up and running.

A function node is used to check if the website is up or down and returns the value in the form of Boolean (true of false)

Switch node acts like an if-else block and triggers the “Compose SMS block” if the website is down.

The function node is used to compose the SMS and trigger the rate limiter node. Here rate limiter is configured to send one SMS per day. But it can also be configured to send SMS’s based on the interval [Refer left image]

Rate limiter triggers Twillio node to send the SMS. Please be noted that Twilio node need to be configured with the credentials. [Refer right image]

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/8_rate_limiter-1.png" class="wp-image-1305" alt="8_rate_limiter" />

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-73.png" class="wp-image-1306" />

# **J.Microblog**

**Description:**

Node-Red flow to create a simple micro-blog web page using mongoDB as the storage and HTTP endpoints.

Using the MongoDB node as a storage for posts, http nodes to provide end points for the service and the html node to format the micro-blog web page.

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/3_main_micro_blog_mysql-1.png" class="wp-image-1307" alt="3_main_micro_blog_mysql" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/04_microblog.json" target="_blank">Get the flow</a>

# **Details**

HTTP Endpoint names public/posts is created for GET method.

MongoDB node fetches the data from the specific collection and pipes the data as the output.

Note: MongoDB need to be configured by providing credentials.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-74.png" class="wp-image-1308" />

Template node contains the HTML to submit a new blog and display the existing blogs

Submitting a new blog call the POST method (Process for POST explained below)

# **Flow J : Process for flow Request**

HTTP Endpoint names public/posts is created for POST method.

The new blog is inserted into mongoDB. The monogDB node need to be configured with credentials and the type of query

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-75.png" class="wp-image-1309" />

Simultaneously the HTTP node triggers the function node. This function node indeed call the get same end point with get method.

Now, the data is displayed along with the newly created blog.

# **K. Dump Data to Cloudant DB**

**Description:**

Node-Red flow to insert CVS data to Cloudant DB.

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/6_main_csv_cloudant-1.png" class="wp-image-1310" alt="6_main_csv_cloudant" />**

<a href="https://gist.githubusercontent.com/snippet-java/02247cf2d1512ea032c987e783043818/raw/7a7a37fd9f8a38448be537dbc58dd6b9f3695edb/04_microblog.json" target="_blank">Get the flow</a>

**Things you can learn: **Working with MySQL Database, Scheduling the trigger every day, working with Box.com, Converting the data formats

# **Flow K: Details**

Inject node fires every morning at the scheduled time.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/3_inject-3.png" class="wp-image-1311" alt="3_inject" />

2\. The HTTP node “CSV File online request” gets the CSV file by requesting the resource by the URL. This node outputs the CSV file.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-76.png" class="wp-image-1312" />

CSV file is to be converted into JSON format before inserting in Cloudant DB. To achieve this , the CSV file is conveted to Javascript Object and then JSON.

The Cloudant DB need to be configured by providing the credentials. The JSON data is inserted into the Cloudant DB.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-77.png" class="wp-image-1313" />

# **L. Insert Data in Redis Database**

**Description:**

Node-red flow to insert key-value pair in Redis Database Messages are configured periodically.

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/9_main_redis-1.png" class="wp-image-1314" alt="9_main_redis" />**

**Things you can learn: **Working with Redis Database

# **Flow L: Details**

Inject node is triggered when deployed.

Function node “Key Value Pair” sets payload.msg to the key and value pair to be inserted in the Redis DB.

Redis node need to be configured by providing credentials and the type of command.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-78.png" class="wp-image-1315" />

Debug node is used to print the status of the operation.