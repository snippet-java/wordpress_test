---
ID: 2410
post_title: Watson Services
author: snippet java
post_date: 2016-11-04 15:40:05
post_excerpt: ""
layout: page
permalink: http://watsonbeach.com/watson-services/
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
**WATSON INTRODUCTION**

**What can Alchemy do for you?**

*   Quickly extract meaningful information from unstructured data
*   Categorize and label text and images
*   Analyze sentiment
*   Connect your data to additional knowledge sources

**Our most popular APIS**

*   AlchemyLanguage
    *   Named Entity Extraction
    *   Sentiment Analysis
    *   Keyword Extraction
    *   Relations Extraction
    *   Taxonomy
*   AlchemyData
    *   News

**Named Entity Extraction**

Extract people, places, organizations, etc. from blogs, news articles and other text.

Example:   
*1) ****President Obama**** works at the ****White House****  
* Output: 3 entities identified:   
a) Person – Obama   
b) Facility – White House   
c) JobTitle – President   
See it yourself: [http://access.alchemyapi.com/calls/text/TextGetRankedNamedEntities?sentiment=1&apikey=<api_key>&outputMode=json&text=President%20Obama%20works%20at%20the%20White%20House][1]   
(*replace the api_key with authorized Alchmey API key)*

*2) ****Zach Walchuk**** was born in ****Mankato****, ****MN**** and lives in the white house down the street  
* Output: 3 entities identified:   
a) Person – Zach Walchuk   
b) City – Mankato   
c) StateOrCounty – MN   
See it yourself:   
[http://access.alchemyapi.com/calls/text/TextGetRankedNamedEntities?apikey=<api_key>&outputMode=json&text=Zach%20Walchuk%20was%20born%20in%20Mankato,%20MN%20and%20lives%20in%20the%20white%20house%20down%20the%20street][2]   
(*replace the api_key with authorized Alchmey API key)*

*3) Text from website URL e.g. *[*http://www.automatedtrader.net/news/at/153105/fidelity-investments-acquires-emoney-advisor*][3]*  
* Output: Multiple entities identified   
See it yourself:   
[http://access.alchemyapi.com/calls/url/URLGetRankedNamedEntities?apikey=<api_key>&showSourceText=1&outputMode=json&url=http://www.automatedtrader.net/news/at/153105/fidelity-investments-acquires-emoney-advisor][4]   
(*replace the api_key with authorized Alchmey API key)*

**What is an Entity?**

It could be

<img src="http://bluecloudnews.com/wp-content/uploads/2016/11/person-entity.jpg" alt="person-entity" width="625" height="391" class="alignnone size-full wp-image-2443" />

<img src="http://bluecloudnews.com/wp-content/uploads/2016/11/company-entity.jpg" alt="company-entity" width="625" height="377" class="alignnone size-full wp-image-2442" />

<img src="http://bluecloudnews.com/wp-content/uploads/2016/11/word-image-71.png" class="wp-image-2437" />

<img src="http://bluecloudnews.com/wp-content/uploads/2016/11/word-image-72.png" class="wp-image-2438" />

**Sentiment Analysis**

Identifies attitude, opinions, or feelings in the content that is being analyzed

Example:

*1) Overall Text Sentiment - So happy the Patriots won the Super Bowl. Let's party. #PatriotsParade  
* Output: Positive   
See it yourself:   
[http://access.alchemyapi.com/calls/text/TextGetTextSentiment?apikey=<api_key>&outputMode=json&text=So%20happy%20the%20Patriots%20won%20the%20Super%20Bowl.%20Let%E2%80%99s%20party!#PatriotsParade][5]   
(*replace the api_key with authorized Alchmey API key)*

*2) Targeted Sentiment - So happy the Patriots won the Super Bowl ****Seahawks**** suck. #BradyBunch  
* Output: Negative   
See it yourself:   
[http://access.alchemyapi.com/calls/text/TextGetTargetedSentiment?apikey=<api_key>&outputMode=json&text=So%20happy%20the%20Patriots%20won%20the%20Super%20Bowl.%20Seahawks%20suck.&target=seahawks][6]   
(*replace the api_key with authorized Alchmey API key)*

**Keyword Extraction**

Extract topic keywords, with higher level abstractions via Knowledge Graph

Example:   
*1) The New England Patriots raised the Lombardi Trophy over the city of Boston on Wednesday  
* Output: Keywords with its type hierarchy extracted   
a) New England Patriots - /teams/   
b) Lombardi trophy - /activities/honors/awards/trophies/   
c) Wednesday - /times/days/   
d) city - /places/   
e) Boston - /places/cities/   
See it yourself:   
[http://access.alchemyapi.com/calls/text/TextGetRankedKeywords?apikey=<api_key>&knowledgeGraph=1&showSourceText=1&outputMode=json&text=The%20New%20England%20Patriots%20raised%20the%20lombardi%20trophy%20high%20over%20the%20city%20of%20Boston%20Wednesday][7]   
*(replace the api_key with authorized Alchmey API key)*

*2) Keyword Extraction from Website URL e.g http://www.wired.com/2015/02/the-upside-of-artificial-intelligence-development/  
* Output: Multiple keywords with type hierarchy extracted   
See it yourself:   
[http://access.alchemyapi.com/calls/url/URLGetRankedKeywords?apikey=<api_key>&knowledgeGraph=1&outputMode=json&url=http://www.wired.com/2015/02/the-upside-of-artificial-intelligence-development/][8]   
*(replace the api_key with authorized Alchmey API key)*

**Relations Extraction**

*Extracts the facts you need from raw text. Identifies Subject > Verb > Object*

Example:   
*1) I want a sandwich  
* Output:   
a) Subject – I   
c) Action – Want   
c) Object – a sandwich   
See it yourself:   
[http://access.alchemyapi.com/calls/text/TextGetRelations?outputMode=json&text=I+want+a+sandwich&keywords=1&apikey=<api_key][9]>   
*(replace the api_key with authorized Alchmey API key)*

*2) Charter buys Bright House  
* Output:   
a) Subject – Charter   
b) Action – buys   
c) Object – Bright House   
See it yourself:   
[http://access.alchemyapi.com/calls/text/TextGetRelations?apikey=<api_key>&outputMode=json&text=Charter%20buys%20Bright%20House&entities=1&keywords=1][10]   
*(replace the api_key with authorized Alchmey API key)*

**Taxanomy**

*Classify text documents based on 1000+ categories and subcategories.*

Example:   
*1) Lebron James has been struggling lately in his recent return to the Cavs  
* Output:   
{

"label": "/sports/basketball",

"score": "0.931426"

},

{

"confident": "no",

"label": "/hobbies and interests/magic and illusion",

"score": "0.223659"

},

{

"confident": "no",

"label": "/sports",

"score": "0.113789"

}

*2) Text from URL e.g. *[*http://www.hollywoodreporter.com/news/sundance-todd-mccarthys-picks-best-769112*][11]*  
* Output:   
{

"label": "/art and entertainment/movies/film festivals and awards",

"score": "0.999824"

},

{

"confident": "no",

"label": "/art and entertainment/movies and tv/movies",

"score": "0.364626"

},

{

"confident": "no",

"label": "/society/sex",

"score": "0.308618"

}

**AlchemyData News**

Query pre-enriched news articles to find trends, monitor events, and get up to date information

Documentation available: <http://docs.alchemyapi.com/>

Try out the Query Builder and see the example: <http://querybuilder.alchemyapi.com/builder>

Sample application: <http://whos-in-the-news.mybluemix.net/>

**Alchemy API in the Application Stack**

**<img src="http://bluecloudnews.com/wp-content/uploads/2016/11/word-image-73.png" class="wp-image-2439" />**

 [1]: http://access.alchemyapi.com/calls/text/TextGetRankedNamedEntities?sentiment=1&apikey=%3capi_key%3e&outputMode=json&text=President%20Obama%20works%20at%20the%20White%20House
 [2]: http://access.alchemyapi.com/calls/text/TextGetRankedNamedEntities?apikey=%3capi_key%3e&outputMode=json&text=Zach%20Walchuk%20was%20born%20in%20Mankato,%20MN%20and%20lives%20in%20the%20white%20house%20down%20the%20street
 [3]: http://www.automatedtrader.net/news/at/153105/fidelity-investments-acquires-emoney-advisor
 [4]: http://access.alchemyapi.com/calls/url/URLGetRankedNamedEntities?apikey=%3capi_key%3e&showSourceText=1&outputMode=json&url=http://www.automatedtrader.net/news/at/153105/fidelity-investments-acquires-emoney-advisor
 [5]: http://access.alchemyapi.com/calls/text/TextGetTextSentiment?apikey=%3capi_key%3e&outputMode=json&text=So%20happy%20the%20Patriots%20won%20the%20Super%20Bowl.%20Let%E2%80%99s%20party!#PatriotsParade
 [6]: http://access.alchemyapi.com/calls/text/TextGetTargetedSentiment?apikey=%3capi_key%3e&outputMode=json&text=So%20happy%20the%20Patriots%20won%20the%20Super%20Bowl.%20Seahawks%20suck.&target=seahawks
 [7]: http://access.alchemyapi.com/calls/text/TextGetRankedKeywords?apikey=%3capi_key%3e&knowledgeGraph=1&showSourceText=1&outputMode=json&text=The%20New%20England%20Patriots%20raised%20the%20lombardi%20trophy%20high%20over%20the%20city%20of%20Boston%20Wednesday
 [8]: http://access.alchemyapi.com/calls/url/URLGetRankedKeywords?apikey=%3capi_key%3e&knowledgeGraph=1&outputMode=json&url=http://www.wired.com/2015/02/the-upside-of-artificial-intelligence-development/
 [9]: http://access.alchemyapi.com/calls/text/TextGetRelations?outputMode=json&text=I+want+a+sandwich&keywords=1&apikey=%3capi_key
 [10]: http://access.alchemyapi.com/calls/text/TextGetRelations?apikey=%3capi_key%3e&outputMode=json&text=Charter%20buys%20Bright%20House&entities=1&keywords=1
 [11]: http://www.hollywoodreporter.com/news/sundance-todd-mccarthys-picks-best-769112