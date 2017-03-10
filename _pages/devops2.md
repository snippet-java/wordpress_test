---
ID: 1518
post_title: DevOps2
author: snippet java
post_date: 2016-10-19 03:25:12
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/services/devops/devops2/
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
Edit and debug Cloud applications using IBM Bluemix DevOps Services web code editor

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

1.  Begn by forking the lab project in DevOps Services. Open your browser and navigate to <http://hub.jazz.net>, then click on the Login button in the top right.

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-260.png" class="wp-image-1519" />   
Enter your IBM account credentials to complete the logon process.

1.  Next, open the URL [https://hub.jazz.net/project/ecosysdevcnc/cdc-lab-5/overview][1] and click the FORK PROJECT button in the top-right corner.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-261.png" class="wp-image-1520" />
2.  In the Fork Project dialog, enter a unique name for the project, and check the "Private project", "Add features for Scrum development", and "Make this a Bluemix Project" boxes. Configure an appropriate Bluemix space, then click on CREATE.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-262.png" class="wp-image-1521" />

2 - Using the DevOps Service Web Code Editor

1.  Once you see the message about successfully creating a new project, click on the EDIT CODE button in the top right.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-263.png" class="wp-image-1522" />
2.  This is the DevOps Services web code editor. Along the top, you will find the menu bar, with options File, Edit, View, and Tools. To the right are the Bluemix runtime control buttons. Along the left column are various buttons for switching between the code editor, git repository, shell, applications, and options views. Immediately to the right of these buttons is the filesystem explorer, and to the right, taking up the majority of the screen, is the code editor and preview pane.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-264.png" class="wp-image-1523" />
3.  Click on app.js to open it in the editor and note how the editor automatically assigns colors based on the inherent knowledge that the file contains JavaScript code.   
      
    On line 10, after the **var express** assignment, add the following text (including the period):   
      
    **express.**
4.  Note how the editor pops up a dialog with suggestions for completing the statement, and also includes text from and links to online documentation for the particular API.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-265.png" class="wp-image-1524" />   
      
    Without selecting any of the options presented, enter a single semicolon to finish the JavaScript statement.   
      
    **express.;**   
      
    Note how the editor intelligence marks the line as an error with a red X. Hovering the mouse pointer over the red X opens a dialog with details about the error.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-266.png" class="wp-image-1525" />   
      
      
    **Be sure to delete this line before continuing with the remainder of this lab!  
      
    **
5.  Select the public directory, then click on **File -> New -> File**. Name the new file "about.html". The editor automatically opens the new file for editing. Enter the following HTML code into the editor:   
      
    <html><body> All about me!</body></html>   
      
    Note now the editor automatically indents and highlights the code as you type it in.   
      
    It is not neccessary to save the file manually, as the editor will automatically save your changes after every change. You can manually force a save of a file by clicking on **File -> Save**.

3 - Deploy an Application to Bluemix from DevOps Services

1.  Locate the drop down dialog in the Bluemix runtime control area and click the down arrow, then click the pencil icon next to your app/project name.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-267.png" class="wp-image-1526" />
2.  In the Edit Launch Configuration dialog, enter a unique name in the Application Name and Host boxes. These names should match, and combined with the domain will create the Bluemix route through which you can access your running application. Click Save.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-268.png" class="wp-image-1527" />
3.  These configuration settings override the settings located in a file called manifest.yml. Open this file now in the editor, and overwrite the host: and name: parameters with the same unique name you set in the launch configuration dialog.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-269.png" class="wp-image-1528" />
4.  You are now ready to deploy the application to Bluemix. Click on the Play button in the Bluemix control pane.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-270.png" class="wp-image-1529" />
5.  The status bar will change to deploying, and after a few minutes will change to running. Click on the popout button to open the application in a new browser tab.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-271.png" class="wp-image-1530" />

4 - Using the Live Edit mode

 

1.  Close the application tab and return to the DevOps Services tab. Then click on the Live Edit toggle switch to enable live editing of the application.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-272.png" class="wp-image-1531" />
2.  Wait for your application to redeploy and click the pop out button again to open the application in a new browser tab.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-273.png" class="wp-image-1532" />   
    Live Edit allows you to rapidly make changes to your application code, and see those code changes without having to redeploy.
3.  Leave the application tab open, and return to the DevOps Services editor. Click on index.html and at the end of the <p> tag section, add the following two lines of code:   
      
    or use the Start Coding guide under your app in your dashboard.   
    <br />   
    <a href="about.html">About Me</a>   
    </table>
4.  Click on the restart button in the Bluemix control pane to restart the node.js server, picking up your recent change to index.html. Note that the restart function takes only a second to complete. Switch to the application tab and refresh the page. Note the code change is now live.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-274.png" class="wp-image-1533" />

Exercise 5.3.5 - Explore the DevOps Services Debug Tools

1.  (Optional - the remaining steps in this lab require the Chrome browser to complete) Close the application tab and return to the DevOps Services editor. In the Bluemix control pane, click on the button to open the debug tools. When prompted, enter your IBM id credentials.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-275.png" class="wp-image-1534" />
2.  The IBM Bluemix Developer Console will open, and give you a status of your application. Click on the Open Shell button.   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-276.png" class="wp-image-1535" />   
    A new tab will open, giving you a shell prompt on the virtual machine running your application. From here, you can get interesting information about the status of your app and container using standard linux commands like free and top.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-277.png" class="wp-image-1536" />
3.  Close the tab and return to the IBM Bluemix Developer Console, then click on the Open Debugger button.

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-278.png" class="wp-image-1537" />   
A new tab will open, and after about a minute, a full debugger will appear. Inside the debugger, you can perform normal debug actions like setting breakpoints, setting watch expressions, viewing the call stack, and stepping through your code during runtime.   
  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-279.png" class="wp-image-1538" />

 [1]: http://hub.jazz.net/project/ecosysdevcnc/cdc-lab-5/overview