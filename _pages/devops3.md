---
ID: 1541
post_title: DevOps3
author: snippet java
post_date: 2016-10-19 03:26:27
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/services/devops/devops3/
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
Describe how to use the Build & Deploy option to manage continuous integration and continuous delivery

Lab Prerequisites

*   IBM Bluemix account
    *   Sign up for Bluemix: <http://bluemix.net>
*   IBM DevOps account
    *   Sign up for DevOps: <http://hub.jazz.net>
    *   Use the same credentials as for Bluemix
*   Supported web browsers:
    *   Chrome, latest version for your OS
    *   Firefox, latest version for your OS or at least ESR 31
    *   Internet Explorer, versions 10 and 11
    *   Safari, latest version for your OS

1 - Getting Started

1.  As in the 5.3 and 5.4 Labs, begin by logging on to IBM DevOps Services and fork the project located at [https://hub.jazz.net/project/ecosysdevcnc/cdc-lab-5/overview][1] into a new project.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-280.png" class="wp-image-1542" />
2.  Give the new project a unique name, check all the boxes, and choose an appropriate Bluemix runtime configuration. Click on CREATE.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-281.png" class="wp-image-1543" />
3.  Once you see the message about successfully creating your project, click on the EDIT CODE button in the top right.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-282.png" class="wp-image-1544" />
4.  Introduce a change to the project's code by editing public/index.html and alter the <h1> header tag to something unique.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-283.png" class="wp-image-1545" />

2 - Configure the Build and Deploy Pipeline

1.  Switch to the pipeline overview by clicking on BUILD & DEPLOY in the top right.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-284.png" class="wp-image-1546" />
2.  Click the ADD STAGE button.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-285.png" class="wp-image-1547" />
3.  Name the stage "Build Stage", then click on the JOBS tab.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-286.png" class="wp-image-1548" />
4.  Click ADD A JOB -> Build.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-287.png" class="wp-image-1549" />   
    Change Builder Type to "npm", then scroll to the bottom and click SAVE.
5.  Back in the Pipeline: All Stages view, click ADD STAGE again.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-288.png" class="wp-image-1550" />
6.  Name the stage "Deploy Stage" and note the options available for the stage. The default configuration will use the artifacts created from the Build Job in the Build Stage as input, and the Deploy Stage jobs will run on successful completion of the previous stage (Build Stage).   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-289.png" class="wp-image-1551" />   
    Click on the JOBS tab now.
7.  Click ADD JOB -> Deploy   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-290.png" class="wp-image-1552" />
8.  The Deploy stage will default to acceptable options, but take a moment to view the different settings available. The default settings are gathered from the configuration you entered when first forking the project. Accept the default settings and click on SAVE at the bottom.   
    Observe that both stages are now configured in the pipeline.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-291.png" class="wp-image-1553" />

3 - Trigger the Pipeline by Pushing to the Git Repository

1.  Click the EDIT CODE button in the top right.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-292.png" class="wp-image-1554" />
2.  Click the Git button in the left column.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-293.png" class="wp-image-1555" />
3.  Enter an informative commit message, check the box next to Select All, then click on Commit.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-294.png" class="wp-image-1556" />
4.  Note that the outgoing commit is now staged. Click on PUSH, then immediately click on BUILD & DEPLOY.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-295.png" class="wp-image-1557" />   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-296.png" class="wp-image-1558" />
5.  Observe how the build stage is automatically started and once complete, the deploy stage is automatically started.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-297.png" class="wp-image-1559" />
6.  The deploy stage should fail. To determine why, click on the "View logs and history" link.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-298.png" class="wp-image-1560" />
7.  From the log, we can see that Cloud Foundry was not happy with the requested route "REPLACE WITH CUSTOM NAME.mybluemix.net".   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-299.png" class="wp-image-1561" />
8.  Return to the web GUI code editor, and open the manifest.yml file. Replace the host: and name: values with a unique name that will be used when creating the route and URL to your application.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-300.png" class="wp-image-1562" />
9.  Open the Git repository view, and commit the changed manifest file.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-301.png" class="wp-image-1563" />
10. Just ast before, push the staged outgoing commit, then switch back to the BUILD & DEPLOY view. Observe the Build and Deploy stages execution again.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-302.png" class="wp-image-1564" />
11. During the deploy stage's execution, click on the "View logs and history" link and scroll to the bottom of the log stream. Once the application has successfully deployed to Bluemix, you will see a "Finished: SUCCESS" message.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-303.png" class="wp-image-1565" />
12. Scroll to the top of the page and click the Back to Pipeline button.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-304.png" class="wp-image-1566" />
13. Locate the Last Execution Result section inside the Deploy stage summary, and note that the status of the Bluemix runtime is displayed, along with a hyperlink to open the application. Click the link now.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-305.png" class="wp-image-1567" />

4 - Configure a Test Job and Modify the Pipeline

1.  Return to the DevOps Services Build and Deploy Pipeline overview and click the Stage Configuration button on the Build Stage and click Configure Stage.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-306.png" class="wp-image-1568" />
2.  Click ADD JOB -> Test.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-307.png" class="wp-image-1569" />
3.  Accept the default configuration for the Test job. Note that the Simple Tester Type allows one to execute a custom Bash script. Our simple project does not have any testing framework to execute, but if it did this would be the place to execute and evaluate tests. Click the SAVE button at the bottom. Note that a new job is added to the Build Stage overview.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-308.png" class="wp-image-1570" />
4.  Manually start the Build stage by clicking the play button at the top.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-309.png" class="wp-image-1571" />
5.  Note that the Build job executes, followed by the Test job. If either of these jobs were to fail, the pipeline execution would stop and the Deploy Stage would not execute.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-310.png" class="wp-image-1572" />

This completes the IBM Cloud Developer Certification Section 5.5 Lab.

 [1]: http://hub.jazz.net/project/ecosysdevcnc/cdc-lab-5/overview