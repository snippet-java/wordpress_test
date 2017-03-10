---
ID: 2704
post_title: >
  How to create Bot with Watson
  Translation (Java)
author: snippet java
post_date: 2016-11-21 09:20:35
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/jazzbot/how-to-create-bot-with-watson-translation-java/
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
To deploy your bot with Watson Translation (Java), please click the "Deploy to Bluemix" button below. </br> [![Deploy to Bluemix][1]][2] </br> When you click the button, you are taken to Bluemix where you get a pick a name for your application at which point the platform takes over, grabs the code from this repository and gets it deployed. </br> During success deployment, follow 2 steps to translate a text from Preferred Language to another language (Supported Language: English, Spanish, French, Italian, Portuguese): 
1.  Set the language to translate from and to - Browse to http://APP_NAME.mybluemix.net/set?sessionId=ANY_ID&from=LANGUAGE&to=LANGUAGE
2.  Translate the text - Browse to http://APP_NAME.mybluemix.net/translate?sessionId=ANY_ID&text=ANY_TEXT

**How it Works with Jazzbot?**

In the Jazzbot window (or browse to https://jazzbot.mybluemix.net), type command </br> 
*   bot register app1 http://APP_NAME.mybluemix.net - to register the above app to use in the jazzbot
*   app1 set from LANGUAGE - to set language to translate from
*   app1 set to LANGUAGE - to set language to translate to
*   app1 translate TEXT - to return translated TEXT from and to Language set above
*   app1 help - to get all available commands of this app

Other userful Bot command: </br> 
*   bot list - to list all registered apps in the bot
*   bot delete - to unregister the app from the bot
*   bot help - to list all available commands of the bot

**Customize your own App** Detect Face [playground edit_mode="yes" show_deploy="yes" show_download="yes" show_run="yes" repo="jazzbot-watson-translate-app" filename="src/main/java/Translate.java" height="1550"][/playground] [floating_div_ps name="popup"]

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/jazzbot-watson-translate-app