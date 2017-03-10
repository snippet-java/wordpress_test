---
ID: 614
post_title: Language Translator
author: snippet java
post_date: 2016-09-27 05:55:47
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/watsonjava/language-translator/
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
<img src="https://bluecloudnews.com/wp-content/uploads/2016/09/lang-translator.jpg" alt="lang-translation" width="1054" height="256" class="alignnone size-full wp-image-524" /> </br></br> **How it Works** </br> Language Translator uses statistical machine translation to translate text from one language to another. The service offers multiple domain-specific models that you can customize based on your unique terminology and language. Use Language Translator to take news from across the globe and present it in your language, communicate with your customers in their own language, and more. </br></br> **Intended use** </br> Use Language Translator in any application that can benefit from real-time, domain-specific translation abilities such as: 
*   Enable an English-speaking help desk representative to assist a Spanish-speaking customer through chat
*   A French news website can source news from across the globe and present it to users in their chosen language
*   Translate product descriptions from English to Arabic using a custom model tailored to a specific bank's product names and terminology
*   A US patent attorney can effectively discover prior art based on invention disclosures made in Korean with the Korean Patent Office</br></br> 

**Your Input** </br> 
*   Plain text in one of the supported input languages and domains</br> 

**Service Output** </br> 
*   Plain text in the target language selected</br></br> 

**Java code to Explore** [playground allow_anonymous="yes" show_deploy="yes" height="1100"] // LanguageTranslationTest //Select a domain, then identify or select the language of text, and then translate the text from one supported language to another. //Example: Translate 'hello my friend' from English to Spanish using the Language Translation service. import javax.servlet.annotation.WebServlet; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonObject; import com.google.gson.JsonParser; import com.ibm.watson.developer_cloud.language_translator.v2.LanguageTranslator; import com.ibm.watson.developer_cloud.language_translator.v2.model.Language; import com.ibm.watson.developer_cloud.language_translator.v2.model.TranslationResult; //After deployment go to the relative URI to test the functionality. //You would see a form to provide the input values. @WebServlet("/") public class Snippet extends SuperGluev2 { public String parameters = "{\"username\":\"\",\"password\":\"\",\"text\":\"hello my friend\",\"fromLanguage\":\"ENGLISH\",\"toLanguage\":\"SPANISH\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); // LanguageTranslation service = new LanguageTranslation(); LanguageTranslator service = new LanguageTranslator(); service.setUsernameAndPassword(myBean.get("username").getAsString(), myBean.get("password").getAsString()); //fromlanguage and tolanguage arg need to be upper case TranslationResult translationResult = service.translate(myBean.get("text").getAsString(), Language.valueOf(myBean.get("fromLanguage").getAsString().toUpperCase()), Language.valueOf(myBean.get("toLanguage").getAsString().toUpperCase())).execute(); JsonObject json = parser.parse(translationResult.toString()).getAsJsonObject(); return json; } public static void main(String[] args) { Snippet myclass = new Snippet(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private static final long serialVersionUID = 1L; } [/playground]