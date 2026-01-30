**Question:**  
Another common issue that we see is whatever images that are pushed onto ECR, right? Nowadays we work with a lot of enterprise customer, and they do a security scanning on those images, right? And no images are like perfect, right? There are a lot of vulnerabilities as well because developers install a lot of packages from here and there, DevOps engineer also installs a lot of packages from here and there. So do you also take care of the overall security of the Docker image, or it is someone else who takes care?

**Ans:**  
No, we only take care. And it is not that developer will directly push the image to ECR. We have CI/CD pipeline setup. So how the process looks like is the developer will push the code into GitHub. Then the pipeline will trigger, and there are multiple jobs, multiple tasks. So initially what it will do is it will first check the code using a tool called like SonarQube. So it will first check that, and then it will go to the next stage where it will go to the build stage where it will create an image, and then afterwards we can, we also have a tool like Trivy to check that Docker image. Sorry, tool like Trivy. Yeah. So it will scan the Docker image, and then it will prepare a report and give it to the developer, and then if everything works well, then only it will push to ECR. Okay. And also we have one the best practice is to ask developers to check all these security scanning tools on your local itself and then push your code to GitHub so that the time is not wasted and the pipelines are also not keep on running. So those things also we make sure to have.

**Q:**  
That is a practice, but how will you ensure that developer does the scanning on his local first and then, because you still need to have some kind of control over the pipeline, right? You cannot trust the developer that he will scan his code and then push the code onto the GitHub repository, right? As a DevOps engineer or a DevSecOps engineer, we still have to enforce certain controls in the pipeline, right?

**A:**  
So correct, correct, that we definitely have, but how developers does is they just test it on the pipeline. So what I'm asking developers to do is first test it on local and then push it on the pipeline because when you run the instances, that also incurs cost. So if a developer is pushing 10 times just for one change, that is not practical for the organization. So it's a best practice that we follow. It's not that the developers will check and push the code and it will go to ECR. Those checks will be done in pipelines. But just to avoid that multiple runs of pipeline, we ask the developers to check it on the local as well and then push the code.

**Q:**  
Okay. Okay. Fine. So this is with respect to security. But if you have to reduce the overall size of the Docker image, so what kind of measures you take?

**A:**  
So we will go through the Docker image. We will see that what are the files we are copying. And as I said that we have to use the lightweight image only, lightweight base image only, and using multi-stage build also helps us to optimize the Docker image; it also helps us to bring the size of the image down. So these are the policies, these are the practices that we follow to have the lightweight image created.
