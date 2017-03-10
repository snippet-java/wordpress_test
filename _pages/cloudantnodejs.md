---
ID: 1799
post_title: CloudantNodeJS
author: snippet java
post_date: 2016-10-21 03:24:18
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/services/cloudant/cloudantnodejs/
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

**Java code to Explore** [playground allow_anonymous="yes" show_deploy="yes" height="1300"] var parameters = { username: '313d6562-626e-4edc-855f-528c7bba73e3-bluemix', password: '38fdea42f285bd146e7a7d2baa15f91dc486dababd609a1c61e3b2a2452aa55a', dbName: 'pet', docId: 'Fri-Apr-15-08:58:52-UTC-2016' }; //Main function //Output will be reflected via console.log function function process(req_parameters, callback) { var Cloudant = require('cloudant'); var cloudant = Cloudant({ account:req_parameters.username, password:req_parameters.password }); var db = cloudant.db.use(req_parameters.dbName); // gets docname from the database with query string {params}. db.get(req_parameters.docId, { revs_info: false }, function(err, body) { if (!err) console.log(body); }); } //Allows Execution of this process //will run if only called directly if (require.main === module) { process(parameters,null); } else { // name of the unit for logging and servlet path also var unitpath = ""; // Template for making above code available // as service via superglue routine var superglue = require('../lib/superglue.js'); module.exports = { path: '/'+unitpath, priority: 1, init: function (app) { // something to do initially }, GET: function(req, res) {superglue.GET(req,res,parameters,unitpath)}, POST: function(req, res) {superglue.POST(req,res,process)} } } [/playground]