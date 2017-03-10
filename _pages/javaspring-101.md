---
ID: 1879
post_title: JavaSpring 101
author: snippet java
post_date: 2016-10-21 10:24:59
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/microservices/javaspring-101/
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
Microservices can basically be considered as component/process/application with characteristics of small, independent and replaceable to compose a complex application.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/Microservice-application.jpg" alt="microservice-application" width="258" height="302" class="alignnone size-full wp-image-2100" /> 

Spring Boot, one of the modules fall under Spring.io family, provides starter kit that allow us, the developers, to quickly setup the microservice application foundation and ready for deployment within hours.

Here, the use case we are using is to deploy eureka client applications that show randomly the Company Stock symbol followed by mocked stock status. To monitor the status of those clients, we setup a Eureka server, in which those Eureka clients report application heartbeat status too. We also setup load balancing using Ribbon and failover using Hystrix. All components mentioned (Eureka server, client, Ribbon, Hystrix) are packaged under Spring Boot.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/Spring-Boot-Discovery-Service-Architecture-diagram2.jpg" alt="spring-boot-discovery-service-architecture-diagram2" width="878" height="485" class="alignnone size-full wp-image-2124" /> 

**Eureka Server **

Deploy your first eureka-server on bluemix by following guidance below. After successful deployment, browse to the Eureka server url and view status of Eureka Server by itself along with other Eureka clients

Guidance:   
1) Under **application.properties** file below, edit eureka.client.serviceUrl.defaultZone=http://DESIRED_EUREKA_SERVER_HOSTNAME/eureka/ (e.g. <font color="blue">http://myeureka-server.mybluemix.net</font>)   
2) Hit "Save" button   
3) Hit "Deploy" button - you will get redirected to "deploy to Bluemix page". REPLACE the **APP NAME** with the one defined in application.prorperties (e.g. <font color="blue">myeureka-server</font>)   
<font color="red"><strong>WARNING</strong>: This is very important step. APP NAME must be identical with the one defined in application.properties, or it won't work !!</font> [playground edit_mode="yes" show_deploy="yes" repo="eureka-server" filename="src/main/resources/application.properties" height="210"][/playground] 

**Other Files:**

pom.xml</br> [playground edit_mode="yes" repo="eureka-server" filename="pom.xml"][/playground] 

EurekaServerApplication.java</br> [playground edit_mode="yes" repo="eureka-server" filename="src/main/java/com/example/EurekaServerApplication.java"][/playground] 

Prerequisite:

*   Eclipse Mars
*   Maven (3.3.9)
*   JDK 1.7
*   Github Account

***Import from Github***

1.  Open Eclipse, under Project Explorer** **view, right click on white space, and select **Import > Import > Git > Project from Git > Clone Uri**
2.  In Source Git Repository** **window, at **URI** column, enter <font color="blue">https://github.com/snippet-java/eureka-server</font> . Enter also your Github account username and password. Click **Next**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-480.png" class="wp-image-1894" />

1.  Select **Master** (By default all available Github branches are checked. Check only **Master** if other branches exist as well), then click **Next**
2.  Leave all defaults, and click **Next** again
3.  Select to **Import as general project** and click **Next**
4.  Define your **Project name**, and finally click **Finish**

***Project Structure Exploration***

1.  After successful import, the project structure should appear as following

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/eureka-server-file-structure.jpg" alt="eureka-server-file-structure" width="301" height="326" class="alignnone size-full wp-image-2111" /> 

1.  Expand to open Java Resources > src/main/java > com.example > **EurekaServerApplication.java**
2.  In this class file, notice the *@EnablEurekaServer*. This single annotation created a Eureka Server. That’s it, very simple. Of course we need to see the supporting libraries defined in **pom.xml** and some configuration entities within **application.properties**.
3.  Open the pom.xml, notice the code under red bracket at screenshot below

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-482.png" class="wp-image-1896" />

This is the only library needed for Eureka server (while other dependency is for setting up Spring project)

1.  Open the application properties, the code under red bracket signify the Eureka server url that this Eureka server and other subsequent client servers to bind to

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-483.png" class="wp-image-1897" />

***Run Locally***

1.  Locate **EurekaServerApplication.java** at **src/main/java**, right click, select **Run As > Java Application**
2.  Under **Console** view, you should find the message “*Tomcat started on port(s): 8080*”   
    *Note: default port is 8080. To change the port no, open application.properties and add server.port=<port_number>*
3.  Open the browser, and enter <http://localhost:8080>
4.  Eureka Server webpage shown

***Run on Bluemix***

1.  Open command prompt, and go to the workspace directory
2.  Enter command **mvn package**
3.  Open manifest.yml and verify **path** is pointing to the valid path of generated WAR file
4.  Enter command **cf push**
5.  Wait until the application successfully deployed and started, open browser and enter hostname.   
    *Note: If forget the hostname url, enter command ****cf app <App_Name>***
6.  Eureka Sever webpage shown

**Expected Outcome**</br> <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/eureka-server-output3.jpg" alt="eureka-server-output3" width="715" height="360" class="alignnone size-full wp-image-2110" /> 

**Eureka Clients**

There are 3 client applications to be deployed:

*   Eureka-client-subject: To display randomly company stock symbol
*   Eureka-client-verb: To display randomly stock status
*   Eureka-client-sentence: To make REST call and display the combination of random selection of subject and verb applications above

**Eureka-client-subject** 

Deploy your first eureka-client-subject on bluemix by following guidance below. After successful deployment, browse to the URL and you should see a random company stock symbol being displayed. Refresh to see different word

Guidance:   
1) Under **application.properties** file below, edit eureka.client.serviceUrl.defaultZone=http://DESIRED_EUREKA_SERVER_HOSTNAME/eureka/ (e.g. <font color="blue">http://myeureka-server.mybluemix.net</font>)   
This should be the same as above when configure eureka server   
2) Hit "Save" button   
3) Hit "Deploy" button - you will get redirected to "deploy to Bluemix page". [playground edit_mode="yes" show_deploy="yes" repo="eureka-client-subject" filename="src/main/resources/application.properties" height="210"][/playground] 

**Other Files:**

pom.xml</br> [playground edit_mode="yes" repo="eureka-client-subject" filename="pom.xml"][/playground] 

SubjectApplication.java</br> [playground edit_mode="yes" repo="eureka-client-subject" filename="src/main/java/com/example/SubjectApplication.java"][/playground] 

EurekaClientController.java</br> [playground edit_mode="yes" repo="eureka-client-subject" filename="src/main/java/com/example/EurekaClientController.java"][/playground] 

To import projects from GitHub to Eclipse, follow the steps under **Eureka Server** section Step 1-6. At Step 2, change URL to <font color="blue">https://github.com/snippet-java/eureka-client-subject</font> 

***Project Structure Exploration***

1.  After successful import, the project structure should appear as following

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/subject-file-structure.jpg" alt="subject-file-structure" width="370" height="378" class="alignnone size-full wp-image-2115" /> 

1.  Expand Java Resources > src/main/java > com.example, there are 2 class files
    1.  **SubjectApplication.java** – notice the different annotation usage compared to Eureka server. This uses *@EnableEurekaClient*
    2.  **EurekaClientController.java** – A REST controller that randomly pick the company stock symbol from **application.properties**
2.  Open pom.xml, notice the same dependency included as Eureka server
  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-485.png" class="wp-image-1899" /></br>
3.  Expand Java Resources > src/main/resources, there are 2 properties files
    1.  **application.properties – **
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-486.png" class="wp-image-1900" /></br>
    2.  **bootstrap.properties** –

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-487.png" class="wp-image-1901" /></br> 
1.  To run locally, can follow steps from Eureka Server above. The main method can be found at **SubjectApplication.java**
2.  To run on Bluemix, follow the exact same steps from Eureka Server above. 

**Expected Outcome**</br> <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/subject-outcome.jpg" alt="subject-outcome" width="404" height="77" class="alignnone size-full wp-image-2119" /> 

**Eureka-client-verb** 

Deploy your first eureka-client-verb on bluemix by following guideline below. After successful deployment, browse to the URL and you should see a random stock status being displayed. Refresh to see different word

Guidance:   
1) Under **application.properties** file below, edit eureka.client.serviceUrl.defaultZone=http://DESIRED_EUREKA_SERVER_HOSTNAME/eureka/ (e.g. <font color="blue">http://myeureka-server.mybluemix.net</font>)   
This should be the same as above when configure eureka server   
2) Hit "Save" button   
3) Hit "Deploy" button - you will get redirected to "deploy to Bluemix page". [playground edit_mode="yes" show_deploy="yes" repo="eureka-client-verb" filename="src/main/resources/application.properties" height="210"][/playground] 

**Other Files:**

pom.xml</br> [playground edit_mode="yes" repo="eureka-client-verb" filename="pom.xml"][/playground] 

VerbApplication.java</br> [playground edit_mode="yes" repo="eureka-client-verb" filename="src/main/java/com/example/VerbApplication.java"][/playground] 

EurekaClientController.java</br> [playground edit_mode="yes" repo="eureka-client-verb" filename="src/main/java/com/example/EurekaClientController.java"][/playground] 

To import projects from GitHub to Eclipse, follow the steps under **Eureka Server** section Step 1-6. At Step 2, change URL to <font color="blue">https://github.com/snippet-java/eureka-client-verb</font> 

***Project Structure Exploration***

1.  After successful import, the project structure should appear as following
  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/verb-file-structure.jpg" alt="verb-file-structure" width="340" height="374" class="alignnone size-full wp-image-2116" />   
2.  Expand Java Resources > src/main/java > com.example, there are 2 class files
    1.  **VerbApplication.java** – notice the different annotation usage compared to Eureka server. This uses *@EnableEurekaClient*
    2.  **EurekaClientController.java** – A REST controller that randomly pick the stock status from **application.properties**
3.  Open pom.xml, notice the same dependency included as Eureka server
4.  Open **application.properties**
  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-489.png" class="wp-image-1903" />  
5.  Open **bootstrap.properties**
  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-490.png" class="wp-image-1904" />  
6.  Follow steps above to run locally or on Bluemix

**Expected Outcome**</br> <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/verb-outcome.jpg" alt="verb-outcome" width="369" height="77" class="alignnone size-full wp-image-2120" /> 

**Eureka-client-sentence** 

Deploy your first eureka-client-sentence on bluemix by following guideline below. After successful deployment, browse to the URL and you should see a random combination of company stock symbol and stock status being displayed. Refresh to see different word.   
In addition, this client includes Ribbon, Feign, and Hystrix components.

*Prerequisite: Deploy Eureka-client-subject AND Eureka-client-verb applications*

Guidance:   
1) Under **application.properties** file below, edit eureka.client.serviceUrl.defaultZone=http://DESIRED_EUREKA_SERVER_HOSTNAME/eureka/ (e.g. <font color="blue">http://myeureka-server.mybluemix.net</font>)   
This should be the same as above when configure eureka server   
2) Hit "Save" button   
3) Hit "Deploy" button - you will get redirected to "deploy to Bluemix page". [playground edit_mode="yes" show_deploy="yes" repo="eureka-client-sentence" filename="src/main/resources/application.properties" height="210"][/playground] 

**Other Files:**

pom.xml</br> [playground edit_mode="yes" repo="eureka-client-sentence" filename="pom.xml"][/playground] 

SentenceApplication.java</br> [playground edit_mode="yes" repo="eureka-client-sentence" filename="src/main/java/com/example/SentenceApplication.java"][/playground] 

EurekaClientController.java</br> [playground edit_mode="yes" repo="eureka-client-sentence" filename="src/main/java/com/example/EurekaClientController.java"][/playground] 

SentenceService.java</br> [playground edit_mode="yes" repo="eureka-client-sentence" filename="src/main/java/com/example/SentenceService.java"][/playground] 

SentenceServiceImpl.java</br> [playground edit_mode="yes" repo="eureka-client-sentence" filename="src/main/java/com/example/SentenceServiceImpl.java"][/playground] 

VerbFeignClient.java</br> [playground edit_mode="yes" repo="eureka-client-sentence" filename="src/main/java/com/example/VerbFeignClient.java"][/playground] 

To import projects from GitHub to Eclipse, follow the steps under **Eureka Server** section Step 1-6. At Step 2, change URL to <font color="blue">https://github.com/snippet-java/eureka-client-sentence</font>

***Project Structure Exploration***

1.  After successful import, the project structure should appear as following
  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/sentence-file-structure.jpg" alt="sentence-file-structure" width="379" height="451" class="alignnone size-full wp-image-2117" />   
2.  Expand Java Resources > src/main/java > com.example, notice there are a few additional files compared to *Eureka-client-subject *and *Eureka-client-verb*
    1.  **SentenceApplication.java** – additional annotations *@EnableFeignClients* and *@EnableHystrix *
    2.  **EurekaClientController.java** – to make REST call to retrieve words from Eureka-client-subject and Eureka-client-verb
    3.  **SentenceService.java – **notice the *@Service*, which make this class a service bean to serve the requirement to enable Hystrix component. *@HystrixCommand* is to determine which fallback method as backup to call, should the method run into no service. More details will be explained at *Scenario* section below.
    4.  **VerbClient.java** – Use Feign Client to replace RESTTemplate to make rest call to Eureka-client-verb
3.  Open pom.xml, notice the different dependencies required
  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-492.png" class="wp-image-1906" />  
4.  Expand Java Resources > src/main/resources 
    1.  **application.properties** – common properties to serve as Eureka client
    2.  **bootstrap**.**properties** – application instance name shown at Eureka Server
5.  Follow the same methods above to run locally or on Bluemix

**Expected Outcome**</br> <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/sentence-outcome.jpg" alt="sentence-outcome" width="400" height="74" class="alignnone size-full wp-image-2121" /> 

**Scenarios:**

1.  Load-balancing: 
    1.  Start 2 instances of Eureka-client-subject applications   
        *Can try using different Word samples (defined at application.properties) to witness the load-balancing functionality*
    2.  At Eureka Server webpage, notice there should be 2 instances of Eureka-client-subject
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-493.png" class="wp-image-1907" />  
    3.  Browse to Eureka-client-sentence URL, then refresh, you should see the Sentence application has made REST call to each of the 2 Subject applications in round-robin fashion. (this is more obvious if different word sampling at subject applications)
    4.  Stop one of the server application. Then refresh Sentence URL. At first you might see intermittently server error. The reason being is Sentence, working as one of the Eureka client, is yet to receive information from Eureka server that one of Subject instances has gone down.   
        After a while (about 1 minute), the error should be gone, and Sentence will only fetch data from functioning Subject
    *   Hystrix: 
        1.  In this use case, we apply failover only to Verb. The expected outcome to be when Verb application is down, the Sentence should not give server error response. On the other hand, backup value will be returned to Sentence to show
        2.  Let’s try by bring up all Subject, Verb and Sentence applications. Browse to Sentence URL and make sure it works and display a random combination of words from Subject and Verb
        3.  Stop Verb application. Then refresh Sentence URL. At first you might see server error. The reason being is Sentence, working as one of the Eureka client, is yet to receive information from Eureka server that Verb instance has gone down   
            After a while (about 1 minute), Sentence URL should work normally and display word, but this time from backup value.</ol> 
    Congratulations, you have just setup a Eureka sever with 3 Eureka clients inclusive of Load-balancing and failover functionalities.