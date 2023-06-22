---
title: "AWS Best Practices from the Ground Up"
author: "Julia Furst Morgado"
date: 2023-xx-xxT17:46:05.964Z
draft: true
cover:
    image: img/100devs.png
tags: 
    - Microsoft
    - Certification
    - Azure
categories: 
    - Tech
description: This is the subtitle that is used for SEO and visible in Medium and Hashnode posts.
slug: /why-I-failed-microsoft-exam


image: 
# images: img/profile.jpg (twitter card)

# toc : true (table of content)
# series: - series-name (enable series)

aliases:


---

Check out my Youtube videos about 100Devs: [How to join 100Devs](https://www.youtube.com/watch?v=MhUAKpF47GU) and [What is 100Devs](https://www.youtube.com/watch?v=HHAXlDu49rE)

![](https://blog-imgs-23.s3.amazonaws.com/iam-iamic.png)


Not sure how many of these are “horror” stories, just make sure you have the best practices figured out before you get in too deep:

Embrace a multi-account architecture and AWS Organizations and Control Tower from day one. It is pretty simple to setup in a greenfield deployment, but a PAIN to implement later.

Get SSO figured out early and get your engineers used to the SSO workflow for console access and API keys. It isn’t difficult once you are used to it, but it can be a battle to convince someone to give up their long-lived IAM user account and access key (and the security risks that come with it).

Follow the best practices on the root user on day one (e.g. MFA). Make sure no one is actively using the account (ever), and it isn’t tied to an employee’s individual email.

Get multi-account security services like GuardDuty, Security Hub, and Firewall manager in place before you start creating a bunch of accounts. (CloudTrail and AWS Config should already be setup if you use Control Tower.)

Get an Infrastructure as Code tool like CloudFormation or Terraform established right away so that becomes the de facto way of working with the account. It instills good habits and saves you the pain of trying to re-implement a bunch of hand-created resources!

Embrace the cloud design patterns (auto scaling, load balancers, automation). If you see the cloud as just another place to run VMs you are doing it wrong.

Make sure you understand availability zones, subnets (public vs private), network ACLs, and Security Groups before you start launching things. It’s hard to move things between subnets and AZs without downtime, so it’s a good idea to think about where you are launching resources. Control Tower will get you setup with a sane subnet/AZ architecture in the beginning.

Figure out monitoring and alerts. The simplest thing to do is send email alerts. You don’t want those alerts going to the mailbox of a single employee. Make a shared email address (e.g. alerts@company.com) and start using that. You can improve things later but get SOMETHING in place.

Implement budgets and billing alerts. If you don’t know how much your expected spend is, take a wild guess and put in a number.

Make sure each account has a non-overlapping IP range when you create it. This will pay off later whenever you try to connect two accounts/regions. Keep track of the IP blocks allocated to each AWS account somewhere (e.g. wiki page).

Related to the previous one, avoid using the default VPC (Control Tower and Account Factory helps).

Think about how you are going to securely access instances in your VPC (VPN, session manager, bastion host, etc.). Lots of EC2 instances get hacked because an AWS novice opened up SSH or RDP!

None of these are complicated or expensive. A one person team with a near $0 budget can do it. But if you don’t take care of them upfront, it can be difficult to retrofit later.

***
If you liked this article, go follow me on [Twitter](https://twitter.com/juliafmorgado) (where I share my tech journey) daily, connect with me on on [LinkedIn](https://www.linkedin.com/in/juliafmorgado/), check out my [IG](https://www.instagram.com/juliafmorgado/), and make sure to subscribe to my [Youtube](https://www.youtube.com/c/JuliaFMorgado) channel for more amazing content!!
