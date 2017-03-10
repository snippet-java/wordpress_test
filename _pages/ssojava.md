---
ID: 1664
post_title: SSOJava
author: snippet java
post_date: 2016-10-21 05:43:45
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/services/sso/ssojava/
published: true
---
<a id="post-1664-__RefHeading__509_1945122989"></a><a id="post-1664-__RefHeading___Toc411148382"></a><a id="post-1664-__RefHeading__279_1945122989"></a><a id="post-1664-_Toc438535314"></a>**Create Java starter application and add Single Sign On service to dashboard**

**Introduction**

When developing an application supporting multiple users, one of the first decisions you will need to face is how to authenticate each users. It might seem like a simple approach to create a database table and populate it with credentials, but this quickly creates further challenges. For one, how will your application be able to integrate with existing applications and their authentication services? This lab will introduce the IBM Single Sign On (SSO) service for Bluemix which you can use to configure your web application to authenticate users from social media sites, enterprise directories via SAML federation, and also a ldap-based cloud identity source.

This lab will walk through the steps to add and configure the IBM Single Sign On service for Bluemix to the java starter application. It will provide step-by-step instructions to create the application, add the service to the Bluemix workspace, configure a cloud identity source, bind and integrate the service into the application, and modify the application code to use external authentication.

The lab requires a workstation (Windows, Mac OS X or Linux are all fine) with the following items installed:

*   bluemix.net account (sign up for a 30-day free trial)
*   Java JRE 7.1 or higher (www.java.com/download )
*   Multiple web browsers (it's most convenient to use one browser for working with the Bluemix and Single Sign On control panel in one and a separate browser for testing your application, recent versions of Firefox, Chrome, Opera, Safari, Internet Explorer)
*   Eclipse mars or later (www.eclipse.org/downloads)
*   Cloud Foundry CLI tool version 6.9 or later – there is a step in the application setup where a link is provided for installation if it is not already on your workstation.

Now let’s get started.

# <a id="post-1664-__RefHeading__511_1945122989"></a><a id="post-1664-__RefHeading__153_1945122989"></a><a id="post-1664-_Toc438535315"></a>**Create Java starter application and add Single Sign On service to dashboard:**

Sign in to Bluemix and go to the Dashboard. Under Cloud Foundry, click on the “CREATE AN APP” button to get started:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-413.png" class="wp-image-1706" />

Then select Web app:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-414.png" class="wp-image-1707" />

Next, you will need to select the runtime for the application. For this lab select the Liberty for Java SDK, and confirm by clicking on CONTINUE:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-415.png" class="wp-image-1708" />

To complete adding the new application, provide a name. Each application in Bluemix public requires a unique name. One easy way to do this for a test app is to append the date and your initials to the name, and then select FINISH:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-416.png" class="wp-image-1709" />

Bluemix will bring up the application's Start Coding panel with a message at the top about the application starting the staging process. If you do not already have the Cloud Foundry (cf) CLI tool installed on your workstation, click on the link shown to go to GitHub and download the current version for your workstation (it will be later than 6.9 but that is ok). After the download is completed, install the cf tool and then proceed to the next step.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-417.png" class="wp-image-1710" />

Next, add the Single Sign On service to the Dashboard. Before proceeding, you will need to select an id that will become the prefix of the URL for the service when used when applications redirect users to the service for selecting an identity provider, and also for handling callbacks from identity providers. This id can be up to 32 characters, and must start with an alphanumeric character. Make a note of it here if you like: __________________________________________________

Then, go back to the Bluemix Cloud Foundry Dashboard and select Add a Service or API:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-418.png" class="wp-image-1711" />

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-419.png" class="wp-image-1712" /> Scroll down in the services list to the Security section and then click on the Single Sign On icon, this will bring up a configuration panel for adding the service. On the right hand side, select Leave unbound under the App: section. You can change the Service name: that will be shown in the dashboard or leave it at the default. Then click on the CREATE button:

A panel will display to prompt for a “name” for the service. This is the id that you chose earlier, it is not the name that was shown in the previous panel as the Service name. Once provided, click on the Continue button:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-420.png" class="wp-image-1713" />

This will add the service to the dashboard and now you will be able to create a simple Cloud directory and add a testing user for external authentication in the next section of the lab.

# <a id="post-1664-__RefHeading__513_1945122989"></a><a id="post-1664-__RefHeading__155_1945122989"></a><a id="post-1664-_Toc438535316"></a>**Configure a Cloud directory identity source**

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-421.png" class="wp-image-1714" /> Back in the IBM Bluemix Cloud Foundry dashboard, scroll down to find the SSO service that you just created. Click on the service to open up the configuration panel:

In the configuration panel, click on the Cloud Directory icon to add and configure a directory in the cloud for our lab exercises:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-422.png" class="wp-image-1715" /> <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-423.png" class="wp-image-1716" />   
  
In the next screen, you may give the identity source a new name other than the default and see the current list of users. It's empty at first so click on the add icon:

and put in some information for a test user. This can be any user information that you prefer, however make a note of the username and password set since that will be used when testing the external authentication service:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-424.png" class="wp-image-1717" />

Save the user by clicking on the Save button, click on the Save button for the identity source configuration panel, and then re-open the service by selecting it:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-425.png" class="wp-image-1718" />

After re-opening the identity source configuration panel, a settings icon button will be shown in the upper right section of the panel. To manage the password policy applied to users in this identity source, you can click on the settings icon button for the identity source:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-426.png" class="wp-image-1719" />

The settings control has two option panels. The Auto Consent option tells the SSO service if it should prompt the user after an authentication to allow the SSO service to retrieve personal (e.g. name and e-mail address) information from the identity source. Leave this setting to On for this lab to observe this prompt in action. The Password Policy option allows you to select various levels of password quality and lifetime. At the present time, these policies are fixed and you may select from one of the three. Choose Medium, and then click on Save.

Lastly, click on save in the identity source configuration panel to return to the main SSO configuration panel

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-427.png" class="wp-image-1720" />

The name shown for the identity source will be the name you selected or the default name of Cloud Directory. The toggle (shown as Enabled) next to the name allows the service administrator to enable or disable a particular identity source for use by applications. Leave the toggle at Enabled and click on the Back to Dashboard link in the upper left to return to the IBM Bluemix Cloud Foundry dashboard.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-428.png" class="wp-image-1721" />

# <a id="post-1664-__RefHeading__515_1945122989"></a><a id="post-1664-_Toc438535317"></a>**Bind the Single Sign On service to the application**

To bind the Single Sign On service with the configured identity source, first click on the application icon in the dashboard to bring up the application overview page. Then click on the Bind a Service or API button:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-429.png" class="wp-image-1722" />

A panel will be displayed, select the radio button next to the Single Sign On service and then click on the ADD button:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-430.png" class="wp-image-1723" />

You will be prompted to restage the application. A restage is used to add the VCAP_SERVICES environment variables to the application so that it will be able to access the Single Sign On service bound to the application. Click on the RESTAGE button:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-431.png" class="wp-image-1724" />

The restage and restart of the application will complete quickly, however, you do not need to wait before proceeding. On the left side of the application's overview panel, click on the Single Sign On label or click on the icon for the service. This will open the configuration panel for the service in the context of this application:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-432.png" class="wp-image-1725" />

**or**

When accessing the configuration panel from within an application, an INTEGRATE tab will also be shown. For the Java application you are configuring, a module needs to be downloaded from the Single Sign On service. The link to this code is available from the INTEGRATE tab. Although we will return later to the INTEGRATE tab to finish configuring the application, click on the label to switch to this tab now:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-433.png" class="wp-image-1726" />

Since this is binding to a Java app, the Return-to URL will already be set. The SSO Service will invoke the Return-to URL after authentication is completed.

For Liberty for Java Applications, the Single Sign On service leverages the OpenID Connect (OIDC) client feature from Liberty and the Bluemix Liberty build pack. As a result, Java applications running on Bluemix do not need to include any code to support the OpenID Connect protocol or Single Sign On. (see <http://www.ng.bluemix.net/docs/services/SingleSignOn/configure_apps.html#tsk_configuringlibforjavaapp> for more info.) You will need to add some security constraints in the Java app to see the Single Sign On work.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-434.png" class="wp-image-1727" />

You may change the Display name for the application from the default. This is the name used by the SSO service when prompting a user for consent to allow the retrieval of personal information from the identity source. Once the Display name updated (if desired), click on the Save button:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-435.png" class="wp-image-1728" />   
After saving, click on Back to Dashboard in the upper left to return to the IBM Bluemix Cloud Foundry dashboard. At this point, the SSO service is ready to be used with the application.

# <a id="post-1664-_Toc438535318"></a>Run the app

Now that it is all configured in Bluemix, go ahead and test that the app is working. From the Bluemix Dashboard, click the SSO application you created above. Click on the app url to open the application’s home page.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-436.png" class="wp-image-1729" />

You should see the home screen for the java starter app.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-437.png" class="wp-image-1730" />

Since you have not put any security constraints in place, no pages in the app or protected.

# <a id="post-1664-_Toc438535319"></a>Add security constraints to Java app

Now that Single Sign On is bound and configured to our java app, add security constraints so only the user you added to the Cloud Directory will be able to see the secure pages.

## <a id="post-1664-_Toc438535320"></a>Download Starter Code

Now that your app and SSO is bound together, you can download the starter code. From the Bluemix dashboard, click your application to enter your application Overview. In the left menu, click Start Coding.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-438.png" class="wp-image-1731" />

Scroll down to the series of numbered steps starting with the Download Starter Code button. Make a note of these steps (they will not match the picture and instead will be customized for your Bluemix id, current Bluemix space and application name). Complete steps 1, 2 and 3 as shown to get a copy of your code.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-439.png" class="wp-image-1732" />

Now that you have the code, it is time to update the application to have some security constraints.

## <a id="post-1664-__RefHeading__517_1945122989"></a><a id="post-1664-__RefHeading__519_1945122989"></a><a id="post-1664-_Toc438535321"></a>Import into Eclipse

Next, open Eclipse. Select File -> Import.. . Select General -> Existing Projects into Workspace in the Import Select dialog.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-440.png" class="wp-image-1733" />

Select Next.

In the Import Projects dialog, click the Browse button and browse to the unzipped code you downloaded from Bluemix.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-441.png" class="wp-image-1734" />

Click Finish.

## <a id="post-1664-_Toc438535322"></a>Add servlet to protect

Now add a servlet to protect from all users except those authenticated by SSO.

In Eclipse, select File -> New -> Servlet.

Create a servlet named MySecuredServlet.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-442.png" class="wp-image-1735" />

Click Finish.

The servlet you just created should already have a WebServlet annotation set.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-443.png" class="wp-image-1736" />

Update the response text in the doGet method to be a custom message you want to see.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-444.png" class="wp-image-1737" />

Next, open index.html.

Add an html link to the new servlet you created.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-445.png" class="wp-image-1738" />

This will add a link from the home page to the secured servlet.

## <a id="post-1664-_Toc438535323"></a>Add http constraints

Now you can protect the servlet. You are going to use javax annotations to secure the MySecuredServlet page.

First you need to include the libraries for the annotations.

Open pom.xml

There are several ways to add a dependency in the pom file. This example shows adding raw xml. So, click the pom.xml tab to see the raw xml for the pom file.

In the dependencies, add a dependency for jsr250-api.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-446.png" class="wp-image-1739" />

Next, open MySecuredServlet.java file.

Add a the servlet security and HTTP constraint annotations as shown in the next image.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-447.png" class="wp-image-1740" />

This will protect all access to this servlet except by those authenticated users who have the role of ‘any-authenticated’.

## <a id="post-1664-_Toc438535324"></a>Map roles

Next you are going to map the role ‘any-authenticated’ to a valid subject.

Add a folder named ‘resources’ under the src\main folder.

Add a folder named ‘META-INF’ under the newly created resources folder.

Create a new file named ibm-application-bnd.xml

Add the xml you see in the next image

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-448.png" class="wp-image-1741" />

This says that All Authenticated Users get the role of ‘any-authenticated’.

Lastly, open the pom.xml again. You will need to inform maven to use the src\main\resources files when it builds the war file. In the build -> pluginManagement -> plugins -> maven war plugin, add the following

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-449.png" class="wp-image-1742" />

## <a id="post-1664-_Toc438535325"></a>Prepare and push your project

You are almost ready to push the project to Bluemix.

Compile the war by right clicking on pom.xml from Enterprise Explorer view.

Select Run As -> Maven build… from the context menu.

In the goal field, type package.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-450.png" class="wp-image-1743" />

Then click the Run button.

Check the Console view and make sure your build was successful.

Open a command prompt.

Go to the directory that contains the project you have been working on.

Using the cloud foundry command, login to bluemix.

Once logged in, push your app. Note, you must be in the directory that has the manifest.yml file.

Run the command cf push yourappname, where yourappname is the name of the app on Bluemix.

Once your app is pushed and restarted, you are ready to test.

# <a id="post-1664-__RefHeading__523_1945122989"></a><a id="post-1664-__RefHeading___Toc411148389"></a><a id="post-1664-__RefHeading__165_1945122989"></a><a id="post-1664-_Toc438535326"></a>**Testing the application**

When testing with the Single Sign On service with the Cloud Directory, it can be easier to use a different browser security and cookie context (for example in a new “private” window in Firefox) to simulate the experience of a new user to your application. Or you can also just use an entirely different browser. Here we'll use a Chrome browser in the screenshots.

Begin by opening your application's url: https://<appname>.mybluemix.net (be sure to use https!):

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-451.png" class="wp-image-1744" />

Note that the My Secured Servlet link is at the end of the paragraph. Click on this link to bring up the Single Sign On identity provider chooser list:

Since the Single Sign On service is configured with only one identity source, only one option is shown. Click on Cloud Directory and sign in as the user you added to the directory previously:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-452.png" class="wp-image-1745" />

After you click on the Login button – a prompt will be displayed (this happens by policy when using the Cloud Directory) stating that the user password has been reset and must be changed. Note that requirements for the password are displayed in the form. Enter in an updated password:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-453.png" class="wp-image-1746" />

Next, there will be a panel asking for permission (from the application name you set in the INTEGRATE panel) to retrieve your personal information from the external authentication identity provider. You may select either Allow or Allow and Remember. If you select Allow, then each time you authenticate with this identity provider through the Single Sign On service, the prompt will be displayed.

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-454.png" class="wp-image-1747" /> Then the application displays the successful authentication message:

# <a id="post-1664-__RefHeading__525_1945122989"></a><a id="post-1664-__RefHeading___Toc411148390"></a><a id="post-1664-__RefHeading__167_1945122989"></a><a id="post-1664-_Toc438535327"></a>Summary and next steps

<a id="post-1664-__RefHeading___Toc411148391"></a><a id="post-1664-__RefHeading__169_1945122989"></a> Now you have an application that can use the Single Sign On service with a simple identity provider. A very good next step would be to continue on with the Bluemix SSO documentation to add a Social Media identity provider. There are step-by-step instructions for this as well as configuration of SAML Enterprise identity sources. To access the documentation, from the configuration panel for the Single Sign On service, click on the DOCS button:

<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-455.png" class="wp-image-1748" />