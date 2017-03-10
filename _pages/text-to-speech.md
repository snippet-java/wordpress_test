---
ID: 631
post_title: Text to Speech
author: snippet java
post_date: 2016-09-27 06:14:30
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/watsonjava/text-to-speech/
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
<img src="http://bluecloudnews.com/wp-content/uploads/2016/09/Text-to-speech.jpg" alt="text-to-speech" width="1047" height="366" class="alignnone size-full wp-image-526" /> </br></br> **How it Works** </br> Watson Text to Speech provides a REST API to synthesize speech audio from an input of plain text. Multiple voices, both male and female, are available across Brazilian Portuguese, English, French, German, Italian, Japanese, and Spanish. Once synthesized in real-time, the audio is streamed back to the client with minimal delay. The Text to Speech service now enables developers to control the pronunciation of specific words </br></br> **Intended use** </br> Anywhere there's a need to communicate using the spoken word, particularly assistance tools for the vision-impaired, reading-based education tools, or mobile applications. </br></br> **Your Input** </br> 
*   Brazilian Portuguese plain text
*   English plain text
*   French plain text
*   German plain text
*   Italian plain text
*   Japanese plain text
*   Spanish plain text</br> 

**Service Output** </br> 
*   Brazilian Portuguese speech (1 female voice)
*   US English speech (choose between 3 voices: 2 female, 1 male)
*   UK English speech (1 female voice)
*   French speech (1 female voice)
*   German speech (choose between 2 voices: 1 female, 1 male)
*   Japanese speech (1 female voice)
*   Italian speech (1 female voice)
*   Castilian Spanish speech (choose between 2 voices: 1 female, 1 male)
*   North American Spanish speech (1 female voice)</br></br> 

**Java code to Explore** [playground allow_anonymous="yes"] import java.util.List; import javax.servlet.annotation.WebServlet; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonObject; import com.google.gson.JsonParser; import com.ibm.watson.developer_cloud.text_to_speech.v1.TextToSpeech; import com.ibm.watson.developer_cloud.text_to_speech.v1.model.Voice; //After deployment go to the relative URI to test the functionality. //You would see a form to provide the input values. @WebServlet("/") public class Snippet extends SuperGluev2 { public String parameters = "{\"username\":\"\",\"password\":\"\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); TextToSpeech service = new TextToSpeech(); service.setUsernameAndPassword(myBean.get("username").getAsString(), myBean.get("password").getAsString()); List<Voice> voices = service.getVoices().execute(); JsonObject json = new JsonObject(); json.add("voice", parser.parse(voices.toString()).getAsJsonArray()); return json; } public static void main(String[] args) { Snippet myclass = new Snippet(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private static final long serialVersionUID = 1L; } [/playground]