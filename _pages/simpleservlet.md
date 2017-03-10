---
ID: 2671
post_title: Simple Java Servlet
author: snippet java
post_date: 2016-11-20 01:26:30
post_excerpt: ""
layout: page
permalink: http://watsonbeach.com/simpleservlet/
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
**Bluemix Java Application – Overview** 

This Java App is app is a simple Servlet or Web Application responsing to a browser request. 

**Bluemix Java Application – SimpleServlet.java Code Walkthrough** 

1.  The @WebServlet annotation is used to declare a servlet. Here the URI pattern / is used for the servlet. 
2.  The / URI GET invocation will trigger doGet(…) method. This method responds with a simple HTML text.  [su_divider] 

### Files in the Application (Edit, Save and Deploy you own version)

**manifest.yml:** Deployment settings</br> [playground edit_mode="yes" repo="Java_Intro_Ex1_SimpleHTTPServlet" filename="manifest.yml" height="220"] </br> **SimpleServlet.java:** Java servlet</br> </br> [playground edit_mode="yes" show_deploy="yes" repo="Java_Intro_Ex1_SimpleHTTPServlet" filename="src/main/java/com/ibm/sample/SimpleServlet.java" height="650"]