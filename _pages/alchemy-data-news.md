---
ID: 3522
post_title: Alchemy Data News
author: snippet java
post_date: 2016-09-27 01:24:03
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/watsonjava/alchemy-data-news/
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
<!-- Alchemy Data News-->

<img src="http://bluecloudnews.com/wp-content/uploads/2016/09/alchemy-data-news2.jpg" alt="alchemy-data-news" class="alignnone size-full wp-image-490" /> </br></br> **How it Works** </br> AlchemyData News indexes 250k to 300k English language news and blog articles every day with historical search available for the past 60 days. You can query the News API directly with no need to acquire, enrich and store the data yourself - enabling you to go beyond simple keyword-based searches. </br></br> **Intended use** </br> Highly targeted search, time series and counts for trend analysis and pattern mapping, and historical access to news and blog content. </br></br> **Your Input** </br> 
*   Build a query with natural language processing to search both the text in indexed content and the concepts that are associated with it.</br> 

**Service Output** </br> 
*   News and blog content enriched with our full suite of NLP services.
*   Keywords, Entities, Concepts, Relations, Sentiment, Taxonomy</br></br> 

**Java code to Explore** [playground allow_anonymous="yes"] import java.util.HashMap; import java.util.Map; import javax.servlet.annotation.WebServlet; import org.apache.commons.lang3.StringUtils; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonObject; import com.google.gson.JsonParser; import com.ibm.watson.developer_cloud.alchemy.v1.AlchemyDataNews; import com.ibm.watson.developer_cloud.alchemy.v1.model.DocumentsResult; //After deployment go to the relative URI to test the functionality. //You would see a form to provide the input values. @WebServlet("/") public class Snippet extends SuperGluev2 { public String parameters = "{\"apiKey\":\"\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); AlchemyDataNews service = new AlchemyDataNews(); service.setApiKey(myBean.get("apiKey").getAsString()); Map<String, Object> params = new HashMap<String, Object>(); // specify the categories to be included. In this case, title, url,author... are included String[] fields = new String[] { "enriched.url.title", "enriched.url.url", "enriched.url.author", "enriched.url.publicationDate", "enriched.url.enrichedTitle.entities", "enriched.url.enrichedTitle.docSentiment" }; params.put(AlchemyDataNews.RETURN, StringUtils.join(fields, ",")); // the time (in UTC seconds) of the beginning of the query duration params.put(AlchemyDataNews.START, "1440720000"); // the time (in UTC seconds) of the end of the query duration params.put(AlchemyDataNews.END, "1441407600"); // return how many articles params.put(AlchemyDataNews.COUNT, 7); DocumentsResult result = service.getNewsDocuments(params).execute(); JsonObject json = parser.parse(result.toString()).getAsJsonObject(); return json; } public static void main(String[] args) { Snippet myclass = new Snippet(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private static final long serialVersionUID = 1L; } [/playground]