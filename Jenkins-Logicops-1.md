
**Interviewer:** Hey folks my name is Ravish and welcome back to another video in the series of DevOps projects. Now today's video is interesting, and in this video we are not asking anything about the cloud part or the cloud DevOps, nothing about that. We are entirely concentrating on the DevOps capabilities; we are entirely concentrating on the pipeline. So the very basic question will come: what exactly do you do in your pipeline? What is the project and how you do the deployment? So in this interview, I have asked the candidate each and every step. Explain me each and every step: what exactly you are doing, what is happening in the steps? And there are multiple steps,   like why are you checking out the code, where is the code, what CI tool you are using, how what kind of a tool you are using to build them, compile them, WAR file, TAR file, or anything, on the archiving, why are you using Nexus, what is the difference between Nexus and JFrog, a bit about SonarQube as well, and then a bit about deployment strategies as well. So,   take a look at this interview and understand that this is a very basic question that every DevOps engineer needs to understand. So this question is kind of suitable for, like, three to four years of experience, and this can be asked of someone who has less experience than that. So concentrate on this interview, even if the process is different, your process, your organization's process is different from our process or the candidate's process. You need to write down each and every step of your organization's process because it is going to be asked in an interview, and any interviewer can pick it up and ask the,   the stages, what exactly you are doing. Alright? So,   that would be the,   today, that would be today's video. Alright, so if you're new over here and seeing me for the first time, my name is Ravish and I create content for DevOps and cloud related stuff. Kindly subscribe to the channel because it really motivates me to create more content like this. So without further ado, let's get started.

 

**Interviewer:** What tools have you worked on?

**Candidate:** So I've worked on tools such as,   Jenkins, SonarQube, Maven, Gradle, Fortify, uDeploy, Docker, and Ansible. I have worked on these tools. So, in my current project, so like my roles and responsibilities, they have multiple,   freestyle jobs for a single application, and they are each,   dependent on each other,   like check out,   then,   clean, build, so upstream and downstream job for a single application. So I am migrating those into the,   CI/CD pipelines. Automation is being done using Jenkins, and deployment is being done using AWS CodeDeploy, and,   as well as,   like a branching strategy as well. And,   like,   DevOps metrics, or like, change time, mean,   change time, lead time, failed deployment, past deployment. So I have integrated Apache,   in Apache, and integrated Jenkins, getting Git, GitHub, and they are, the unused could check how many,   commits has been done, how many for our, or like, still repositories? So all the things,   and the failed past deployments,   into the dashboard. So that's.

**Interviewer:** Okay, so you said that your total experience is 6.5 years, right?

**Candidate:** Yes.

**Interviewer:** And your relevant experience in DevOps 4.5?

**Candidate:** 4.5.

**Interviewer:** And in cloud?

**Candidate:**   cloud, I have recently started working from Capgemini.

**Interviewer:** Okay, so less than one year, right?

**Candidate:** Yeah.

**Interviewer:** Okay, okay, okay, okay.

**Interviewer:** What is your project?

**Candidate:**   can you please explain me your,   project? Like, what exactly does it do?

**Interviewer:**   the project is like,   they have multiple applications which are on, into the,   freestyle jobs. Means, they have a,   under the Java applications, and that,   they are like using freestyle jobs for CI, for checkout, build, and all those things. So that I am migrating into the CI/CD pipelines. So that I am doing.

**Interviewer:** Okay, what is the technical stack,   tech stack behind this project?

**Candidate:** The thing is that this,   project is meant to,   like, a few,   like,   the project involves many teams, like other,   but from TCS, juniors, so there are a lot of,   things,   it's like other clients as well with this project, and few of the applications they have given to the,   Capgemini team to work on. So once,     those things will be done like this, and then,   the Capgemini DevOps team will be part of their central stream. So first initially they have started like this.

**Interviewer:** Okay,   no no, I was actually looking for the,   like, what language this code is written on the project.

**Candidate:** Oh, Java.

**Interviewer:** Java. And what type of application is it? A desktop application, web-based application, anything, mobile application? What kind of application it is?

**Candidate:** It is a Tata Click e-commerce application.

**Interviewer:** E-commerce, I mean, you have...

**Interviewer:** What is your role in this project?

**Candidate:** To access it through web, right?

**Interviewer:** Yes.

**Candidate:** Okay, okay, okay. So what is,   your role exactly in this project? What, what do you do on a general basis?

**Interviewer:** So, the general basis, any deployments is coming, so I'm used to, I'm deploying on to the,   so environment, then integration of the Jira with Jenkins, and then this,   like DevOps metrics as I mentioned, then migrating to the,   the freestyle jobs into the CI/CD pipelines. Like this I'm working.

**Candidate:** Okay, okay. So your,   pipeline is declarative or scripted?

**Interviewer:** Declarative.

**Candidate:** Okay, okay. So,   can you walk me through the whole...

**Candidate:** Can you walk me through the whole pipeline?

**Interviewer:** Pipeline from step one till deployment, whether you do production or something, or how many environments do you have: dev, stage, QA, whatever. From first step till the end step, I want to know the knowledge of the life cycle of your product.

**Candidate:** Yes. Also, there are two pipelines: first, like, on the on-premises and,   cloud. So I explain,   because cloud is something,   it's not completed fully, so I'll explain on-premises. Okay, so,   it will start with the pipeline, then agent any, then environment sections if you want to declare any environments with that. So you can now declare environments if you are using any environment variables, then, then after that triggers,   the means like any GitLab trigger, on push, trigger on request, like that. And after that, parameters. So in that parameters, you can declare boolean parameters and then choice parameters if you want to specify. Then tools, like JDK8. And after that, you know, stages will start. Stage one: checkout. Then stage two: branches. Or then stage clean, or to clean any build artifacts previously built artifacts? No. Then,   stage,   build,   for,   building the code,   then stage generate reports, for the,   test report, or then stage test for the, like, the integration test. Or then,   stage compile, or compile metrics and archive, archive artifacts for the archiving the artifact. So for that, and then stage Sonar,   quality gate for the,   quality coverage. If that code quality meets with that, then it will execute that pipeline; if not, it will abort the pipeline. Then stage static analysis for the,   JaCoCo test code coverage and JUnit.   then,   stage dev deploy,   when,   like I have specified even expression, when expression like params...

 

...deployment. Then stage staging deployment, performance deployment, and then stage QA deployment,   sorry, UAT deployment. Then stage demo deployment,   for the demo environment, stage L2 deployment and,   L4 deployment. And,   if there is a means like,   continuous testing, so,   that,   stage,   CI, like for building the, then stage Nexus repository for the,   like,   storing your applications and,   into the, storing your artifacts,   into the application into the Nexus. Then post email notifications for the,   passed and failed deployments, like that.

**Interviewer:** Okay, so,   what was the first step?

**Candidate:** Stage checkout.

**Interviewer:** So you are checking out. Okay, so,   what is the, um...

**Interviewer:** What is the repository you are using?

**Candidate:** Like, repository you are using, on which platform? I mean, what is the source code management over here?

**Interviewer:** Source code management is a GitLab.

**Candidate:** GitLab. What is the difference between Git and GitLab?

**Interviewer:** The Git is a command line based and it provides multiple commands, and whereas the GitLab stored as a,   like a code and,   takes,   like text,   it takes a minute. And GitLab backup is a command line utility and which mostly runs on the Linux server as a, as a GitLab.

**Candidate:** Okay, so GitLab is like, do you install anything for GitLab or something? I mean, what do you need?

**Interviewer:** Okay, okay.   what is the difference between Git...

**Interviewer:** What is the difference between Git rebase and Git merge?

**Candidate:** Rebase and Git merge? So Git rebase,   is like you have to,     it's like,   like, it rebase means,   Git merge and Git rebase are used to, early to work,   combined work for the multiple developers in one code. Like,   rebase is a command that allows your developers to,   integrate changes from one branch to another branch. And the Git merge is used to allows you to merge the branches of merge from branches from the Git.

**Candidate:** Okay, okay. So you were talking about the branching strategies, right? So what are the branching strategies that you folks follow?

**Interviewer:** The branching strategy is, on a feature, develop, master, pre-production.

**Interviewer:** How to fix a bug in production?

**Candidate:** Okay, so let's say there is a bug in production. Okay, how would you,   get the developers to fix it, and what would be the branching strategy then? So I would like to reiterate the question:   so your branch, which branch goes to production?

**Candidate:** Branch, broad branch goes to production.

**Interviewer:** Okay, so now there is a bug in production. How will you work it out now in the branching strategies? Gain production means any error? Means you mean to say, yeah, production. The error came in production. For example, your e-commerce application is running on your production server, and your client has notified that there is a functionality that is not working, which is very much essential today. Okay, now how will you get it fixed from the developers? What would be the branching strategy then?

**Candidate:** So,   like,   first, no, I mean, it's like if there is any issue, like, then I will check like if there is firefighting or anything issue regarding with the developer, I will ask developer to fix that, or, or else it will go to the hotfix branch.

**Candidate:** Hotfix branch.

**Interviewer:** So hotfix branch. So you will create a hotfix branch, right?

**Candidate:** Yes.

**Interviewer:** So you will create this hotfix branch from which branch? What would be the base branch for this?

**Candidate:** So the base branch is branch.

**Interviewer:** Okay, now production branch has a new hotfix branch, and you have written your code there, fix that functionality, you have checked in the code into the production branch. Okay, now you deployed and everything is running fine. Now did you notice that production branch does have a new code now? What happens to the underlying branches?

**Candidate:** Sorry, could you repeat it again?

**Interviewer:** Okay, so ideally what happens is, whenever you write a feature, you do it from a dev branch, right?

**Candidate:** Yes.

**Interviewer:** So you write your code, put it into dev, and then you push it forward to stage, then QA, then production, right? This is the basic scenario. But now you cut out a branch from production branch. Now production branch has more code; the other underlying branch does not have that. Now what happens then? Miss production branch has more books? More code? Now you have fixed the functionality, right? Because that hotfix branch, you cut it out from production, right? Now it has more code; the underlying branches does not have that. What happens now to the underlying branches?

**Candidate:** So I have to,   to Git, I will perform,   to track all the branches, so you know, same line, so I will use a command, so that I am not able to remember actually.

**Interviewer:** Okay, okay, no problem. Okay, what is the second step in your pipeline?

**Candidate:** Clean stage clean.

**Interviewer:**   what do you do in this clean?

**Candidate:** Like,   cleaning the,   artifact previous, any of our artifacts in there, like.

**Interviewer:** Okay, okay.   what is the third step?

**Candidate:** Third step is a stage build, like assemble, Gradle is using.

**Interviewer:** So that's okay. You are using Gradle, right?

**Candidate:** Yes.

**Interviewer:** So,   when you are running Gradle,   what is the output of this stage?

**Candidate:** So,   like, it will,   compile and build the code.

**Interviewer:** Okay, and what kind of,   output does it produce?

**Candidate:** What's the difference between TAR file and WAR file? Um...

**Candidate:** War files.

**Interviewer:**   the servers that you folks are using are Windows or Linux?

**Candidate:** Linux.

**Interviewer:**   like, the,   WAR files are used for only web applications. Okay, and the,   is like that,   file can be,   like both,   it is like archive file.

**Interviewer:** Okay, okay. So you are producing a web archive file, right? WAR file.

**Candidate:** Yes.

**Interviewer:** Okay,   okay, great. Now,   what is the fourth step?

**Candidate:** Fourth step is,   like,   stage integration test. Okay, so you are not putting this artifact which you produced over somewhere, or you are just placing it in some sort? Like, first it will,   go with all the,   stages like, no,   stage materialization or quality, after that it will put into the Nexus repository.

**Interviewer:** Okay, okay. So your next step is,   the fourth step is some kind of testing. What, what testing you have?

**Candidate:**   generate matrices to generate your... This is the plugin, yeah, but it has a full form, that's how it got a name. It's actually Java code coverage, J A C O C O.

**Interviewer:** JaCoCo, Java code coverage. Okay, so this is a plug-in. Where do you install this plug-in?

**Candidate:**   it, it has been installed into the,   build.xml, of the Gradle.

**Interviewer:** Okay, okay.   now,   it produces some kind of...

**Interviewer:** Integration test?

**Candidate:** Report or something.

**Interviewer:** Yes.

**Candidate:** Okay, and what does that report contain?

**Interviewer:** That I have not checked. It is a developer task that...

**Candidate:** Okay, okay.   what is the next step, fifth step?

**Candidate:**   stage or test for the integration test.

**Interviewer:** Okay, what do we have in this integration test?

**Candidate:**   like, integration,   test means,   integration testing will happen like on,   I have specified like,   `sh gradle w` and integration test, and it will run the JUnit build or test results.xml.

**Interviewer:** What do you understand by integration test? What does it mean, actually, in the sense? And why I am running this,   in my pipeline?

**Candidate:** Integration test? Integration test is like,   what you can do is,   is the one kind of,   software testing that runs for the units and the modules and the components of the software applications to combine the entity or any, like, these modules.

**Candidate:** Regression testing.

**Interviewer:** Okay, do you do anything for regression testing in your pipeline?

**Candidate:** Now, that the testing people might agree with that.

**Interviewer:** Okay, no problem. Okay,   after this test, what is the next step, the six steps?

**Candidate:**   the six steps is a stage compile,   compile on matrix and,   archive artifacts. Okay, archiving the artifact. And where are you archiving it?

**Interviewer:**   into the Nexus.

**Candidate:** Nexus. What is this Nexus?

**Interviewer:** Nexus is, oh no, this, or storing artifacts, it is an artifactory tool.

**Candidate:**   is there any other artifactory tool that you know about?

**Interviewer:**   S3.

**Candidate:** S3, okay. S3 is not actually an artifactory tool,   it's just a storage place, you can store there, yeah.   know the difference between Nexus and JFrog?

**Candidate:** Nexus and JFrog.

**Interviewer:** Yeah, so, is kind of X-Ray scans for both, like, regulatory issues and the vulnerability as well. And Nexus performs,   like the health check of the repository.

**Candidate:** Versioning.

**Interviewer:** Okay, okay. So,   who has done the setup on Nexus already?

**Candidate:** See, our team has been done the setup.

**Interviewer:** Okay, there's a different team for this.

**Candidate:** Yes, yes.

**Interviewer:** Okay, okay, okay, okay. So,     let's say, how, how are you doing the versioning of it?

**Candidate:**   like, in the Nexus,   there are two repositories: snapshot and release. So the deployment from the dev,   and QA, it goes to snapshot, and the,   deployment from the master branch and the upper branches, it goes to the release branches. So there we are maintaining the,   versioning.

**Interviewer:** Okay, what do you understand by repository manager?

**Candidate:** Yes, like a repository manager,   is like,   your,   like a dedicated server for your application to manage the repositories for binary components.

**Interviewer:** Okay,   how are you handling this,   authentication and authorization in Nexus repository?

**Candidate:** So,   when we are producing,   means,   generating the,   the files, so into the,   environment variables as I mentioned, so there we are declaring,   that one.

**Interviewer:** Okay, so in Nexus there is something known as policies. Any idea what is that?

**Candidate:** Yes, I heard it, but,   never worked on the Nexus.

**Interviewer:** Okay, just try to take a guess. I mean, what it could be? It's okay if you don't know, but just take a guess what it could be.

 

**Candidate:** Like administering your,   like components,   stages and the policies,   that features integrate with other tools of that. Okay, server applications for administrating your component stage and policies and other features to integrate with the other tools of the suite.

**Interviewer:** Okay, is this a free software, open source, or paid software?

**Candidate:** It is enterprise version.

**Interviewer:** No, no, not version, I mean, is it free or paid? I mean, can I...

**Candidate:** It's paid.

**Interviewer:** Okay, okay. Can you create custom repository in Nexus? Is it possible?

**Candidate:** Custom repositories?   yes, we can. We can create a custom,   repositories, like, you have to,   like,   click,   click on the repositories, and you have to,   add and enter the properties of that appropriate type of artifacts it will hold later.

**Interviewer:** Okay, okay. So the pipeline that you folks are using,  ...

**Interviewer:** Pipeline.

**Candidate:** It pushes the artifact to Nexus repository, right? So this is automatically done?

**Interviewer:** Yes.

**Candidate:** Okay, so if I want to upload manually, is that possible?

**Interviewer:** Manually?

**Candidate:** Yeah, if I want to upload it manually on a Nexus repository, is it possible?

**Interviewer:** That I'm not...

**Candidate:** Okay, no problem. Okay, what is the next step after archiving?

**Candidate:**   after the,   stage archive,   then stage or Sonar quality gate.

**Interviewer:** Sonar quality gate. And why are you using,   SonarQube over here?

**Candidate:** For code quality,   and vulnerabilities of the code.

**Interviewer:** Okay, so,   in SonarQube,   there is something known as technical debt. Any idea what it is?

**Candidate:** What? Technical debt? Any techniques? Technical debt? Any idea? Debt, debt? Yeah, technical,   debt. Like,   its overall ratings,   range from A as in best rating to E as in worst rating. And, and like, maintain your Sonar,   sooner or later, like a technical debt is less than, like, five percent, and,   these are technical debt between these six to ten percent, and see, the technical debt is between 11 to 20 percent.

**Interviewer:** Okay, okay.

**Interviewer:** Code Coverage?

**Candidate:** So you were saying that when,   build is aborted if the code coverage is less than some percent, right? It is so. What is that? How much percentage is that?

**Interviewer:** 80 percent code coverage.

**Candidate:** Yes.

**Interviewer:** Okay, so when I say 80% of my code is covered, what does that supposed to mean?

**Candidate:** Means,   whatever I have applied,   policies or the,   like,   whatever the,     means language,   those,   code coverage meets with the code quality. So that's the thing.   so let's say there is 100 lines of code, okay? In your project, consider 100 lines of code, it can be more, but let us consider 100 lines of code. Now the code coverage is 80 percent. What is the meaning of this?

**Candidate:** Means it meets with the,   criteria of that quality code, like where you defines the,   like sets and rules, and that are,   like, it is not crossing,   that limit, so that meets with your,   criteria. So that's the...

**Interviewer:** Okay, okay, quality profiles. Okay.

**Interviewer:** Quality Profiles.

**Candidate:**   so let's say if it has failed,   what is the next step? What do you do?

**Interviewer:** So,   if it is failed, then pipeline will be aborted.

**Candidate:** Yeah, that. What is the next step? I mean, if it is, the next step is like, you have to check on the console output whether it is a developer side issue, so we'll ask developer to fix that code and all, right?

**Interviewer:** Okay, okay, okay, great.   what is the next step,   after SonarQube?

**Candidate:**   so the next step is,     like, cause stage static code analysis.

**Interviewer:**   what is static code analysis mean?

**Candidate:** Like, static code analysis here,   like, there are two,   pages we are using, like,   parallel, in parallel,   and is mentioned like JaCoCo, J coco exclusion pattern, then,   start S dot class, like that mentioned config, and in, and another one step into the, like, JUnit,   health skills factor, like, oh, that way, and test results dot XML.

**Candidate:** Static vs Dynamic Analysis.

**Interviewer:** Okay, what is the difference between static analysis and dynamic analysis?

**Candidate:** Static,   analysis,   like,   like static,   analysis,   is like more to your,   your,   static means it will static your code, and dynamic means like it will change or forceful with any action, like change or forceful action.

**Interviewer:** Okay, okay, okay.   what is the next step after that?

**Candidate:** Stage Save Deployment.

**Interviewer:** The next step is,   stage dev deployment, deployment onto the developer.

**Candidate:** Okay, and how are you deploying it?

**Interviewer:**   like,   through Jenkins.   I have created job, so in that I have chosen parameter as in the,     like, I have passed the parameters: dev, QA, then,   now, are they staging? So if I want to deploy on to the dev, then I have to, you know, click on to the done, it will deploy on to the dev server.

**Candidate:** Okay, okay, no problem.   do you know what is...

**Candidate:** Deployment Strategies?

**Interviewer:** What, what is,   deployment strategies?

**Candidate:** Yes.

**Interviewer:**   can you walk me through,   what are all the deployment strategies we have?

**Candidate:** Deployment strategies means, in like,   deployment or deployment strategies to change your upgrade and application. So there are main or three types of deployment: deployment process is like development, testing, and monitoring.

**Candidate:**   no no, I was talking about this: blue-green deployment, canary deployment, rolling updates, recreate.

**Candidate:** Blue Green Deployment.

**Interviewer:** Any idea about that? Heard about it?

**Candidate:** Blue-green deployment? I heard it.

**Interviewer:** Okay, like, whatever I have heard it, what does it mean?

**Candidate:** Blue-green,   blue-green, in the blue-green, it will be,   like a roll back will be done, and,  ...

 

...so canary is like a blue-green deployment with your current and new version of the,   your run, running a parallel, and all the,   like,   your,   traffic and all shifts to the,   to the next version or any new version. And the,   canary deployment, or like, once the new version rolls out,   incrementally to,   like your subset of the users, or to be released, or any,   to all the users, like that.

**Interviewer:** Okay, okay. Oh yeah, I think I'm done.