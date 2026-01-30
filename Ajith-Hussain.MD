**Ajith:**  
Hey. Hi Hussain. How are you? Thanks for joining.

**Hussain:**  
Hi Ajith. I'm doing good. Thank you so much. How are you doing?

**Ajith:**  
I'm good as well. Thank you for asking. So let's do one thing. Let's quickly introduce ourselves and then maybe we can deep dive into the interview.

**Hussain:**  
Sure. Yes. So would you like to introduce yourself first?

**Ajith:**  
Sure. Sure. I'll go ahead. So first of all, of course, as I said, thank you so much for having this call. I am Hussain Lokhandwala, having more than 4.5 years of experience as a DevOps engineer and I am certified in AWS, Kubernetes, Terraform and Azure. I started my journey in 2021 as a junior DevOps engineer, worked there for 1.5 years, and then I switched to my current company where I'm working as a senior DevOps engineer. So mostly my day-to-day activities look like we support a US client where we work in agile methodology. We have junior developers, junior DevOps and senior DevOps in our team. So mostly my responsibility is to take care of the tickets which are assigned to us, setting up the priority and completing those tickets, and also assigning tickets to the junior DevOps. And also I have to create a few proof of concepts for the clients and move ahead if those things go well. So I'm passionate about solving complex problems and architecting new things. Yeah. So this was about me.

**Ajith:**  
Okay. Thanks, Hussain, for the brief introduction. So I will also quickly introduce myself. So I'm Ajith. I lead the technology team at one of the service-based companies in India. So I have about total 14 years of experience in the IT industry across multiple domains and geographies. So for the initial 6 to 7 years of my career, I was more into full-stack development. Later on, for the next four to five years, I was into cloud platform engineering, solutioning, and a few cloud leadership-related roles. Last one and a half years, I have taken a leadership role at this particular company where I'm heading the entire technology unit. So yeah, let's get right into the content about the interview. So, Hussain, tell me one thing. How would you architect a fully available and fault-tolerant application on AWS?

**Hussain:**  
Okay. So first of all, I would assume a couple of things like the application is a data analytics and there are a lot of services required. So we would go with EKS there, and we'll start from the basics first talking about the networking part. We will create a VPC, private subnets, public subnets, and we'll make sure that the compute and database is in the private subnet and the application load balancer and those stuff are in the public subnet, and accordingly we'll set up the NACL and security groups. Talking about the storage part, we would use S3. S3 also we will enable cross-region replication so that in another region we also are replicating data. Then for databases, if we are using RDS, then we'll make sure to enable replicas in cross-region as well for disaster recovery processes. And if the application allows, we would go with DynamoDB because it supports global tables. Then coming on to compute, as I said that we would use EKS. It also supports cross-region node deployments, and we will have a cluster in the primary region and also we will have a secondary region EKS deployment there as well. And I would use monitoring. For monitoring, we would use AWS CloudWatch logs and also we can integrate with Prometheus and Grafana to have custom logs of application logs and Kubernetes logs as well. And we would set up everything on Route 53 as well. We'll have failover policies there. So if any region goes down, then the traffic should be diverted to the DR region. So these are the things that I would use. Also, for the security part, we'll make use of AWS Secrets Manager to store the secrets, and we will try to have everything automated in an automated form. So we'll have pipelines, Terraform pipelines, and application deployment pipelines, and we'll use a GitOps approach as we are using Argo CD, as we are using Kubernetes. Yeah.

**Ajith:**  
Okay. Okay. So you mentioned that you will use EKS, right? Any specific reason you'll use EKS and not any other container service like ECS?

**Hussain:**  
So I assumed that the application is a data analytics and a lot of security is required, and there are a lot of services to manage. So in those terms, I would go with EKS because it provides more in terms of security like RBAC rules are there, then network policies are there, and also deployment is way easier in Argo CD in Kubernetes using a GitOps approach. And also we can have rollbacks also easy in EKS. So considering those scenarios, I chose EKS rather than going to ECS or EC2.

**Ajith:**  
Okay. Okay. And why do you think that ECS won't be a good choice in that particular scenario? Because I have seen a lot of enterprise-grade companies use ECS for their highly available and fault-tolerant applications. So what do you think? You mentioned about security, you mentioned about Argo CD, right? You mentioned about other things. So don't you think that ECS also provides that kind of stuff which EKS does?

**Hussain:**  
ECS also provides, but let's say in terms of security, then only it will be limited to AWS, like you can have your access in the roles of task definition and mention that only. But on EKS, you can get a lot of customizations available. Again, it depends on the application's need. If the application is okay to work on ECS, then we can select that as well, but if you need more complex architecture and more security, then I would prefer to go with EKS.

**Ajith:**  
Okay. Can you tell me a scenario where ECS will be better suited as compared to EKS?

**Hussain:**  
Sure. So if you have a simple deployment, you don't have a lot of services, and everything you think that can be manageable inside AWS only, and the access management can be done using the policies mentioned in the IAM roles. So in those kinds of scenarios, we can definitely go with ECS because there also you just have to mention the task definition and all the services that you want. It is definitely a reliable choice, and the routes also you can mention in the application load balancer. So if you feel that everything can be managed using those specific services and you don't need complex services like ingress and those kind of services, then definitely you can move ahead with ECS.

**Ajith:**  
Okay. And what do you think, which one is cheaper as compared to each other?

**Hussain:**  
ECS is cheaper.

**Ajith:**  
Why do you think ECS is cheaper?

**Hussain:**  
Because it only costs around the services that you use. In terms of EKS, it will charge you for the EKS cluster by default, no nodes running, and as soon as you spin up the nodes, as soon as you use a lot of services of EKS, so it will be way more costlier.

**Ajith:**  
Okay. Okay. So you meant to say EKS controller manager or maybe the actual cluster is also billable, and in case of ECS, only the underlying infrastructure is billable.

**Hussain:**  
Correct. Yeah.

**Ajith:**  
Okay. Anything apart from that?

**Hussain:**  
I think apart from that, I'm not able to think of anything as of now.

**Ajith:**  
Okay. No worries. No worries. Okay. So you also mentioned about public subnets and private subnets, right? So when you create a subnet, there is no option to maybe create a private subnet or a public subnet, right? It is some configuration that needs to be done to make that particular subnet as public or private. So I wanted to understand what is that configuration? How would you make your subnet a public or a private one?

**Hussain:**  
Okay. So for making a subnet public or private, the answer lies in the route tables which are assigned to that particular subnet. So if you mention in the route table of a subnet that the routes coming to that subnet should go through an internet gateway, then it becomes a public subnet. So any route in that subnet will go through the internet. And if you mention that there is also a capability of NAT gateway that can be attached to a public subnet, and you can mention a route in a subnet that any request should go to NAT gateway, that will be a private subnet.

**Ajith:**  
Okay. And internet gateway is attached to a subnet or it is attached to a VPC?

**Hussain:**  
It is attached to a VPC.

**Ajith:**  
Are you sure about that?

**Hussain:**  
Yes. And NAT gateway, you said that it is a public...

**Ajith:**  
Okay. Okay. And where are the rules? Suppose I have a private subnet, and my private subnet needs access to the internet, right? So where would be my outgoing rules? In the public subnet or the private subnet route table?

**Hussain:**  
In the private subnet route table, you will mention it that any request coming to the private subnet should go through NAT gateway.

**Ajith:**  
All right. Okay. Okay. Fine. Have you worked with hybrid networking in AWS?

**Hussain:**  
Yes.

**Ajith:**  
Okay. So like if I have to connect my on-premises network with AWS, can you list down all the choices you have to connect both the networks, like your on-prem as well as your AWS?

**Hussain:**  
Correct. Sure. So first option is Direct Connect, where you will, if you have tons and tons of workload that you have to migrate or data transfer from AWS cloud to on-premise, so Direct Connect is one of the option. Second option is a site-to-site VPN connection, where you can create a customer gateway and AWS gateway, and that also you can connect your on-premise and cloud. And one of the third option that I could think of is Transit Gateway, that is also something that you can configure to have your data transfer from AWS to your on-premise. So if you have, if you don't have a lot of workload, then Transit Gateway and site-to-site VPN connection is a choice because it is cheaper than Direct Connect.

**Ajith:**  
Okay. Any other networking options that you can think of apart from these?

**Hussain:**  
I think AWS hub service is also there. I am not able to remember that complete name, but that's one service is also there.

**Ajith:**  
Okay. Okay, fine. There is also VPC peering right in AWS. So why do you think you require a Transit Gateway, and what problem Transit Gateway solves? Or maybe why Transit Gateway is required at the first place because we have VPC peering, right? If you have to connect multiple VPCs within AWS, how Transit Gateway is beneficial as compared to VPC peering.

**Hussain:**  
So let us consider if you have to connect only two VPCs, then VPC peering is fine. But let's say if you want to connect more than two VPCs, let's say five or 10 VPCs, then you have to do VPC peering among all VPCs. That is from A to B, A to C, A to D. Okay, it is not transitive. But Transit Gateway is hub and spoke model, that means you can just have one Transit Gateway in the middle which can be connected to all the VPCs, and then all the VPCs can communicate with each other using the Transit Gateway.

**Ajith:**  
Okay. So you mentioned that VPC peering is cheap as compared to Transit Gateway when it comes to pairing only or connecting only two VPCs. Why do you think it is so?

**Hussain:**  
So the data transfer via VPC peering is cheaper than the data transfer via Transit Gateway.

**Ajith:**  
Okay. 

**Hussain:**
So it depends on the data transfer. Just configuration is fine.   

**Ajith:**  
Okay. Okay. Fine. Hussain, have you worked with disaster recovery in your experience?

**Hussain:**  
Yes, I worked with.

**Ajith:**  
Okay. So suppose I have an e-commerce website, okay? And I want to design a disaster recovery solution for this e-commerce website, and the disaster recovery region should be geographically isolated from the primary one. So what would be the solution that you will design?

**Hussain:**  
Sure. So first of all, I would get to know how critical is your application, and I would ask that if you are okay with some time of downtime or no downtime is required. Okay. Accordingly, I will set up a solution. So let's go through those scenarios. In the first scenario where you say that we can handle some downtime, but we need a cheaper solution, so at that time we would go with backup and recovery process where we are backing up all the EKS cluster and the application and the RDS, and we are ready whenever the disaster happens. We will spin up the new EKS, we will spin up the new RDS in the DR region, and once the application is up, we will route the traffic to the new region. So in this scenario, there might be some downtime, but it is the cheapest solution. Coming to the next solution where you want less amount of downtime, in that scenario, what we can have is we can have a read replica in another region for RDS. We can have EKS cluster there, but we'll have scaled down all the nodes to zero. That means your application is not running, but it is ready whenever the disaster happens, so in less amount of time, we just have to spin up the nodes of the EKS, and then we will route the traffic. And in the third scenario where you say that your application is very much critical, you have to have the application up all the time, you cannot afford any downtime. At that time, in the DR region, we will spin up the full-scaled EKS. We will have RDS as read replica. And at the time of disaster, we will have failover policies in our Route 53. So whenever the application load balancer is not giving the perfect health check in the primary region, then all the traffic will be diverted to the secondary region, and without any downtime, the users won't face any issues, and all the traffic will be diverted to the DR region. So this is how we would set up a DR.

**Ajith:**  
Okay. So just in case, if you want to support this particular e-commerce website globally, okay? So imagine this will be accessed from US as well as India, okay? And the latency should be also very minimum, right? If someone from India tries to access, it should be accessible from the nearby data center, and similarly with the US, okay? So in that case, how will you design a solution? Because I also want to separate the writes, okay? So the database also needs to be separate from each other. So in that case, how will you support both the regions at one time?

**Hussain:**  
Okay. Sure. So for that, we would also make use of CDN like CloudFront, which is a global service. So it will help us to serve the static content, and we will use a global load balancer so that any request coming from the specific region, it will be handled in that particular region itself. And talking about database, we will have read replicas in all the regions from where the traffic will be coming from. And also to reduce latency, we will use ElasticCache or RDS for caching the data in those specific regions. So this is how we will maintain the lowest latency, and the users can get that data from the nearest data center.

**Ajith:**  
Okay. So the CDN will take care of your front end. The ElasticCache will cache your database queries, but still it will not support multiple writes, right? So it needs to be some kind of a global table solution to make sure this happens. That's okay, not a problem. So basically, you have worked with compute, networking, databases, and storage, all right? So can you name a few security best practices in each and every area that you can think of?

**Hussain:**  
Okay. So starting from networking, I would say that make use of AWS services like AWS Shield is there, then AWS WAF is there to have specific rules so that whatever requests are coming in, that we can authenticate first and then move ahead. We can enable AWS Flow Logs to trace all the requests which are flowing through VPC. These are the things that we can think of in networking part. Second, talking about compute and storage. So I would say whatever RDS are getting created or whatever EBS are getting created, those should be encrypted with an encryption key, and we'll also make sure that we back up those RDS and EBS volumes. Next, we'll make sure to enable all the CloudTrail logs, and we can also configure a few AWS Config rules so that if any misconfigurations are done in our AWS environment, then we can set up a few Lambda functions or we can set a few events to correct those things.

**Hussain:**  
Okay. And apart from that, monitoring is something that we'll take into consideration, that is AWS CloudWatch logs. So and also we can set alarms for any issues. So if any database goes down or if any CPU reaches a higher limit, then we should be notified about that so that we can immediately take any action against it. So yeah, I think these are the things that I can think of right now.

**Ajith:**  
Okay. Okay. So this is good for an enterprise-grade customer, right? So having Shield, WAF, all these things are very costly, right? So if there is a conservative customer, he mentions to you that, Hussain, I just have to keep the lights on. I have to ensure my infrastructure is secured enough. I do not have a budget to, as you know, right, security is very costly. So in that case, what are the bare minimum things that you would do to keep your cloud secure?

**Hussain:**  
Okay, got it. So for those bare minimum things can come like security group rules should be managed with the lowest access possible with the granular access. It shouldn't be open to all. The second, NACL, we can also configure on subnet level. Next is maintaining the granular access while providing any policies in IAM roles. And also, if it's a small-based company, then we will be managing access management. So whatever the roles that we have assigned to the users, those policies also should be minimized. Like if we are using IAM Identity Center, that we mention the permission sets, so those things also should be minimized. We should have rules for a couple of teams, and we should give them access accordingly. And apart from that, one main thing that we can have is to deploy anything using automation only. There shouldn't be any manual configurations done in AWS. No one should have any manual access. This is something is a very best practice that we can follow that any DevOps, if you need any infrastructure, you reach out to your DevOps team, and they will create a Terraform code, and then they will deploy it, and then you can access it. So these are some things that a small-grade application, small-grade company can take into consideration.

**Ajith:**  
Okay. Okay. So there is one security best practice where you keep your databases in a private subnet, right? But imagine that there is a scenario where we need to keep our database in a public subnet because some other third party has to access it, or maybe basically I want to make my database accessible to a certain third party. So how will you extend access without compromising on the overall security?

**Hussain:**  
So there are a couple of ways of accessing your RDS. That is one of the ways using your traditional user ID and password. Second way is to also make use of IAM database authentication. So this is where you can create your IAM role, and that IAM role only can access those databases. So this is something that also you can configure it after keeping your database into your public subnet. And then also, you will attach a security group rule to your RDS. Make sure that we are not opening the port to all of the internet, but we'll make sure to add the specific IP only to get through the database. And apart from that, we can also enable the TLS communication in transit so that any request coming to your database should be via SSL certified only, or else it shouldn't get through your database. So I think these are the configurations that we can do.

**Ajith:**  
Okay. So if you have an EC2 instance, okay, and there is a vulnerable package installed in your EC2 instance, AWS provides one service which can be installed or the agent can be installed, and it can give you what kind of package is vulnerable to what kind of CVE. So do you know what service is that?

**Hussain:**  
I think AWS Inspector is one of the service which will scan all the resources that you have in AWS, and it will show the vulnerabilities.

**Ajith:**  
Okay. Okay. Okay. Fine. Have you worked with a well-architected framework?

**Hussain:**  
Yes, I worked with that.

**Ajith:**  
Okay. Can you list down all the pillars and maybe summarize each one of them?

**Hussain:**  
Sure. So there are six pillars. Initially, there were five pillars, then sustainability was also added. So there are six pillars that based on which you should architect your framework. Okay. So first pillar is like cost is there, security is there, then operational excellence is there, then performance is there, and reliability is there, and sustainability is there. So these are the six pillars which will help you to design an architecture. Talking about each pillar, I'll just brief each one of them. So let's say performance we are talking about that means what AWS tells you to select your specific instances, select your specific RDS which is aligned with your application. Because there are multiple AWS instance families, there are multiple AWS instance types, then you might not know which one to select. So that framework helps you to select that specific instance, that specific RDS. Next coming on to operational excellence. So there are multiple AWS services which will help you to develop and deploy your architecture, that is like AWS CI/CD is there, then backups are there. So operationally also you can be very much clear on that. Then talking about performance, so again it comes like which all services that you are using, which services will be best for your application, which instance type you are selecting, what services you are selecting, so those should be optimized. Next talking about reliability, we can have multi-AZ availability zones, we have disaster recovery, we have backups and recovery, so that there shouldn't be any concerns where the data is gone or not. And next talking about security, so confidentiality, integrity, and any threat detection, those things are also managed by AWS. So we just have to enable those services and integrate those services and our application. And sustainability is something that AWS takes care of. It depends on which instances that you are spinning up, then it should be sustainable. So this is something that mostly AWS takes care of it.

**Ajith:**  
Okay. Yeah. Okay. Have you worked with cross-account? Like you have multiple AWS accounts, and suppose you want to access a particular KMS key from one particular source account to a destination account, right? So have you worked with this kind of a setup where you have, maybe one example would be KMS, another could be S3? So you have a source EC2 instance in some other account, and you want to access an S3 bucket. So how do you facilitate that connectivity? So one example would be your KMS, and the other one could be S3. So what is the configuration that is required to do that or enable that connectivity?

**Hussain:**  
Sure. So for this, we will use STS, that is Secure Token Service. And how we would do is, let's say there is an AWS account A and account B, and your EC2 is in account A wants to access S3 in account B. So in your IAM role of account A, we will mention the policy of STS to assume a role, and the ARN of the role of account B we will mention there in the policy. And in the account B, the role, we will mention inside the trust policy, we will mention the ARN of account A so that the account A can assume a role in account B. And all the policies, let's say I want to access S3 in account B, then in account B IAM role only, I allow the access inside the policies so that the IAM role of account A can assume a role in account B, and then it can access the S3 bucket, get or put objects, whatever role want to do.

**Ajith:**  
Okay. So while establishing this particular connectivity, did you face any issues in your past, any experience with connectivity failures, and what was the issue like, and how did you resolve those?

**Hussain:**  
Yes, 

**Ajith:**
cross-account access is tricky, right? For most of the times, it doesn't work in the first attempt when it comes to multiple environments, multiple services. So anything that comes to your mind that that particular issue was for a long time, and you figured out anything that comes to your mind?

**Hussain:**  
Yes, regarding the KMS key only, because that is not just read KMS key that you have to give, but you also have to give extra read access to the policies in account B as well. I'm not able to recall what's those specific read and get access you have to add, but those are the things also policies you have to add. And also when you are trying to access any S3 bucket and if it's a cross-account, then you also have to mention inside the bucket policies that this is the role which should be allowed to do access on the S3. So bucket policies also we have to take into consideration there.

**Ajith:** 
Okay. Have you hosted a website on S3?

**Hussain:** 
Yes. 

**Ajith:**  
Maybe a static website on S3.Do you remember what? Suppose I have a domain abc.com, and I want to host it on S3. So can you recollect what kind of configurations or what kind of steps you have to do to make sure that website is publicly available and deployed on S3?

**Hussain:**  
Yeah, I think we also have to make use of CloudFront in front of S3, that we can mention the ARN of S3, and there should be an index.html file in S3, and we have to mention that specific file to be accessed to.

**Ajith:**  
Okay. Anything else that comes to your mind, or that is it?

**Hussain:**  
Yeah, actually I don't remember that because I have done it long back.

**Hussain:**  
Okay. No, no worries. No worries. So, we spoke about security, right? What kind of best practices we have to follow in terms of cloud, in terms of compute, in terms of network, in terms of storage and database. So I have another question on similar lines. It would be with respect to cost. Okay? So if a customer says that, most of the customers nowadays are cost-sensitive, right? They are burning a lot of cost behind infrastructure, and on top of their mind, there is always everything related to cost, right? Yes. So maybe as a cloud engineer, what would be your suggestions, or what would you implement in your cloud infrastructure to make sure that your customer is happy and you implement a lot of cloud cost optimization solutions? Or it can be on any part; it can be like similar to security; it can be on compute; it can be on security, databases, whatnot. So just wanted to understand your perspective on cost.

**Ajith:**  
Sure. So I have worked with healthcare domain clients where the compliances and security, these are the two main pillars that they have to work on. So, and also, be it enterprise-level solution or be it a new application, new company, but everyone has to be cost-sensitive. Now, let's see, so I am definitely responsible for how the cost management is to be done. So how I would look at it is, first I'll make sure that the compliance and security, these two things are not compromised whenever I am trying to reduce the cost. Now, there are a lot of things that I'll go through. First is, I'll check that what is the service which is costing the highest for the AWS account, and then I'll see if we can minimize it or if we can have alternative of it. Second, if I know that these are the instances we will be using for long terms, then definitely we'll ask to get reserved instances, and we can also pay the money upfront. So that will be way cheaper for us. And we can also use spot instances for the task like batch jobs are going on. So if any interruption is there, then also it's fine for the developers. So I'll make sure that we use those. Next, there are a lot of updates coming from AWS itself. Let's say recently they said that GP2 was available, but now GP3 is also available, and they suggest to shift your traffic from GP2 to GP3. It will give high performance, and it's cheaper as well. So I'll make sure to integrate those solutions, to change instance types, and see what intensive instances we are using and are they required or not. Because instances are like GPU intensive, IOPS intensive, memory intensive, and these are the specific families there and instance types are there. So if we can switch from instance type like, say, T3 to T3a because T3a is cheaper but the configurations are the same. So if those are the scenario, then I'll hop onto that. Next, we definitely take backups of RDS, we definitely take backups of EBS. So what is the retention of those backups? If you are taking, if you are keeping it for longer time which is not required, so I'll minimize those retention. Then in storage classes, we have storage in S3. So are we keeping it in which class? If we know that this particular storage is not required, then we can keep it in Glacier class or archive class. These are the things that I'll do. And I'll also make use of the AWS services like AWS Cost Explorer and AWS Trusted Advisor. So these are the services which suggests on how we can save cost.

**Hussain:**  
So yeah, these are the things that come to my mind as of now. 

**Ajith:**
Is Trusted Advisor free?

**Hussain:**    
No, I think you have to pay for it.

**Ajith:**  
Okay. Okay. So you mentioned that if there are any batch jobs, you can use a spot instance. Okay? So suppose I have a scenario where at 11:30 PM, I want to run a job which will fetch some data from the database and massage data and put it on some other data pipeline, right? So in this scenario, will you still use a spot instance? Batch jobs, right? So this is kind of a batch job, right? Or maybe a particular batch job which needs to be run at a particular time. So will you still run a spot? That is the question.

**Hussain:**  
So let's say how much time your spot instance is taking, first of, how much time your batch job is taking, and also if it is not completed, are there any retries available? So if retry is there, then definitely you can use a spot instance. If it completes the job, then it's fine. If it doesn't complete the job, if there are any interruptions there, and then if you can rerun your batch job, then also it's fine. You can use spot instance because it will create a new instance and it will run through it.

**Ajith:**  
Okay, what if that particular instance type is not available in that region?

**Hussain:**  
So I think there are a lot of alternative instance types available. Or I'll also switch if instance family, if required, because a higher instance type is still cheaper than an on-demand instance that we take. So I'll again measure the cost. If it's cheaper, then we can use those things.

**Ajith:**  
Okay. No, no worries. So have you worked with Infrastructure as Code? In your experience, right? So in AWS, there is CloudFormation right, and we have Terraform as well. Okay? So out of the two, which one is more suitable for you? Or maybe under what circumstances you will choose CloudFormation versus Terraform or Terraform versus CloudFormation. So just wanted to understand your thought process behind both the technologies.

**Hussain:**  
Sure. So I feel Terraform provides a lot of functionalities, be it just for AWS or it is also multi-cloud. And mostly on the enterprise level, we use Terraform, even though we have to deploy everything on the AWS only, because it provides like S3 state file, and also there are a lot of, it multi-cloud support is there, then modularized code is there, that is one code you can use it multiple times for multiple environments. You don't have to reuse the code, rewrite the code. So these functionalities are provided by Terraform. So mostly I would prefer Terraform over CloudFormation, even though when you want to deploy everything on the AWS. But there might be a few situations where you go with CloudFormation. Like, one of the major functionality that CloudFormation has is if any new service comes to AWS, it will take a bit of time to have their code on Terraform, but CloudFormation will have it immediately. So if you are on a project where any new services that come to AWS and you have to automate it, then I think you should go with CloudFormation. Also, CloudFormation is very much easy when it comes for creating a code in AWS. Let's say if you want to create a Lambda function, so in Terraform, there is a long process to write a Python code, then you have to push the Python code up, and then you have to create a Lambda function. But in CloudFormation, that is also easy. So these are the few functionalities where you might choose CloudFormation. But if you ask me, then I would prefer Terraform only.

**Ajith:**  
Okay, so you mentioned about multi-cloud, right? One of the key benefits of using Terraform over CloudFormation is clearly the multi-cloud or cloud-agnostic abilities. But imagine you have a dedicated infrastructure only on AWS; it does not have any other cloud provider or on-premises or wherever. Will you still choose Terraform, or you'll go ahead with CloudFormation?

**Hussain:**  
I would still choose Terraform because multi-cloud is one of the functionalities, but there are other functionalities as well, like say modularized code is there. The community of Terraform is way huge; if any issues that you face, then you'll be able to figure out way easier. And if you have multiple environments that you have to deploy, if you have multiple accounts that you have to deploy, you can do it in just one directory of the Terraform file. So those are a lot of functionalities provided by Terraform. So that's why I would still prefer Terraform.

**Ajith:**  
Okay. Okay. So during the initial conversation, you mentioned about load balancers, right? During the highly available question. So in AWS, there are multiple types of load balancers, right? So what are those, and under what circumstances you'll use which load balancer?

**Hussain:**  
Okay. So AWS provides three types of load balancers: Application Load Balancer, Network Load Balancer, and Gateway Load Balancer. And there was a Classic Load Balancer which is which is deprecated right now. So talking about Application Load Balancer, if you have path-based routing, if you have host-based routing, and for application use case, mostly we use Application Load Balancer because it works on layer 7 of OSI model, that is application layer, and it will mostly route your traffic to your target groups and EC2 instances. Okay. And then next is Network Load Balancer. So Network Load Balancer is used where you have to serve your traffic with very low latency. And for example, you would use Network Load Balancer in trading platforms where millisecond is also very much important, and you cannot expect any delay on your request. So in those terms, you would use Network Load Balancer. Also, a functionality that NLB provides is you can attach an elastic IP to it. And a third load balancer is Gateway Load Balancer. So Gateway Load Balancer mostly comes in terms of security because it integrates well with your API gateway and the web as well, and it is mostly used in financial sector where your authorization is more important than reaching to the application. So whenever a request comes, then Gateway Load Balancer is responsible to check if the request is authentic or not, and then only it will forward it to the application. So that's when you use Gateway Load Balancer.

**Ajith:**  
Okay. Okay. So if you want to deploy your serverless applications right, you can use maybe API Gateway and Lambda, right? So what is the difference, or maybe when you would use an API Gateway versus when you would use an Application Load Balancer? Any particular use cases that things that come to your mind where API Gateway is more suited or load balancer is more suited?

**Hussain:**  
Yeah. So let's say if your APIs are transferring only inside the VPC, and those are simple APIs, any path-based routing or host-based routing will work, then at that time you would use Application Load Balancer itself. But if your APIs also have to be authenticated, those are coming from third-party APIs, and you also have to send your request to third-party tools, so in those scenarios, you would use API Gateway. API Gateway also supports DDoS protection, and it also supports TLS by default. There are a lot of configurations that you can do in terms of security in API Gateway. So in those scenarios, you would go with API Gateway. But if anything that you want to request inside your VPC, so then I would suggest to go with Application Load Balancer.

**Ajith:**  
Okay. So suppose your application is deployed completely on AWS, right? It has Route 53, it has load balancers, it has auto-scaling groups, it can have an EKS cluster or ECS cluster, it will have RDS instances. Suppose users are reporting failures in your application, okay? It can be any kind of a failure. We just got a message from one of our customers that your application is not working. So what would be your next steps as a cloud engineer to investigate the issue, and how do you remediate that particular issue?

**Hussain:**  
Okay. So first thing I would check is what changed when the application was running. Was there any deployment done, and after that the application is not running, or if any configuration has been changed? I'll first check the pipelines if anyone has run the pipeline, if any infrastructure has been deployed or application has been deployed. So first I will check that. If those are the things, then it will be easier for us to catch hold of the issue, and we can revert it back. But let's say if there are no deployments done, then I'll go to the like EKS is there, then I'll first check the logs of each and every component. I'll start with EKS. I'll see if the pod is running or not, if the application is active or not. Then I would check the database, are active or not, has anyone stopped it, or if there are any kind of those issues. Next, I would also see the logs, the flow logs which are going through. We have also monitoring in place, observability in place. We have health checks in place. So we will check that which health check is failing. Is your ALB is not working, or your database is not working? And most probably, I'll get hold of that specific issue, and then I'll first see if a new application was, if a new version was deployed, then I'll revert it back so that the application is stable. My first point, my first thing would be to make the application stable and then figure out what was the issue. So I'll first revert it back, and then I'll see through the logs that what's the issue, and then I'll try to again redeploy it on the staging and dev environment first and then again move to production.

**Ajith:**  
Okay. So Hussain, we spent a lot of time on AWS. So I think let's dive deep into the other DevOps tools right, like Docker, Kubernetes, Terraform. So just wanted to understand from your end, apart from AWS, what kind of other DevOps tools you are well-versed with, and what's your experience on all the tools like?

**Hussain:**  
So I'm well-versed with Terraform and Kubernetes because that's a day-to-day task that I have to do, and also creating CI/CD pipelines, that is also something that I do on daily basis using GitHub Actions and AWS CodePipeline. And also creating and pushing Docker images to ECR and deploying those things.

**Ajith:**  
Okay. So do you create Docker images, or you get Docker images from the developers? You are just responsible for the CI/CD?

**Hussain:**  
No, I create as well. We get on a call with the developer; mostly I only create. And yeah, the requirements, let's say there is a requirements.txt file, those things will be given by the developer, but we usually create a lightweight image.

**Ajith:**  
Okay, okay. In that case, I want to understand what are some Docker best practices that you follow in terms of image creation, right?

**Hussain:**  
So as I said, we have to create a lightweight Docker image. It should be optimized. It should not be a very heavy weight. So for that, we first, we should use is, it should be a multi-stage build where initially in the first stage you are building the application, and then you are utilizing that artifact which was built by the older image, and then you build your final image, and then you run the container. So that is one thing to have multi-stage builds. And even in that, you have to make sure that you're using lightweight image, one of the, and also you shouldn't be using like, let's say Alpine is one of the lightweight image, but you shouldn't be using like Alpine:latest because there might be any new configurations done, so there shouldn't be any surprises for you. So always make sure that we are using the base image with a specific tag only. And then definitely we will move ahead. We will update the tags. We will go through the document, what are the new updates in that specific image, and then we'll update it. Next best practice that we follow is to not run the container with the root access. So we will create a specific user in that image, and then we will run the Docker image with that specific user having the access to that specific folder only. And we'll make sure, we also make sure that whenever we create a Docker image, we also document it so that if any new DevOps engineer comes or even the developer comes and watches that image, they should know that why every command is written, for what purpose. So these are the things that I would make sure while creating a Docker image.

**Hussain:**  
Okay. And where do you host your Docker images?

**Ajith:**  
Right now we host it on ECR, AWS ECR.

#TimeStamp 48:25

**Ajith:**  
Okay. ECR. And how do you control how many number of images are there in ECR because it can grow, right? I have been working with a customer where some of the DevOps engineers have kept like unlimited number of ECR images, and their ECR usage or bill has been shot up. So what kind of practices you follow to ensure that the ECR images are not orphan, and only required or whichever images are required are there in the repository? How do you ensure that?

**Hussain:**  
Correct. Yes. So that is a case that was a case with our organization as well because developers would add a tag, and they would push even for testing, they would push a lot of Docker images. So we have a couple of Lambda functions that will trigger on daily basis to check how many images are there, and the latest 5 to 7 images, it will make sure that it is there in ECR, but the older images, it will, we don't just do it for ECR, we do it for all the resources as well, for EC2 and RDS if they are running on the nighttime as well, so it will make sure that during night time, we scale down those resources because in the night time no one is using that. And similarly we do it for ECR as well.

**Ajith:**  
Okay. Okay. Fine. So one of the challenges that I face in our org is basically developer says that this particular Docker images are working fine or absolutely fine in our local machines, but when we deploy it on maybe AWS environment, it doesn't work. Okay? So this is a very typical and common scenario. Okay? So how do you ensure that whatever Docker image is created on the developer machine is working as is on the ECS cluster or EKS cluster?

**Ajith:**  
Yeah, correct. So this was actually a major issue, and that's why also Docker came into picture that system things are working on my system but not working on another system. So Docker is one of the solution that it should work on every system. But one of the solution that even I have faced is there can be a port issue, that means you are opening your port in your local system, but that is already being used on EKS or Docker EC2 that you are using. So those things we also need to take into consideration that how you are deploying it on your local machine and is the same thing, the same way that how we are deploying it on EKS or on EC2. So that is one thing that we would get on a call with the developer and check that. And apart from that, we'll also check like, let's say the port that you're opening is also open in the security group or not. So those request coming to should be allowed there. So that can be one of the port issue. And second is the tags that you are giving to your image, is it repeated or not? Because that might be a case that you are pushing a different image and you are pulling a different image from on the EKS or on the EC2. So those things I would see first.

**Hussain:**  
Okay. Another common issue that we see is whatever images that are pushed onto ECR, right? Nowadays we work with a lot of enterprise customer, and they do a security scanning on those images, right? And no images are like perfect, right? There are a lot of vulnerabilities as well because developers install a lot of packages from here and there, DevOps engineer also installs a lot of packages from here and there. So do you also take care of the overall security of the Docker image, or it is someone else who takes care?

**Ajith:**  
No, we only take care. And it is not that developer will directly push the image to ECR. We have CI/CD pipeline setup. So how the process looks like is the developer will push the code into GitHub. Then the pipeline will trigger, and there are multiple jobs, multiple tasks. So initially what it will do is it will first check the code using a tool called like SonarQube. So it will first check that, and then it will go to the next stage where it will go to the build stage where it will create an image, and then afterwards we can, we also have a tool like Trivy to check that Docker image. Sorry, tool like Trivy. Yeah. So it will scan the Docker image, and then it will prepare a report and give it to the developer, and then if everything works well, then only it will push to ECR. Okay. And also we have one the best practice is to ask developers to check all these security scanning tools on your local itself and then push your code to GitHub so that the time is not wasted and the pipelines are also not keep on running. So those things also we make sure to have.

**Hussain:**  
That is a practice, but how will you ensure that developer does the scanning on his local first and then, because you still need to have some kind of control over the pipeline, right? You cannot trust the developer that he will scan his code and then push the code onto the GitHub repository, right? As a DevOps engineer or a DevSecOps engineer, we still have to enforce certain controls in the pipeline, right?

**Ajith:**  
So correct, correct, that we definitely have, but how developers does is they just test it on the pipeline. So what I'm asking developers to do is first test it on local and then push it on the pipeline because when you run the instances, that also incurs cost. So if a developer is pushing 10 times just for one change, that is not practical for the organization. So it's a best practice that we follow. It's not that the developers will check and push the code and it will go to ECR. Those checks will be done in pipelines. But just to avoid that multiple runs of pipeline, we ask the developers to check it on the local as well and then push the code.

**Hussain:**  
Okay. Okay. Fine. So this is with respect to security. But if you have to reduce the overall size of the Docker image, so what kind of measures you take?

**Ajith:**  
So we will go through the Docker image. We will see that what are the files we are copying. And as I said that we have to use the lightweight image only, lightweight base image only, and using multi-stage build also helps us to optimize the Docker image; it also helps us to bring the size of the image down. So these are the policies, these are the practices that we follow to have the lightweight image created.

**Hussain:**  
Okay. All right. So this was about Docker. So let's move to Kubernetes. So you have talked a lot of stuff about Kubernetes, your experience with Kubernetes, EKS, and in general, right? So one thing that I'm interested in is how do you update your EKS clusters? Okay? So what kind of steps you take to update your EKS cluster? How do you make sure that your applications are not down? It is like a zero downtime upgrade. So how do you do that?

**Ajith:**  
Sure. So before upgrading any EKS cluster, we have to have a lot of prerequisites, and we follow that first. So we first create a manual on what are the steps that we will be following. Next, we will also go through the release notes on which the Kubernetes version we are going to, are there any deprecated APIs or not. The application that we have deployed, is it compatible with the Kubernetes version that you are upgrading to? So these are the few prerequisites that we follow. We also make sure that the Terraform, the deployment of the application and the deployment of the EKS is both done through pipelines. So anytime if you want to roll back, it can be done as soon as possible. We don't have to wait for that. We also take the backup of the application using a tool like, and EKS also. So after doing all these prerequisites, first we will test the upgrades in the lower environments, and then only we will move to higher environments. Now talking about the upgrades, so how we do it is we use EKS. So that mostly the upgrades of control plane is managed by EKS only. And then we, one by one, cordon a node, and then we upgrade that specific node, and then we uncordon that node. So this is a process that we follow for all nodes. And after that, if we have any add-ons, that also we have to upgrade. So we do that afterwards. So mostly this is how we follow the process.

**Hussain:**  
And just in case the upgrade fails, okay? So imagine that you are moving from 1.x to 1.x+ or some other version, and if it fails, okay, if the application stops working, so what are your next steps?

**Ajith:**  
Yes. So as I said that because of that, in the prerequisite, we take backup of EKS. We are ready with the deployment of application because once you upgrade, you cannot downgrade the EKS, be it node or be it cluster. So first of all, of course, we will troubleshoot what's the issue. If it is a version issue, if it is an API issue, a specific small service is not working because of that the whole application is down, can we do something about it, and we can resolve it or not? And if those things are not possible, then definitely we have to spin up another EKS cluster in the older version, we have to deploy our application again for the older version, and first we have to make the application ready and stable so that no users are being hampered, and then we will check that what was the issue in the deployment process, and then we can take up some decision.

**Hussain:**  
Okay. Okay. So have you worked with stateful applications on Kubernetes?

**Ajith:**  
Yes.

**Hussain:**  
Okay. Can you give an example of a stateful application that you worked on Kubernetes?

**Ajith:**  
Yeah. So there was a PoC that we have created where we had to deploy the application on EKS, and we had to use the MongoDB database. So for using that MongoDB database, we made use of StatefulSet, and there we created a couple of pods, and we created persistent volume for that. And so that was one of the scenario where we used StatefulSets.

**Hussain:**  
Okay. But in AWS, you have a managed service called DocumentDB which provides MongoDB support, right? So why you wanted it to be deployed on a Kubernetes cluster?

**Ajith:**  
Okay. So that was a requirement to have it deployed on the Kubernetes cluster. But let's say if you ask me that where it should be deployed, then of course AWS-provided solution is better than deploying it on EKS. But they wanted a specific PoC on if everything is deployed on EKS, then how it will work.

**Hussain:**  
Okay, but you didn't question them? Maybe as a DevOps engineer, you should start questioning as well.

**Ajith:**  
Yeah, but when it's a business requirement, they are very much stick to it, and also they wanted to check. So it was a PoC. Yeah.

**Hussain:**  
Okay. One of the reason could be cost because AWS managed services are very costly. Okay? So there was a customer where they wanted Kafka to be deployed on Kubernetes versus Kafka as a managed service, right? MSK is a managed service from AWS, but they were reluctant to move from Kubernetes to a managed service because of the cost.

**Ajith:**  
Correct. So cost is one of the biggest concern because I am of an opinion that Kubernetes and EKS should be mostly stateless.

**Hussain:**  
Yeah. So anything that comes with respect to state, it should be moved to a managed service or outside the Kubernetes cluster. But yeah, there are different opinions, but I still believe it should be all stateless.

**Ajith:**  
So you have worked a lot on deployments, right? There are a lot of deployment strategies, right? So I'm more interested in, does Kubernetes support a blue-green deployment? If yes, so what is the configuration like? How will you deploy a particular application with blue-green?

**Hussain:**  
Sure. So Kubernetes definitely supports blue-green deployment, canary deployment, and rolling update deployment which is the default one. Talking about the blue-green deployment, the configuration how I would do is I would first create the upgraded version of application. Let's say I have a specific namespace, and that I have to update that application. So new version of application, I will deploy first the deployment file of the whole new application in that specific namespace, and then I will configure on the ingress file that how much traffic should be diverted to the newer version of that application. So you can manage the configuration on the ingress file that, let's say if 100% of your traffic is going to the older version, and then you can just update that annotations on your ingress so that the whole traffic will be diverted to the newer version using labels and selectors. Okay. Yeah. So this is one of the way that you can do. Also, you can make use of Argo Rollouts, so that is also something that you can do. So everything will be managed by the CRD that you create in Argo Rollouts. So there you have to mention all the configurations, and you can also test it there and there itself.

**Ajith:**  
Okay. So can you list down a few best practices with respect to Kubernetes and not EKS or AWS? I wanted to understand specifically with respect to Kubernetes.

**Hussain:**  
Kubernetes. Yeah. Yes. So it can be cost, it can be security, anything that comes to your mind. What are the best practices that you follow as a DevOps engineer?

**Ajith:**  
Sure. So one of the best practice that you should follow is to mention the request and limits in your pods, that how much CPU and memory it will be utilizing. Second thing is you also should make use of the configuration systems like Secrets and ConfigMap to hold your secrets and hold your variables rather than mentioning it in the environment variables or your hard-coding it into application. Next, also make use of monitoring your EKS cluster. So of course, CloudWatch might do that; you can install that agent, or if you want any custom metrics, you want to create any custom logs of your application, so in those scenarios, you will use Prometheus and Grafana as well. It is very easy to deploy it using Helm, and you can also make use of PromQL to query a specific metric, and you can visualize it on the dashboard so that if any happenings, you are ready with it. Next, you can again using this Prometheus and Grafana, you can also set up alerts. So if any node is taking like more than 80% of usage, then you can get an alert if you don't want to like auto-scale, or if you have an auto-scale stop at five nodes, but even beyond five nodes if they are requesting, even if then your pods are not getting created, so at that time you might get notified. So those are the things that you can configure. And talking about security, you also make use of RBAC, you make use of IRSA, service accounts you can create so that you can give access to your specific pod to specific resource and not the whole cluster to those resources. So these are the best practices I can think of right now for Kubernetes.

**Hussain:**  
All right. So you mentioned about Secrets and ConfigMaps, right? But the Secrets that comes with Kubernetes out of the box, are they really secrets, or you need to do some more stuff to make sure that particular configuration is secured? Because I think Secrets can still be decoded, right? Because it is in a base64 format.

**Ajith:**  
Yes, it can be decoded, right? So anyone who has access to a Kubernetes cluster can get that secret. So imagine I want to connect my application pod to a database, and I put that database password in the secret. So how do I make it more secure?

**Hussain:**  
So in that level, what you can do is we have RBAC as well. So we can not give access to that secret to all the developers. Only the specific DevOps engineers or only the, let's say, manager or tech lead can have only access to those secrets. And then you can like fetch it from the AWS Secrets Manager and then you can store it on that secrets, right?

**Ajith:**  
Yeah. Yeah. So AWS Secrets Manager is that additional layer of security that it provides. Even if you put an RBAC and you don't use Secrets Manager, it still can be a problem, right? Because I want to keep the secret in an external location and not within the Kubernetes cluster.

**Hussain:**  
Okay. That is good. So what kind of troubleshooting scenarios you have faced in Kubernetes?

**Ajith:**  
A lot of, I would say, because whenever you run a pod, there are a lot of scenarios. Let's say there's a CrashLoopBackOff error or ImagePullBackOff error, or it's in the Pending state only. It's not getting scheduled to any nodes. So these are a lot of troubleshooting cases there. And talking about one of them is like, let's say if there's a CrashLoopBackOff error where your pod is getting restarted again and again. So at that time, you first have to go through logs, that is `kubectl logs`, mostly you will find the issue there, or you can describe the pod. So in that, you will find the event that because of which reason the pod is not getting created. So that you can find the reason, and then you can take a decision on what needs to be done.

**Hussain:**  
Okay. So at the beginning, you mentioned about ingress, right? So my question is simple, like why do you need ingress at the first place because there is something called as services as well right in Kubernetes? So services are also used to expose your deployments, your pods, right, to the external world. So why they needed to create another construct called as ingress? So how it is different from services?

**Ajith:**  
Correct. So services can, first of all, internally they can communicate. But if you want to communicate to a service, you'll need to create a load balancer so that the outside user can also communicate with that service. Now if there are 10 services, and if you create 10 load balancers, so that will be a huge cost to the company. So that's why we make use of controller like ingress controller. And that ingress controller also provides a lot of functionalities like, let's say, NGINX ingress controller is there. So that is something that you integrate with your Kubernetes, and you mention all the routes there. So just by one application load balancer and mentioning all the services routes in your ingress, you can route your traffic accordingly to the different services, to the different pods, and not have 10 application load balancers for 10 services.

**Hussain:**  
Okay. So you mentioned about a lot of application deployment on EKS or Kubernetes, right? So what tool you use to deploy your applications?

**Ajith:**  
So for Kubernetes, we use Argo CD, which is a GitOps approach, as a continuous deployment in our CI/CD pipeline.

**Hussain:**  
Okay. So only Argo CD you use, or you use Helm plus Argo CD?

**Ajith:**  
Yeah, it's Helm plus Argo CD.

**Hussain:**  
Okay. Because yeah, most of the organizations use Helm, and on top of that, they have Argo CD to pull all the Helm charts and all that stuff.

**Ajith:**  
Correct.

**Hussain:**  
So yeah, so Kubernetes also have YAML, right? So you can basically write a deployment, services, and just run it. It's quite simple, right? Why do you want to add complexity of having something like a Helm chart, right? Why do you need Helm chart?

**Ajith:**  
So Helm chart is required. You can consider it as a package of your deployment. If you need secrets, you need deployment, you need replica sets, you need config maps, so all of these things, what you can do is you can create a package of it, and you can have values.yaml file to just update the values there. And the major functionality of using Helm is you can use the same configuration in the different environments. So you don't have to write the files for dev, val, production. Okay? So just using one Helm chart, you can make use of in different environments, and you just have to update the values.yaml file depending on the environment that you want to deploy.

**Hussain:**  
Okay. Right, right, right. So there is a term or maybe there is a concept called probes in Kubernetes, right? There are multiple types of probes. Do you have experience working with probes, or you just know what the probes are?

**Ajith:**  
Yeah, I have experience. So in one of the application, we had a liveness probe and readiness probe. These are the two probes that we configured.

**Hussain:**  
How different are they from each other?

**Ajith:**  
So liveness probe is something that will tell that the pod is actively running, it's in the running state. And readiness probe is something that will tell that is the pod ready to serve traffic or not. For example, if there is a pod, you have configured readiness probe in it, and that pod is trying to fetch queries from database, but database is not working. The pod is up and running, but it is trying to fetch query from database which is not running fine. So you have logics in your how you would check your readiness probe and this liveness probe.

**Hussain:**  
Okay. Okay. So there is a typical scenario that most of the times we have faced is we update a particular config in our Kubernetes cluster which is added as an environment variable on your pod definition, right? And the idea is the config should work behind the scenes, right? It should like I change a config and automatically it should percolate, and the application should start working. But it doesn't work like that. Okay? So if I make a change to the config, I need to restart my pod. Okay? So why do you think that this is needed, and how will you overcome this? So basically what I need is if I change a config, behind the scenes my pod should pick up that latest config.

**Ajith:**  
Correct. Yeah. So if you, it depends on how you are mapping your ConfigMap with your pod. If you are just mapping it using the environment variable, that is from env, what pod will do is it will just fetch the values when the pod is starting or restarting. But if you are mapping your ConfigMap as a volume to your pods, that means whenever you're updating your ConfigMap, then it will take the latest values because now you have mapped it as a volume and not just as an environment variable. But also there might be one scenario that your application is configured in a way that it will fetch values from ConfigMap only at the time of starting the pods. So in those scenarios, if the application is configured like that, then you definitely have to restart it, but the solution of mapping it as a volume might solve the problem.

**Hussain:**  
Okay. But what the developers claim is it requires a code change, right? Reading it from an environment variable and reading it from maybe if you add it as a ConfigMap, it needs to be mapped to a certain path, right? Yeah. For a developer, it is a change, right? So that is also one key consideration that we have to make. So that is kind of a tricky situation for us.

**Ajith:**  
Okay, I think that is it for Kubernetes. I think let's quickly jump to Terraform and IaC section. So we had a brief conversation on this versus that, right? Why CloudFormation or why Terraform? Okay? So imagine that you have an enterprise, and they have a Control Tower or maybe a landing zone where there are multiple accounts like 15, sorry, 15 to 20 accounts they have, and they want to deploy their entire infrastructure, their accounts, all new accounts, all the underlying infrastructure using Terraform. So I wanted to understand how would you architect a Terraform directory. Basically, imagine that I am inside the Terraform directory. I want to understand what would be the different folders, what would be the different files, and the requirement would be there would be multiple accounts, under multiple accounts there can be multiple environments as well, and multiple regions as well. So since it is an enterprise customer, the customer will have multiple accounts, multiple regions, and multiple environments. So considering this requirement, how will you kind of have a directory structure?

**Hussain:**  
All right. So as I have the requirements like there are multiple accounts, there are multiple environments, and multiple regions. So first I will try to group them. Let's say we group them as environments and accounts. So my directory structure how it would look like is first I will have, let's say there are three environments: dev, validation, and production. So first I will have three root folders that is dev, val, and prod. And inside dev, I would have directory structure as per the accounts; you can have account name or account number. So in dev directory structure, there will be small different directories of the account number. Let's consider that. Similarly for val and production, I would also have a directory of shared services because there might be an AWS account where there are centralized storages are there. So if that is also one central account, then I'll have one directory of that as well. And fourth directory I will have is for the modules. So what I would do is I won't be writing code for all the accounts, right? So I will make use of modules. And modules also I'll make sure that either we are using AWS-provided modules or we are creating local modules as per our requirement of the organization. And then I would be calling those modules like IAM or network because these are reusable modules in all the accounts. So those modules I'll be calling from the directory structure that I have said, from the accounts.

**Ajith:**  
Mhm. Mhm. Mhm. Okay. Okay. So you are working with, or maybe your organization is working with open-source Terraform or the enterprise or the cloud version?

**Hussain:**  
Currently, you are working with open-source only.

**Ajith:**  
Open-source. So do you face any challenges working with open-source?

**Hussain:**  
Right now we don't because we are managing, let's say, we are managing access management using GitHub. We are storing the remote backend in S3. So for now, I'm not facing any specific challenges. But if we would have used the enterprise, then these things can be taken care by enterprise itself.

**Ajith:**  
Okay. So you mean to say you are using open-source, right? So suppose if I have to deploy an EC2 on a production environment, okay? So you write your code on your local and directly deploy on production, or how is the process like?

**Hussain:**  
No. So if I want to do it on production, definitely I won't be able to do that directly. First I have to go for like dev and production. And even let's consider you want to do it in dev. So there is a CI/CD pipeline which is configured where you store the TF state file in the S3 bucket. So you would first push the code, the pipeline will trigger, it will do all the security scanning, TF lint, fmt, validate, and then it will do Terraform plan. After Terraform plan, it will stop, and it will be reviewed by your senior, and then if it looks good, then only he will approve it, and then it will deploy it on first dev environment. Then you have to raise a change request, you have to go through the processes, approvals for validation and production. And then in the production validation, it will be the same process to push it, get the approval, and then deploy it, and then you merge your CR to main.

**Ajith:**  
Okay. But if your customer says that you have got like 5 minutes, and you want to deploy that infrastructure, so will you still go through all these iterations? And no? So if that is an urgent requirement, then still there will be an approval process. If we have all the approvals, and if you want to do it on production, then you can run directly pipeline on production as well, but it has to go through pipeline process.

**Hussain:**  
Okay. Okay. That is one kind of a challenge that all the organizations face who uses like open-source version, right? When it comes to enterprises, when it comes to Terraform enterprise or cloud, they give you some additional benefits that OSS doesn't provide, right? So okay, that is kind of a big challenge for us as well. So while creating like infrastructure, right, there is also a lot of secret management involved, right? So suppose if you want to create a database or maybe you want to create an EC2, you have to pass your SSH keys right while creating the EC2 instance. If you want to create an RDS instance, I want to use an admin password. So where are these secrets stored, okay? So how will you make sure that these particular secrets are safe and not exposed to the external world?

**Ajith:**  
Correct. So for, let's say if we are creating any RDS and we want to add a username and password there, so either we would use a random function functionality provided by Terraform that it would create a random secret there and there itself, and then it would create an RDS, and that random secret and username and password will store it in the AWS Secrets Manager. So this is how mostly we used to do.

**Hussain:**  
Okay. Okay. But there is a scenario where I don't want my state file to have any sensitive information. This particular random string will create that particular string and store it in the state file, right? Correct. So how will you ensure that it doesn't happen? It's okay if you don't know, but that will happen, right?

**Ajith:**  
Yeah, definitely, yeah. So some organizations will try to keep your Terraform state file secured in a central location. You mentioned at S3, so that is good. But they will try to restrict that particular S3. But there are other alternatives as well, right? So you can still safeguard that particular thing. And there are few hard requirements from the security where they said that even it is okay if you don't automate the entire infrastructure 100%, but our password should not be stored anywhere. In that case, there are other alternatives as well, right? So yeah. So one of the practice that we follow. Yeah. Right. So we work with, so there are few organizations where they are like they give little bit of leeway where it's okay to have secrets in your Terraform state file. There it is okay. But there are organizations like banks or highly regulated industries where they want each and everything to be secured right; they don't care about automation. Automation is to make our lives easy, but their job is to keep everything secure. In that scenario, what we usually do is some secrets we create manually using AWS CLI, and we pass that into the Terraform.

**Hussain:**  
Okay. Okay. So there is a little bit of manual stuff involved. Okay. But as we mentioned that the organization needs to comply with 100% security, so that is kind of an adjustment we have to do or an arrangement we have to do. But yeah, there is nothing right or wrong in that. So according to what your requirement or what your customer requirement is, we have to make changes to our solution.

**Ajith:**  
Okay. So yeah, so we spoke about Terraform state as well, right? So if there are multiple developers, okay, like if there are 10 developers or 10 DevOps engineers working on their local, so how will you ensure, or what is that particular configuration that ensures that you don't jump onto each other's work? Terraform state will store it in a centralized location, but how do you guarantee that so that your changes are not like you are not overstepping on each other's work?

**Hussain:**  
Okay. So we have this trunk-based, first of all, branching strategy that all the code should be in GitHub only. Second thing is the S3, we will be storing the TF state file in S3 itself, and it will make sure that it will be locking the state file whenever one developer is using. So and before the next developer does the apply. But let's say if two developers are working in parallelly, and they don't have to wait for one DevOps engineer to complete their job, so in those scenarios, what we do is we create workspaces, and the workspaces, Terraform state file are in the local only so that you can just test your code, you can do Terraform plan, and you can test your code, and then if things are looking well, then you can raise a PR so that at the time of merge, there we will run the main pipeline once again, and then the actual TF state file will be updated, and then your code will be deployed. But before that, if you want to just test your code, then you can make use of Terraform workspace.

**Ajith:**  
Okay. So you mean to say Terraform workspaces on your local, right? Not the enterprise or the cloud version?

**Hussain:**  
Yeah, yeah, on the local.

**Ajith:**  
Okay. So do you have any information on the enterprise version of workspaces? How they are different from your local?

**Hussain:**  
I'm not, I've not much worked with enterprise-level solution.

**Ajith:**  
That's completely okay. So one of the challenges that I face working with my team is sometimes the infrastructure fails, right? Your Terraform fails, or there is some or the other thing that has not worked as per the expectation. So how do you ensure that it goes to the earlier state, or maybe you roll back? So do you follow any practices to roll back your infrastructure with respect to Terraform, of course?

**Hussain:**  
Yeah, correct. So there are definitely scenarios where your code will pass all the test cases, it will go through Terraform plan well, and then at the time of deployment, it might fail. So first of all, things that we need to check is what are the services that has created or what it has destroyed because there might be a possibility that if partial deployment is done, then the application might suffer or any issues might be there. So first I will, we would check that if there is no issues like that, then what we will do is we would revert back to the older version or older commit, and then we would run the pipeline so that the deployment is reverted first of all, and then we would check that what was the issue and how we can resolve it. Again, it should be done from dev, val, prod. Another automation that we can add is as soon as the Terraform pipeline fails in the workflow itself, we can mention that you should check out to your older version and run the pipeline once again so that we just get notified that the pipeline has failed and the older version is now up and running. So this is something configuration that can be done on the workflow end as well.

**Ajith:**  
Okay. Okay. Okay. Fine. Thanks, Hussain. So I think we have covered AWS, we have covered Kubernetes, a little bit of Docker and Terraform. So I wanted to ask you non-technical questions. Okay? So right now, there is a lot of buzz around AI, right? DevOps or developer jobs are going to cut or anything else. So in your day-to-day activities or day-to-day work, how much part is driven by AI? Okay? So like Hussain works for 8 hours, or maybe he has some x number of tasks. What number is driven by AI or assisted by AI, and what part Hussain does?

**Hussain:**  
Correct. So as we work in enterprise level and also in-house, one of the thing that we have to maintain is the documentation of whatever you do. And so for those things, I completely am dependent on AI. I try my level best to ask the AI to create those documentation, to create all the points, so that and it gives in a really good manner so that I can use it. Second thing, I don't usually use it for development because I know that AI tools hallucinates; it gives wrong answer very confidently. So if I have to create any infrastructure, if I have to deploy anything, so my first place would be to go to documentation. Terraform has a very good documentation, Kubernetes has its own really good documentation. So for development, I usually do it on documentation, on official documentations only.

**Ajith:**  
But the problem with this approach is it will be slow, right? Because I remember creating infrastructure like I have been working with Terraform since like 6 to 7 years now, like from 2018 or 19, I have been working with Terraform or maybe CloudFormation for that matter. So when I started to create a particular multi-account landing zone, I had to maybe I used to take like 15 days, 20 days to script an entire landing zone, right? 10, 12 accounts, CloudTrail configs, multiple EC2 instances, ALBs, or whatnot. But with AI, so I and my team uses a lot of Cursor, okay, and now Anti-Gravity. So we can create the same infrastructure in like a couple of days. Okay? So I understand that you rightly mentioned that it hallucinates; the downsides are already there, but there are few benefits as well, right? So imagine 10 to 15 days of work was cut down into like two days. Okay?

**Hussain:**  
Correct. Yes. But I was able to do that because I had the experience, right? I was able to write the correct prompts, and if the tool hallucinates or it doesn't give the required output, I was able enough to make changes to that. But I think you should start using a little bit of AI in your workflow. I understand that documentation is correct or maybe it is the right place to do it, but I still believe that AI has the potential. It will not replace the entire engineer work, but it can be a good assistance. The problem right now with the mindset is people are kind of relying everything on the AI. Yeah. So that is kind of a problem. But yeah, maybe you'll get more confidence in AI, and you should start working with tools like Cursor. Do you use any tools like Cursor or Anti-Gravity or Cloud load?

**Ajith:**  
No, as of now we don't use any of them.

**Hussain:**  
I will request you to or maybe recommend you to use Cursor at least. Start with Cursor, then maybe you can try other tools. So you'll certainly like it. Okay? So apart from that, you are currently working as a cloud engineer or a DevOps engineer, right? So what are your aspirations like in next 5 years? Where do you see yourself like you want to continue doing hands-on DevOps work, or you want to get into management kind of an architect-level role? So what are your next five-year plans?

**Ajith:**  
Next at least for 3 years, I would say I still want to be a DevOps engineer hardcore where I have all the technical knowledge and not go into manage level. But if you say 5 years, then definitely I would look myself as a solution architect which can architect every solution, and I should be fully knowledgeable. So it should go like if Hussain has said this should be done, then it should be done. So I have to reach there. And to reach there, I have to rigorously be first very much skilled DevOps engineer in the era of AI, as you said that you have to adapt to AI to reach there. So after doing that, maybe after 5 years, I will be at a solution architect level where still I want to stay connected with the technology, not just manage things and get things done, but I want to create architectures and I want to work as a like hardcore engineer.

**Hussain:**  
Okay. Okay. So even with solution architect, sometimes people kind of misinterpret the role of an architect. Okay? So I worked as an architect for six years, and for all six years, I was doing hands-on work. Okay? So there is a thin line between an engineer and architect. So engineer is something who actually do the hands-on work. An architect is someone who can do the solutioning, who can create beautiful diagrams and create the entire ecosystem, but he also needs to be hands-on just in case if required, right? So that is where it needs to go.

**Ajith:**  
Okay. Yeah, apart from that, one last question. So I see a lot of tussle between DevOps engineers and developers, right? So how will you ensure that the friction between you as a DevOps engineer and the developer is reduced, and the work is not compromised?

**Hussain:**  
Correct. Yeah. So our position is also like that it's DevOps, that is developers and system that that consists of this developers and operations. So definitely there is a lot of tussle that this work should be done by developers, no, this work should be done by DevOps. So we usually face that issue, but this is something where we both have to be knowledgeable in on each other's task. Let's say if anyone wants to deploy anything on Kubernetes, then I also have to know how the APIs work inside the application, and the developers also should have some knowledge on how Kubernetes work. So this is again from both ends, we have to be knowledgeable. Of course, in the next industry, if you're not that skilled enough, it is very much hard for you to survive. So and also here is where the tech lead comes into picture. Your manager comes into picture, and he lays down the task, and he makes sure that we are working as one team and not a different handover task. We have to make sure while developing anything, I also have to be there, and while developing CI/CD pipelines and deployments, the developer also should be somewhat knowledgeable on how things are done.

**Ajith:**  
Right. Right. Yeah. Yeah. That was a good answer, Hussain. So thanks a lot for taking this interview and taking out time for this mock interview. I think a lot of people will benefit out of this conversation. Anything you would like to ask me, or anything that comes to your mind, or maybe we can wrap up.

**Hussain:**  
Yeah, first of all, thank you so much for having this and taking your time out as well. I even hope that people get most out of the interviews that we are doing. One question I would like to ask you that you have been 14 years of experience, so what is your next goal like after 5 years or 10 years? How do you see yourself, and how do you see as a DevOps industry how it will grow in next 5 years, in next 10 years? What advice would you give for freshers who wants to build a career in DevOps?

**Ajith:**  
Yeah. Yeah. So, I'll answer this question in general, right? Not specific to DevOps, right? When I started working, I started like in the introduction, I mentioned that for the initial six to seven years, I was into software development. When I was into like four to five years, I was like fascinated like with designations like I used to feel like managers, directors, and I thought that I'll also become a manager or a director one day. But right now, I'm leading a team of 30 technical people right, but I'm still doing 3 to 4 hours of hands-on work. I will consider myself successful over the next 5 to 7 years if I'm able to maintain that 4 to 5 hours of hands-on job, okay, hands-on work. So I consider people should not worry too much about the designation. With the advent of AI, I think every single person needs to stay hands-on, or they will get absolute. Okay? So that is going to happen for sure. You will see a smaller number of teams, right? So initially with big companies, you used to see thousands and thousands of engineers, but it is slowly changing. Okay? So there are startups with like 5 to 10 engineers, and they are doing multi-million dollars of business. So that is going to happen over the next 5 years. I believe a person should have at least basic information or basic knowledge of all the aspects. And with the help of AI, they can learn other stuff as well. Right? So if you ask me, full-stack is the need of the hour. So a person needs to understand front-end, back-end, databases, and cloud and DevOps. So even it is okay if they are not expert in a particular area, but they need to understand all the stuff. And with AI coding tools and other new tools that coming up in the market, they can write software, they can create enterprise-grade solutions. It is not there yet, but maybe in a couple of years, it can reach that set. Having said that, it is going to give you problems. It is going to fail in production. It maybe it will not work, but you should be having that capability to make changes to that AI-written code. Okay? That is what I said. There are a lot of people who do a lot of AI coding. So at the MVP stage, they are like very successful, but when it hits production, they start to face scaling issues, they start to fail security issues. That is where the main challenge or your experience comes into picture. Okay? So the people with no programming experience or no DevOps experience or no software engineering experience will fail over there. And we need to make sure that at least we should be able to make changes or update the code that AI has written. Okay? So to sum it up, I would say that I stay hands-on over the next 5 years regardless of where I am or what kind of a designation I am in, but I still want to keep hands-on. That is what I can say. Hope I was able to answer your question.

**Hussain:**  
Yes. Yes, definitely. Yeah. All right. Hussain, it was a good time talking to you. Maybe we'll catch up later.

**Ajith:**  
Thank you. Sure. Yes. Thank you so much.