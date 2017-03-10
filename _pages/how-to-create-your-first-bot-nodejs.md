---
ID: 2596
post_title: How to create your first Bot (NodeJS)
author: snippet java
post_date: 2016-11-18 06:41:37
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/jazzbot/how-to-create-your-first-bot-nodejs/
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
</br> When you click the button, you are taken to Bluemix where you get a pick a name for your application at which point the platform takes over, grabs the code from this repository and gets it deployed. </br> During success deployment, browse to http://APP_NAME.mybluemix.net/reverse?text=hello, you should see result of the reversed string of "hello" </p> 
To deploy your first Jazzhub App (NodeJS), please click the "Deploy to Bluemix" button below. </br> [![Deploy to Bluemix][1]][2] 
**How it Works with Jazzbot?**

In the Jazzbot window (or browse to https://jazzbot.mybluemix.net), type command </br> 
*   bot register app1 http://APP_NAME.mybluemix.net - to register the APP as BOT
*   app1 <function_you_implmented> TEXT - to get respons
*   app1 help - to get all available commands of this app



**Create your own Bot and Deploy in one click on Bluemix** [playground edit_mode="yes" show_deploy="yes" show_download="yes" show_run="yes" allow_anonymous="yes" repo="jazzbot-reflect-nodejs-app" filename="index.js" height="510"][/playground]

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/jazzbot-reflect-nodejs-app