---
ID: 714
post_title: Conversation
author: snippet java
post_date: 2016-09-29 07:55:34
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/watsonjava/conversation/
published: true
inkblot_webcomic_term_image:
  - ""
inkblot_webcomic_comments:
  - ""
inkblot_webcomic_order:
  - ""
inkblot_webcomic_image:
  - ""
inkblot_webcomic_group:
  - ""
inkblot_avatar:
  - "0"
---
<!-- Conversation-->

<img src="http://bluecloudnews.com/wp-content/uploads/2016/09/conversation2.jpg" alt="conversation" width="1063" height="303" class="alignnone size-full wp-image-715" /> </br></br> **How it Works** </br> IBM Watson Conversation Service lets you add conversational capabilities to your apps using Natural Language Understanding with conversational interaction flows and dialog scripting tools. No programming background is required to use the rich dialog scripting tools, so you can quickly build and train a chat bot or virtual agent for more powerful customer engagements. This early experimental version, introduces the new user interface and the ability to manage intents, which are the goals of a user's question. </br></br> **Intended use** </br> 
*   Create virtual agents and chat bots
*   Allow your users to control your application using natural language
*   Add state-of-the-art language & intent understanding
*   Add a chat bot to your website that automatically responds to your customers' most frequently asked questions
*   Allow customers to control your mobile app using natural language</br> 

**Your Input** </br> 
*   Text to a pre-trained model</br> 

**Service Output** </br> 
*   Intents ordered by confidence</br></br> 

**Java code to Explore** [playground allow_anonymous="yes" show_deploy="yes" height="1300"] import javax.servlet.annotation.WebServlet; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonArray; import com.google.gson.JsonObject; import com.google.gson.JsonParser; import com.ibm.watson.developer_cloud.conversation.v1.ConversationService; import com.ibm.watson.developer_cloud.conversation.v1.model.MessageRequest; import com.ibm.watson.developer_cloud.conversation.v1.model.MessageRequest.Builder; import com.ibm.watson.developer_cloud.conversation.v1.model.MessageResponse; @WebServlet("/") //After deployment go to the relative URI to test the functionality. //You would see a form to provide the input values. public class test extends SuperGluev2 { public String parameters = "{\"username\":\"ac00ef1a-5ad1-416c-b778-27953b982e13\",\"password\":\"nHMkzS2ShYYY\"," + "\"workspace_id\":\"6a95d1df-8f65-4249-a58b-b5c83e56f4e4\"," + "\"question1\":\"Hi Watson\",\"question2\":\"Turn on the wiper\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); ConversationService service = new ConversationService(ConversationService.VERSION_DATE_2016_07_11); service.setUsernameAndPassword(myBean.get("username").getAsString(), myBean.get("password").getAsString()); JsonArray messageArray = new JsonArray(); Builder builder = new MessageRequest.Builder(); MessageRequest messageReq = builder.inputText("").build(); MessageResponse response = service.message(myBean.get("workspace_id").getAsString(), messageReq).execute(); messageArray.add(response.getText().toString()); messageReq = builder.context(response.getContext()).inputText(myBean.get("question1").getAsString()).build(); response = service.message(myBean.get("workspace_id").getAsString(), messageReq).execute(); messageArray.add(response.getInputText()); messageArray.add(response.getText().toString()); messageReq = builder.context(response.getContext()).inputText(myBean.get("question2").getAsString()).build(); response = service.message(myBean.get("workspace_id").getAsString(), messageReq).execute(); messageArray.add(response.getInputText()); messageArray.add(response.getText().toString()); JsonObject messageJson = new JsonObject(); messageJson.add("Responses", messageArray); JsonObject json = parser.parse(messageJson.toString()).getAsJsonObject(); return json; } public static void main(String[] args) { test myclass = new test(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private static final long serialVersionUID = 1L; } [/playground]