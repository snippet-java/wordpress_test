---
ID: 629
post_title: Speech To Text
author: snippet java
post_date: 2016-09-27 06:12:52
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/watsonjava/speech-to-text/
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
<img src="https://bluecloudnews.com/wp-content/uploads/2016/09/speech-to-text2.jpg" alt="" width="712" height="232" class="alignnone size-full wp-image-3174" /> </br></br> **How it Works** </br> Watson Speech to Text can be used anywhere there is a need to bridge the gap between the spoken word and its written form. This easy-to-use service uses machine intelligence to combine information about grammar and language structure with knowledge of the composition of an audio signal to generate an accurate transcription. It uses IBM's speech recognition capabilities to convert speech in multiple languages into text. The transcription of incoming audio is continuously sent back to the client with minimal delay, and it is corrected as more speech is heard. Additionally, the service now includes the ability to detect one or more keywords in the audio stream. The service is accessed via a WebSocket connection or REST API. </br></br> **Intended use** </br> The Speech to Text service can be used anywhere voice-interactivity is needed. In addition to transcribing audio in multiple languages, the service provides the ability to detect the presence of specific keywords or key phrases in the input stream. Common uses for the Speech to Text service include: 
*   Interactions in mobile experiences
*   Transcribing media files
*   Call center transcriptions
*   Voice control of embedded systems
*   Converting sound to text to make data searchable</br></br> 

**Your Input** </br> 
*   Streamed audio with Intelligible Speech
*   Recorded audio with Intelligible Speech</br> 

**Service Output** </br> 
*   Text transcriptions of the audio with recognized words</br></br> 

Sample audio [audio wav="https://bluecloudnews.com/wp-content/uploads/2016/09/STTInput.wav"][/audio] </br> 

**Java code to Explore** [playground allow_anonymous="yes"] // SpeechToTextTest //to recognize the text from a .wav file. import java.io.File; import java.util.Collection; import java.util.Iterator; import javax.servlet.annotation.WebServlet; import org.apache.commons.io.FileUtils; import com.google.gson.Gson; import com.google.gson.GsonBuilder; import com.google.gson.JsonObject; import com.google.gson.JsonParser; import com.ibm.watson.developer_cloud.speech_to_text.v1.SpeechToText; import com.ibm.watson.developer_cloud.speech_to_text.v1.model.SpeechResults; //After deployment go to the relative URI to test the functionality. //You would see a form to provide the input values. @WebServlet("/") public class Snippet extends SuperGluev2 { public class Parameters { public String userName = ""; public String password = ""; } public String parameters = "{\"username\":\"\",\"password\":\"\"}"; @Override protected JsonObject process(String jsonString) { JsonParser parser = new JsonParser(); JsonObject myBean = parser.parse(jsonString).getAsJsonObject(); SpeechToText service = new SpeechToText(); service.setUsernameAndPassword(myBean.get("username").getAsString(), myBean.get("password").getAsString()); File audio = findFile(); SpeechResults transcript = service.recognize(audio).execute(); JsonObject json = parser.parse(transcript.toString()).getAsJsonObject(); return json; } public static void main(String[] args) { Snippet myclass = new Snippet(); //****** Process method contains the key logic ****** JsonObject processResult = myclass.process(myclass.parameters); Gson gson = new GsonBuilder().setPrettyPrinting().create(); System.out.println(gson.toJson(processResult)); } @Override JsonObject getParameters() { return new JsonParser().parse(parameters).getAsJsonObject(); } private File findFile() { File root = new File(System.getProperty("user.dir")); String fileName = "STTInput.wav"; File sourceFile = null; try { boolean recursive = true; Collection files = FileUtils.listFiles(root, new String[] {"wav"}, recursive); for (Iterator iterator = files.iterator(); iterator.hasNext();) { File file = (File) iterator.next(); if (file.getName().equals(fileName)) { sourceFile = new File(file.getAbsolutePath()); break; } } } catch (Exception e) { e.printStackTrace(); } return sourceFile; } private static final long serialVersionUID = 1L; } [/playground]