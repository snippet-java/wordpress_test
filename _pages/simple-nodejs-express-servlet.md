---
ID: 3532
post_title: Simple NodeJS Express Servlet
author: snippet java
post_date: 2017-01-11 12:57:23
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/microservices/simple-nodejs-express-servlet/
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
**Bluemix NodeJS Express Application – Overview** 

This NodeJS Express app is a simple Servlet or Web Application responsing to a browser request. 

**Bluemix NodeJS EXpress Application – app.js Code Walkthrough** 

1.  The @WebServlet annotation is used to declare a servlet. Here the URI pattern / is used for the servlet. 
2.  The / URI GET invocation will trigger doGet(…) method. This method responds with a simple HTML text.  [su_divider] 

### Files in the Application (Edit, Save and Deploy you own version)

**manifest.yml:** Deployment settings</br> [playground edit_mode="yes" repo="NodeJS_Intro_Ex2_Expressjs" filename="manifest.yml" height="220"] </br> **app.js:** Java servlet</br> </br> [playground edit_mode="yes" show_deploy="yes" repo="NodeJS_Intro_Ex2_Expressjs" filename="app.js" height="650"]