---
ID: 2735
post_title: >
  How to create Bot for 3rd Party Sendgrid
  Email Service (Java)
author: snippet java
post_date: 2016-11-21 12:57:36
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/jazzbot/sendgridjava/
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
## Overview This app acts as the backend for Jazz Bot. Once this app is deployed and registered with jazz bot , an email can be sent from the bot with just a few commands. 

  
  
[ ![Deploy to Bluemix][1] ][2]   
  
When you click the button, you are taken to Bluemix where you get a pick a name for your application at which point the platform takes over, grabs the code from this repository and gets it deployed. 
### How it Works with Jazzbot? In the Jazzbot window (or browse to 

<https://jazzbot.mybluemix.net>), type command 
1.  Register the bluemix app with bot. [code langauge="javascript"]bot register app http://<APP_NAME>.mybluemix.net[/code] 
2.  Provide credentials of Sendgrid API. You can sign up for free tier at [sendgrid][3] [code langauge="javascript"] app set apikey <YOUR_SENDGRID_APIKEY> [/code] 
3.  Enter the destination email [code langauge="javascript"]app set toemail <TO_EMAIL>[/code] 
4.  Enter the source email [code langauge="javascript"]app set fromemail <FROM_EMAIL>[/code] 
5.  Enter the optional cc email [code langauge="javascript"]app set ccemail <CC_EMAIL>[/code] 
6.  Enter the optional cc email [code langauge="javascript"]app set bccemail <BCC_EMAIL>[/code] 
7.  Enter the optional cc email [code langauge="javascript"]app mail<MAIL_MESSAGE>[/code] 

### Demo: 

### Other useful commands: 

` help` : To view all the commands available for that bot   
`bot list` : to list all registered apps in the bot   
`bot delete` – to unregister the app from the bot   
`bot help` – to list all available commands of the bot 
### Customize your own App [playground edit_mode="yes" show_deploy="yes" show_download="yes" show_run="yes" repo="jazzbot-watson-sendgrid" filename="src/main/java/Mail.java" height="900"] [playground edit_mode="yes" show_deploy="yes" show_download="yes" show_run="yes" repo="jazzbot-watson-sendgrid" filename="src/main/java/Help.java" height="700"]

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/jazzbot-watson-sendgrid
 [3]: https://sendgrid.com/