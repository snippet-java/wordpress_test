---
ID: 2701
post_title: >
  How to create Bot with Watson Visual
  Recognition (Java)
author: snippet java
post_date: 2016-11-21 09:00:12
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/jazzbot/how-to-create-bot-with-watson-visual-recognition-java/
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
To deploy your bot with Watson Visual Recognition (Java), please click the "Deploy to Bluemix" button below. </br> [![Deploy to Bluemix][1]][2] </br> When you click the button, you are taken to Bluemix where you get a pick a name for your application at which point the platform takes over, grabs the code from this repository and gets it deployed. </br> During success deployment, browse to http://APP_NAME.mybluemix.net/detectface?text=IMAGE_URL, you should see result of identified person in the IMAGE_URL 

**How it Works with Jazzbot?**

In the Jazzbot window (or browse to https://jazzbot.mybluemix.net), type command </br> 
*   bot register app1 http://APP_NAME.mybluemix.net - to register the above app to use in the jazzbot
*   app1 detectface - to analyze the picture and return the result of name, gender and age
*   app1 help - to get all available commands of this app

Other userful Bot command: </br> 
*   bot list - to list all registered apps in the bot
*   bot delete - to unregister the app from the bot
*   bot help - to list all available commands of the bot

**Try it yourself** Detect Face [playground edit_mode="yes" show_deploy="yes" show_download="yes" show_run="yes" repo="jazzbot-watson-visual-recog-app" filename="src/main/java/DetectFace.java" height="1650"][/playground] [floating_div_ps name="popup"]

 [1]: https://bluemix.net/deploy/button.png
 [2]: https://bluemix.net/deploy?repository=https://github.com/snippet-java/jazzbot-watson-visual-recog-app