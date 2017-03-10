---
ID: 3184
post_title: Natural Language Classifier
author: snippet java
post_date: 2017-01-11 08:23:02
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/watsonjava/natural-language-classifier/
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
<img src="https://bluecloudnews.com/wp-content/uploads/2017/01/natural-lang-class.jpg" alt="" width="982" height="232" class="alignnone size-full wp-image-3185" /> </br></br> **How it Works** </br> The Natural Language Classifier service understands the intent behind text and returns a corresponding classification, complete with a confidence score. For example “What is the weather like today? or “Is it hot out?” or “Is it going to be nice today?” are all ways of asking about “temperature”. Use NLC to answer questions in a contact center, create chatbots, categorize volumes of written content and more. </br></br> **Intended use** </br> The Natural Language Classifier works best with short text (1000 characters or less) and can be trained to function in any domain or application. Use Natural Language Classifier to perform tasks such as: 
*   Classify SMS texts as personal, work, or promotional
*   Classify tweets into a set of classes, such as events, news, or opinions
*   Tackle common questions from your users that are typically handled by a live agent
*   Trigger actions in an application, such as start another application, respond with an answer, or begin a dialog</br> 

**Your Input** </br> 
*   Text to a pre-trained model</br> 

**Service Output** </br> 
*   Classes ordered by confidence</br></br> 

**Java code to Explore** [playground allow_anonymous="yes" show_download="yes" height="1150"] import javax.servlet.annotation.WebServlet; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonObject; import com.google.gson.JsonParser; import com.ibm.watson.developer_cloud.natural_language_classifier.v1.NaturalLanguageClassifier; import com.ibm.watson.developer_cloud.natural_language_classifier.v1.model.Classification; @WebServlet("/") public class Snippet extends SuperGluev2 { public String parameters = "{\"username\":\"1e2a85d3-f9f3-4d77-9b44-d0d56c93a028\",\"password\":\"EjhIkxAUWWVQ\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); NaturalLanguageClassifier service = new NaturalLanguageClassifier(); service.setUsernameAndPassword(myBean.get("username").getAsString(), myBean.get("password").getAsString()); Classification result = service.classify("ff18c7x157-nlc-2810", "Is it sunny?").execute(); System.out.println(result); JsonObject json = parser.parse(result.toString()).getAsJsonObject(); return json; } public static void main(String[] args) { Snippet myclass = new Snippet(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private static final long serialVersionUID = 1L; } [/playground]