---
ID: 3032
post_title: How to use JazzBot Advisor
author: snippet java
post_date: 2016-12-07 09:03:52
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/jazzbot/how-to-use-jazzbot-advisor/
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
Here is the guide to get you started on using the JazzBot Advisor:

*   To list the available Bots registered on catalog, run   
    [code langauge="javascript"]catalog list[/code]   
    
*   To register the advisor, run   
    [code langauge="javascript"]catalog register advisor[/code] or  
    [code langauge="javascript"]catalog register 1[/code]   
    
*   Next, you need to set the **book** that you want to use:   
    [code langauge="javascript"]advisor set book <BOOK_JSON_URL>[/code] for example:  
    [code langauge="javascript"]advisor set book http://nodered-reflect-laksri.mybluemix.net/transformFlow?flowId=c9dacf55.5e08[/code]   
    The **BOOK_JSON_URL** is a url that points to a JSON formatted state diagram.  
      
    
*   Then, to start the conversation, simply run:   
    [code langauge="javascript"]advisor start[/code] or just  
    [code langauge="javascript"]start[/code]   
    
*   To reply or response to the question / options given, simply reply with:   
    [code langauge="javascript"]advisor reply <YOUR_ANSWER>[/code] or  
    [code langauge="javascript"]reply <YOUR_ANSWER>[/code]   
    

### Screenshots:

<img src="https://bluecloudnews.com/wp-content/uploads/2016/12/advisor1.png" alt="" width="527" height="750" class="alignnone size-full wp-image-3043" />  
<img src="https://bluecloudnews.com/wp-content/uploads/2016/12/advisor2.png" alt="" width="527" height="750" class="alignnone size-full wp-image-3044" />  
<img src="https://bluecloudnews.com/wp-content/uploads/2016/12/advisor3.png" alt="" width="527" height="750" class="alignnone size-full wp-image-3045" />