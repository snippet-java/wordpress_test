---
ID: 1395
post_title: DevOps1
author: snippet java
post_date: 2016-10-21 03:09:06
post_excerpt: ""
layout: page
permalink: >
  http://watsonbeach.com/services/devops/devops1/
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
Understand capabilities of IBM Bluemix DevOps Services source code management for projects

Lab Prerequisites

*   IBM Bluemix account
    *   Sign up for Bluemix: <http://bluemix.net>
*   IBM DevOps account
    *   Sign up for DevOps: <http://hub.jazz.net>
    *   Use the same credentials as for Bluemix
*   Supported web browsers:
    *   Chrome, latest version for your OS
    *   Firefox, latest version for your OS or at least ESR 31
    *   Internet Explorer, versions 10 and 11
    *   Safari, latest version for your OS

1 - Getting Started

1.  As in the 5.3 Lab, begin by logging on to IBM DevOps Services and fork the project located at [https://hub.jazz.net/project/ecosysdevcnc/cdc-lab-5/overview][1] into a new project.

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-196.png" class="wp-image-1446" />

1.  Give the new project a unique name, check all the boxes, and choose an appropriate Bluemix runtime configuration. Click on CREATE.

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-197.png" class="wp-image-1447" />

1.  Once you see the message about successfully creating your project, click on the EDIT CODE button in the top right.

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-198.png" class="wp-image-1448" />

1.  Wait a moment for the workspace to setup. Once the project is ready, click on the Git icon located along the left vertical column.

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-199.png" class="wp-image-1449" />

2 - Adding Local Changes to the Git Repository

1.  The Git Repository view, or "git view" is organized into two panes. The left pane shows any staged outgoing changes, any incoming changes, and the active branch's history. The right pane, taking up the majority of the screen, shows any working directory changes and provides the functionality to select changed files, enter a commit message, and stage the files for a push.

  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-200.png" class="wp-image-1450" />

1.  The process of forking a project causes changes to occur in the files. Notice there are two files listed in the right pane. Click on each one to get a view of what has changed.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-201.png" class="wp-image-1451" />
2.  .gitignore is a file used by git to list all the files and directories in the project that should be ignored by git. Things like Bluemix launch configurations and build artifacts generally do not need to be tracked by git and should not be commited to the master branch.   
    project.json is a file used by DevOps Services to identify your project. It should remain unchanged and can be committed to the master branch.   
    Enter a commit message, something simple like "Initial project creation" is fine, check the box to Select All, then click the Commit button in the top right.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-202.png" class="wp-image-1452" />
3.  Notice that the working directory changes pane is now empty of any files, and a new entry is made in the Outgoing section of the left pane. This is called "staging" a commit.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-203.png" class="wp-image-1453" />
4.  The master branch is still unchanged, and will remain so until you push the outgoing commit. If there were any incoming changes from other branches, you might need to merge them together with your outgoing changes, and you would have the opportunity to do so before the push completed. Click on the Push button now and note that the History is updated to include your commit. Any other branches would be able to pull this commit and it's changes into their local working copy.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-204.png" class="wp-image-1454" />

3 - Verify the integrity of code delivered to the repository with a build

1.  Next we will configure DevOps Services to perform a build of the code and have the build process trigger off a successful push to the master branch. The builder will watch the master branch for any new pushes, and when detected, it will automaticaly begin building the project into a deployable package.   
    Click on the BUILD & DEPLOY button in the top right.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-205.png" class="wp-image-1455" />
2.  The buiild and deploy pipeline view gives a high level view of the various stages that are configured in the pipeline. Click on the ADD STAGE button now.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-206.png" class="wp-image-1456" />
3.  A stage consists of a series of jobs that run in sequence and the input for those jobs. Stages can be configured to run automatically based on triggers.   
    The input can be either the project SCM repository or build artifacts from a preceding stage. Input applies to all jobs in the stage. When a stage is run, the input is fetched. The files are placed in the working directory before each job starts.   
    Jobs perform the work for a stage, such as building, deploying, and testing. The jobs in a stage run sequentially, and each job runs in a clean container environment. Files do not persist across job executions, so any dependencies required by the jobs must be provided in the stage input or installed as part of the job.
4.  Give the stage a good name to identify it, then click on the JOBS tab.   
    Note that the input for the stage is the SCM repository that contains the master Git branch of your project. Also note that the default has the stage run whenever any change is pushed to Git.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-207.png" class="wp-image-1457" />
5.  In the JOBS tab, click on the plus sign to add a job, then select Build.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-208.png" class="wp-image-1458" />   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-209.png" class="wp-image-1459" />
6.  Under Builder Type, select "npm".   
    Note that many builder types are available to facilitate your project's specific needs, and futher configuration options include working directory, build archive directory, and an option to stop the stage execution on the event of a job failure.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-210.png" class="wp-image-1460" />   
    Scroll to the bottom and click SAVE.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-211.png" class="wp-image-1461" />
7.  We are automatically returned to the build and deploy pipeline overview and the new stage is displayed. It is possible to start a build automatically by clicking the play button within the stage. Do this now.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-212.png" class="wp-image-1462" />
8.  The stage starts running, and the build job status changes from Pending, to Queued, to Running, to Succeeded. To view the logs from the build, click on the job status message.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-213.png" class="wp-image-1463" />

From the Stage History view, we can see the history of all previous executions of this stage, and download any artifacts generated as a result of a particular stage execution.   
  
<img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-214.png" class="wp-image-1464" />

4 - Trigger the Build Stage by Pushing to the Git Repository

1.  Return to the Web GUI editor by clicking on EDIT CODE in the top right.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-215.png" class="wp-image-1465" />
2.  Alter the project slightly by opening the public/index.html file and change the <h1> tag to something new.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-216.png" class="wp-image-1466" />
3.  Switch to the Git repository view by clicking the Git icon in the left column.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-217.png" class="wp-image-1467" />
4.  Note that the SCM detected a change in the working directory. Enter an informative commit message, check the box next to index.html, then click the COMMIT button. 
5.  The outgoing commit is now staged, and ready to push. Immediately after pushing the commit, switch over to the BUILD AND DEPLOY view. You will need to be quick to see the builder stage automatically start, but if you   
    miss it, you can always view the details of the build in the history view.   
    Click on Push, then immediately click on BUILD AND DEPLOY.   
      
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-218.png" class="wp-image-1468" />   
    <img src="http://bluecloudnews.com/wp-content/uploads/2016/10/word-image-219.png" class="wp-image-1469" />

Observe the automatic execution of the build stage.

This completes the IBM Cloud Developer Certification Section 5.4 Lab.

 [1]: http://hub.jazz.net/project/ecosysdevcnc/cdc-lab-5/overview