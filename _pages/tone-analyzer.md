---
ID: 633
post_title: Tone Analyzer
author: snippet java
post_date: 2016-09-27 06:15:52
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/watsonjava/tone-analyzer/
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
<img src="http://bluecloudnews.com/wp-content/uploads/2016/09/tone-analyzer.jpg" alt="tone-analyzer" width="1049" height="251" class="alignnone size-full wp-image-523" /> </br></br> **How it Works** </br> Wonder how your message might be perceived by the end user? Perhaps a bit too angry in your emails? Tone Analyzer can help. The IBM Watson™ Tone Analyzer Service uses linguistic analysis to detect three types of tones from text: emotion, social tendencies, and language style. Emotions identified include things like anger, fear, joy, sadness, and disgust. Identified social tendencies include things from the Big Five personality traits used by some psychologists. These include openness, conscientiousness, extroversion, agreeableness, and emotional range. Identified language styles include confident, analytical, and tentative. </br></br> **Intended use** </br> Common uses for the Tone Analyzer service include: 
*   Personal and business communications - Anyone could use the Tone Analyzer service to get feedback about their communications, which could improve the effectiveness of the messages and how they are received.
*   Message resonance - optimize the tones in your communication to increase the impact on your audience
*   Digital Virtual Agent for customer care - If a human client is interacting with an automated digital agent, and the client is agitated or angry, it is likely reflected in the choice of words they use to explain their problem. An automated agent could use the Tone Analyzer Service to detect those tones, and be programmed to respond appropriately to them
*   Self-branding - Bloggers and journalists could use the Tone Analyzer Service to get feedback on their tone and fine-tune their writing to reflect a specific personality or style
*   Market research - Financial advisors and investors could use the Tone Analyzer service to look at the tones reflected in announcements and reports from the companies that they are researching and investing in</br> 

**Your Input** </br> 
*   Any text</br> 

**Service Output** </br> 
*   JSON that provides a hierarchical representation of the analysis of the terms in the input message</br></br> 

**Java code to Explore** [playground allow_anonymous="yes" show_download="yes" height="1100"] import javax.servlet.annotation.WebServlet; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonObject; import com.google.gson.JsonParser; import com.ibm.watson.developer_cloud.tone_analyzer.v3.ToneAnalyzer; import com.ibm.watson.developer_cloud.tone_analyzer.v3.model.ToneAnalysis; @WebServlet("/") public class Snippet extends SuperGluev2 { public String parameters = "{\"username\":\"\",\"password\":\"\"," + "\"text\":\"I know the times are difficult! Our sales have been " + "disappointing for the past three quarters for our data analytics " + "product suite. We have a competitive data analytics product " + "suite in the industry. But we need to do our job selling it! " + "We need to acknowledge and fix our sales challenges. " + "We can't blame the economy for our lack of execution! " + "We are missing critical sales opportunities. " + "Our product is in no way inferior to the competitor products. " + "Our clients are hungry for analytical tools to improve their " + "business outcomes. Economy has nothing to do with it.\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); ToneAnalyzer service = new ToneAnalyzer(ToneAnalyzer.VERSION_DATE_2016_05_19); service.setUsernameAndPassword(myBean.get("username").getAsString(), myBean.get("password").getAsString()); // Call the service and get the tone ToneAnalysis tone = service.getTone(myBean.get("text").getAsString(), null).execute(); JsonObject json = parser.parse(tone.toString()).getAsJsonObject(); return json; } public static void main(String[] args) { Snippet myclass = new Snippet(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private static final long serialVersionUID = 1L; } [/playground]