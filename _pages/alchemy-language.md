---
ID: 593
post_title: Alchemy Language
author: snippet java
post_date: 2016-09-27 02:51:35
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/watsonjava/alchemy-language/
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
<img src="http://bluecloudnews.com/wp-content/uploads/2016/09/alchemy-lang.jpg" alt="alchemy-lang" class="alignnone size-full wp-image-492" /> </br></br> **How it Works** </br> AlchemyLanguage offers several API functions as part of its text analysis service, each of which uses sophisticated natural language processing techniques to analyze your content. Note: The Emotion Analysis Beta will end on July 1st, 2016. On that date, all users will start to be charged per event for the Emotion Analysis API. </br></br> **Intended use** </br> Use one or all of the natural language processing APIs available through AlchemyLanguage to add high-level semantic information. Browse the documentation to learn more about each of AlchemyAPI's text analysis service functions: 
*   Entity Extraction
*   Sentiment Analysis
*   Emotion Analysis (Beta)
*   Keyword Extraction
*   Concept Tagging
*   Relation Extraction
*   Taxonomy Classification
*   Author Extraction
*   Language Detection
*   Text Extraction
*   Microformats Parsing
*   Feed Detection
*   Linked Data Support</br> 

**Your Input** </br> 
*   Any publicly-accessible webpage or posted HTML/text document.</br> 

**Service Output** </br> 
*   Extracted meta-data including, entities, sentiment, keywords, concepts, relations, authors, and more, returned in XML, JSON, and RDF formats.</br></br> 

**Java code to Explore** [playground allow_anonymous="yes" show_download="yes" height="1000"] import java.util.HashMap; import java.util.Map; import javax.servlet.annotation.WebServlet; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonObject; import com.google.gson.JsonParser; import com.ibm.watson.developer_cloud.alchemy.v1.AlchemyLanguage; import com.ibm.watson.developer_cloud.alchemy.v1.model.DocumentSentiment; //After deployment go to the relative URI to test the functionality. //You would see a form to provide the input values. @WebServlet("/") public class Snippet extends SuperGluev2 { public String parameters = "{\"apiKey\":\"\", \"text\":\"IBM Watson won the Jeopardy television show hosted by Alex Trebek\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); AlchemyLanguage service = new AlchemyLanguage(); service.setApiKey(myBean.get("apiKey").getAsString()); Map<String, Object> params = new HashMap<String, Object>(); params.put(AlchemyLanguage.TEXT, (myBean.get("text").getAsString())); DocumentSentiment sentiment = service.getSentiment(params).execute(); JsonObject json = parser.parse(sentiment.toString()).getAsJsonObject(); return json; } public static void main(String[] args) { Snippet myclass = new Snippet(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private static final long serialVersionUID = 1L; } [/playground]