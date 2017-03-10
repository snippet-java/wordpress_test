---
ID: 1864
post_title: NodeRed 101
author: snippet java
post_date: 2016-10-21 06:07:26
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/node-red/nodered-101/
published: true
inkblot_webcomic_term_image:
  - ""
inkblot_webcomic_comments:
  - ""
inkblot_avatar:
  - "0"
inkblot_webcomic_group:
  - ""
inkblot_webcomic_image:
  - ""
inkblot_webcomic_order:
  - ""
---
### Before you Begin:

<span>Node-RED is a tool for wiring together hardware devices, APIs and online services in new and interesting ways.Node-RED provides a browser-based flow editor that makes it easy to wire together flows using the wide range nodes in the palette. Flows can be then deployed to the runtime in a single-click.JavaScript functions can be created within the editor using a rich text editor.A built-in library allows you to save useful functions, templates or flows for re-use. </span>  
  
<span>Find more about node-red</span>[here][1]  
  
<span>Deploy your node-red on bluemix by clicking on this button. This instance of node red is pre loaded with sample flow to make your learning journey easier. </span>  
  
<a href="https://bluemix.net/deploy?repository=https://github.com/snippet-java/node-red-playground-bluemix-starter.git" target="_blank"><img src="https://bluemix.net/deploy/button.png" alt="Deploy to Bluemix" /></a><span>[su_divider]</span>
### 1\.Comment ,Inject and Debug nodes

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow1_HelloWorld.png" alt="flow1_helloworld" width="615" height="180" class="aligncenter size-full wp-image-1008" />**Description:**  
<span>This simple flow accepts the string </span>**Hello World!**<span>as input from inject node and displays it using the debug node. </span>  
  
**Details:**  
1.  **Inject** node injects the message into the flow. By default the current time stamp is injected. But the custom message of various javascript types can be injected in the flow. In this flow the string **Hello World!** is injected.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow1_injectNode.png" alt="flow1_injectnode" width="496" height="422" class="aligncenter size-full wp-image-1009" />
2.  **Debug** node displays the output of any message property in the debug tab. The default is to display **msg.payload**. The string received from inject node is displyed in the debug tab.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow1_debugNode.png" alt="flow1_debugnode" width="498" height="270" class="aligncenter size-full wp-image-1007" />

**Things you learnt:**  
<span>Comment ,Inject and Debug Node. </span>  
<span>[su_divider]</span>
### 2\. Function , Delay , Trigger

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow2_DelayTrigger.png" alt="flow2_delaytrigger" width="919" height="397" class="aligncenter size-full wp-image-1011" />**Description:**  
<span>Strings are injected to the flow. The function node is used to append </span>**Hello**<span>before the provided string. This flow demonstrates the use of </span>**delay**<span>and</span>**trigger**<span>nodes </span>  
  
**Details:**  
1.  Strings are provided as inputs for the first two inject nodes. But, third inject node acts as a dummy node to start the flow.
2.  **Delay**node introduces delay in the flow. It can also rate limit the messages. In this flow the delay is set to **3 seconds**. So the message is displayed in debug window three second after receiving the message.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow2_DelayNode.png" alt="flow2_delaynode" width="500" height="274" class="aligncenter size-full wp-image-1010" />
3.  The **trigger** node introduces delay time between tranferring the messages.In this flow the interval between two messages is **500ms.**   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow2_TriggerNode.png" alt="flow2_triggernode" width="498" height="427" class="aligncenter size-full wp-image-1013" />

**Things you learnt:**  
<span>Dela , Trigger and function nodes </span>  
<span>[su_divider]</span>
### 3: HTTP

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow3_http.png" alt="flow3_http" width="909" height="222" class="aligncenter size-full wp-image-1015" />  
**Description:**  
<span>HTTP nodes can be used to create the simple web services. HTTP in node can be configured to create the endpoints , while HTTP out node is used to send HTTP response back to the http requests received from the HTTP in node. </span>  
  
**Details:**  
1.  HTTP input node is used to create an HTTP Endpoint **/hello**. The path of the end point is relative to the root of the application.   
      
    Example: If the root of the application is **node-red-example.mybluemix.net **,the end point created is **node-red-example.mybluemix.net/hello**   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow3_httpInNode.png" alt="flow3_httpinnode" width="499" height="251" class="aligncenter size-full wp-image-1016" />
2.  Function node captures the **name** form the HTTP Request and create a response. This response is passed to the http out node.   
      
    The values need to be passed through URL in this format:   
    node-red-example.mybluemix.net?param1=value1&param2=value2 , In this scenario the parameter need to be passed can be encoded in URL like node-red-example.mybluemix.net?Name=Alice   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow3_functionNode.png" alt="flow3_functionnode" width="499" height="244" class="aligncenter size-full wp-image-1014" />
3.  HTTP out node captures the response.<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/b4_Flow3httpDemo.png" alt="b4_flow3httpdemo" width="575" height="101" class="aligncenter size-full wp-image-1056" />

  
**Things you learnt:**  
<span>HTTP input , HTTP output nodes. </span><span>[su_divider] </span>
### 4: HTML

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow4_HTML.png" alt="flow4_html" width="976" height="435" class="aligncenter size-full wp-image-1017" />**Description:**  
<span>Flow to extract all the content from </span>**H2**<span>tags in a web page. A HTML node is used crawl the content of the web page. </span>  
  
**Details:**  
1.  Inject is used as a dummy node to start the flow.
2.  URL to be crawled is provided as the input for the HTTP Request function node. HTTP node makes the request ans passes the HTML.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/b2_flow4_httpNode.png" alt="b2_flow4_httpnode" width="496" height="345" class="aligncenter size-full wp-image-1031" />
3.  HTML node extracts all the content from **H2** tags and combines them as an array. This array is passed to the debug node.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/b2_flow4_HTML_Tag.png" alt="b2_flow4_html_tag" width="495" height="349" class="aligncenter size-full wp-image-1030" />  
      
    

<span>[su_divider]</span>
### 5: CSV, JSON

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow5_CsvJSON.png" alt="flow5_csvjson" width="1037" height="338" class="aligncenter size-full wp-image-1018" />**Description:**  
<span>HTTP nodes can be used to create the simple web services. HTTP in node can be configured to create the endpoints , while HTTP out node is used to send HTTP response back to the http requests received from the HTTP in node. </span>  
**Details:**  
1.  Firstname **Alice** and LastName **Smith** are injected as a string.
2.  The name of the columns are configured in CSV nodes and it converts received string **"Alice","Smith"** to javaScript object.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/b2_flow5_CSV_Node.png" alt="b2_flow5_csv_node" width="541" height="513" class="aligncenter size-full wp-image-1032" />The corresponding javascript object is [code] { "FirstName": "Alice", "LastName": "Smith" } [/code] 
3.  **JSON** node is used to convert javaScript object to a JSON String. The message from CSV node is received by this node and convert it to a JSON String.

**Things you learnt:**  
<span>CSV , JSON nodes. </span>  
<span>[su_divider]</span>
### 6:IOT

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/flow6_iot.png" alt="flow6_iot" width="973" height="172" class="aligncenter size-full wp-image-1019" />**Description:**  
<span>HTTP nodes can be used to create the simple web services. HTTP in node can be configured to create the endpoints , while HTTP out node is used to send HTTP response back to the http requests received from the HTTP in node. </span>  
**Details:**  
1.  IBM IoT accepts the device ID as the input. Go to [QuickStart IOT][2] to get the device ID of the virtual sensor and provided it to the IBM IoT node. The messages received from this IOT device are passed to function node.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/b2_flow6_IBMIOT_Node.png" alt="b2_flow6_ibmiot_node" width="509" height="385" class="aligncenter size-full wp-image-1034" />
2.  Function node extracts the temperature and humidity from the message and formats it into a new string   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/b2_flow6_DelayNode.png" alt="b2_flow6_delaynode" width="498" height="288" class="aligncenter size-full wp-image-1033" />
3.  JSON node is used to convert javaScript object to a JSON String. The message from CSV node is received by this node and convert it to a JSON String.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/b2_flow6_DelayNode.png" alt="b2_flow6_delaynode" width="498" height="288" class="aligncenter size-full wp-image-1033" />

**Things you learnt:**  
<span>CSV , JSON nodes. </span>

 [1]: http://nodered.org/
 [2]: https://quickstart.internetofthings.ibmcloud.com/iotsensor/