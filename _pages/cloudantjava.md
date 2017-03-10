---
ID: 3526
post_title: CloudantJava
author: snippet java
post_date: 2016-10-21 03:24:56
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/services/cloudant/cloudantjava/
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
<!-- Cloudant - List single doc-->

<img src="http://bluecloudnews.com/wp-content/uploads/2016/09/ibm_cloudant_blue_x2.png" alt="ibm_cloudant_blue_x2" width="728" height="164" class="alignnone size-full wp-image-1751" /> **How it Works** IBM Cloudant is a NoSQL JSON document store that’s optimized for handling heavy workloads of concurrent reads and writes in the cloud; a workload that is typical of large, fast-growing web and mobile apps. You can use Cloudant as a fully-managed DBaaS running on public cloud platforms like IBM SoftLayer or via an on-premise version called Cloudant Local, that you can run yourself on any private, public, or hybrid cloud platform you choose. **Intended use** 
*   Social Healthcare App
*   Mobile Game App
*   Mobile News App
*   Personal Training and Fitness App

**Your Input** 
*   Database name
*   Document ID

**Service Output** 
*   The whole document with matched ID in JSON format

**Java code to Explore** [playground show_deploy="yes" height="1300"] import java.io.IOException; import java.io.InputStream; import java.net.MalformedURLException; import java.net.URL; import javax.servlet.annotation.WebServlet; import com.cloudant.client.api.ClientBuilder; import com.cloudant.client.api.CloudantClient; import com.cloudant.client.api.Database; import com.cloudant.client.org.lightcouch.NoDocumentException; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonObject; import com.google.gson.JsonParser; //After deployment go to the relative URI to test the functionality. //You would see a form to provide the input values. @WebServlet("/") public class Snippet extends SuperGluev2 { public String parameters = "{\"username\":\"313d6562-626e-4edc-855f-528c7bba73e3-bluemix\", " + "\"password\":\"38fdea42f285bd146e7a7d2baa15f91dc486dababd609a1c61e3b2a2452aa55a\", " + "\"dbName\":\"pet\", " + "\"docId\":\"Fri-Apr-15-08:58:52-UTC-2016\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); String result = "{\"output\": \"No result\"}"; try { CloudantClient client = ClientBuilder.url(new URL("https://" + myBean.get("username").getAsString() + ".cloudant.com")) .username(myBean.get("username").getAsString()) .password(myBean.get("password").getAsString()) .build(); //@param false - if database don't exist, dont create it Database db = client.database(myBean.get("dbName").getAsString(), false); //provide document id InputStream is = db.find(myBean.get("docId").getAsString()); int i; char c; String output = ""; while((i=is.read())!=-1) { c=(char)i; output += c; } //convert the document format to JSON format result = output; } catch (MalformedURLException e) { e.printStackTrace(); } catch (NoDocumentException e) { System.out.println("No Document found"); } catch (IOException e) { e.printStackTrace(); } JsonObject json = parser.parse(result).getAsJsonObject(); return json; } public static void main(String[] args) { Snippet myclass = new Snippet(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private static final long serialVersionUID = 1L; } [/playground]