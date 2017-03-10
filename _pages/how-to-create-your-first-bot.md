---
ID: 2565
post_title: How to create your first Bot (Java)
author: snippet java
post_date: 2016-11-17 07:32:04
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/jazzbot/how-to-create-your-first-bot/
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
To deploy your first Jazzhub App (Java), please click the "Deploy to Bluemix" button below. </br> [![Deploy to Bluemix][1]][2] </br> When you click the button, you are taken to Bluemix where you get a pick a name for your application at which point the platform takes over, grabs the code from this repository and gets it deployed. </br> During success deployment, browse to http://APP_NAME.mybluemix.net/reverse?text=hello, you should see result of the reversed string of "hello" 

**How it Works with Jazzbot?**

In the Jazzbot window (or browse to https://jazzbot.mybluemix.net), type command </br> 
*   bot register app1 http://APP_NAME.mybluemix.net - to register the above app to use in the jazzbot
*   app1 reverse TEXT - to get inputted TEXT in reverse order
*   app1 help - to get all available commands of this app

Other userful Bot command: </br> 
*   bot list - to list all registered apps in the bot
*   bot delete - to unregister the app from the bot
*   bot help - to list all available commands of the bot

**Customize your own App** Reverse Command [playground edit_mode="yes" show_deploy="yes" show_download="yes" show_run="yes" repo="jazzbot-reflect-java-app" filename="src/main/java/Reverse.java" height="710"][/playground] Help Command [playground edit_mode="yes" repo="jazzbot-reflect-java-app" filename="src/main/java/Help.java" height="560"][/playground] [floating_div_ps name="popup"]

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/jazzbot-reflect-java-app