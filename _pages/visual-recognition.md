---
ID: 642
post_title: Visual Recognition
author: snippet java
post_date: 2016-09-27 06:20:14
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/watsonjava/visual-recognition/
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
<img src="https://bluecloudnews.com/wp-content/uploads/2016/09/visual-recog2.jpg" alt="" width="853" height="250" class="alignnone size-full wp-image-3179" /> </br></br> **How it Works** </br> Visual Recognition understands the contents of images - it's learned over 20,000 visual concepts including faces, age and gender. You can also train the service by creating your own custom concepts. Use Visual Recognition to detect a dress type in retail, identify spoiled fruit in inventory, and more. </br></br> **Intended use** </br> Need to figure out what is contained in many images, but don’t have the man-power to manually go one-by-one? 
*   Organize image libraries into categories
*   Segment user interests from social media pictures
*   Find great images with specific content faster
*   Recognize custom content from images
*   Identify matching images</br> 

**Your Input** </br> 
*   JPEG images
*   PNG images
*   Image or website URLs
*   Custom: Classifier name, JPEG images (positive examples for each class, and negative examples)
*   Custom: Collections - your own images that you want to search for similar images</br> 

**Service Output** </br> 
*   Class description
*   Class taxonomy
*   Face detection (Gender, age range, celebrity (very limited see docs))
*   Similar images with confidence scores</br></br> 

**Java code to Explore** [playground allow_anonymous="yes" show_download="yes" height="1150"] import java.io.File; import java.io.IOException; import java.net.URL; import java.net.URLConnection; import javax.servlet.annotation.WebServlet; import org.apache.commons.io.FileUtils; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonObject; import com.google.gson.JsonParser; import com.ibm.watson.developer_cloud.visual_recognition.v3.VisualRecognition; import com.ibm.watson.developer_cloud.visual_recognition.v3.model.DetectedFaces; import com.ibm.watson.developer_cloud.visual_recognition.v3.model.VisualRecognitionOptions; @WebServlet("/") public class Snippet extends SuperGluev2 { public String parameters = "{\"apiKey\":\"cf8ff9af4fd5323e190b6df6b730ab4919464c73\",\"url\":\"https://www.whitehouse.gov/sites/whitehouse.gov/files/images/first-family/44_barack_obama%5B1%5D.jpg\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); VisualRecognition service = new VisualRecognition(VisualRecognition.VERSION_DATE_2016_05_20); service.setApiKey(myBean.get("apiKey").getAsString()); File fileA = new File("test.jpg"); URL url = null; try { url = new URL(myBean.get("url").getAsString()); URLConnection conn = url.openConnection(); conn.setRequestProperty("User-Agent", "NING/1.0"); FileUtils.copyInputStreamToFile(conn.getInputStream(), fileA); } catch (IOException e) { e.printStackTrace(); } VisualRecognitionOptions voptoins = new VisualRecognitionOptions.Builder().images(fileA).build(); DetectedFaces result = service.detectFaces(voptoins).execute(); JsonObject json = parser.parse(result.toString()).getAsJsonObject(); return json; } public static void main(String[] args) { Snippet myclass = new Snippet(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private static final long serialVersionUID = 1L; } [/playground]