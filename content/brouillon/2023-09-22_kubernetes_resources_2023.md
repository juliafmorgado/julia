---
title: ""
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


# A Master List of Resources for Learning Kubernetes 

## The Best Resources for Learning Kubernetes from Scratch
Kubernetes is the world’s leading container orchestration platform. Its cloud agnostic status enables you to manage your workloads with ease, whether they reside in the cloud or on-premises. It has reduced the necessity of being locked into services provided by a cloud provider as well as the need for an entire operations team to manage large workloads on-premises on virtualization platforms. Because Kubernetes is so useful and popular today, having the skills to work in this platform is critical in the DevOps world. This article presents a number of resources, organized by topic, intended to help you learn Kubernetes or brush up on your K8s skills.

General Introduction to Learn Kubernetes
The following links are good resources for gaining a better understanding of the concepts behind Kubernetes.

What is a Container?  by Docker

Before you work with Kubernetes, you need to understand the concepts behind the use of containers, including what problems they solve and why you should adopt them. This article explains these concepts and provides a good general overview of the platform.

Why (and when) you should use Kubernetes by Fahim ul Haq, Hackernoon

This article explains what container orchestration is, how Kubernetes came into the picture, and what problems Kubernetes helps solve.

A Beginner’s Guide to Kubernetes by Imesh Gunaratne, Container Mind

This article explains container orchestration, the architecture and components of Kubernetes, and the resources you will be dealing with in Kubernetes. As its title suggests, this is a great article for beginners to read in order to get started. 

Understanding the Kubernetes YAML Syntax by Ryan Pivovar, Better Programming

Kubernetes configurations are written in YAML format, making it important for you to understand how to write YAML syntax before starting to deploy applications.

Managing and Configuring Kubernetes Clusters
Once you have an overall understanding of Kubernetes, you need to learn how to set up and manage Kubernetes clusters. These resources address how to set up and run managed versions of Kubernetes and how to do a manual set up of Kubernetes from scratch.

Kubernetes Tutorial – Step by Step Introduction to Basic Concepts by Bruno Krebs, Auth0

This guide by Auth0 provides an overview of all the major cloud vendor solutions for Kubernetes and provides an in-depth guide to setting up a Kubernetes cluster using DigitalOcean.

Deploying a Kubernetes Cluster with Amazon EKS by Daniel Berman, Logz.io

This article provides details on how to get started with Kubernetes using Amazon Elastic Kubernetes Engine.

Kubernetes as a Service: GKE vs. AKS vs. EKS by Evan Klein, Logz.io

This article provides you with a comparison of the Kubernetes services provided by the three major cloud providers—Google, Azure, and AWS. This comparison can help you decide which Kubernetes service you should use for your next project.

Quickstart – Create an Azure Kubernetes Service (AKS) using the Azure portal by Microsoft Azure

This article guides you through the process of setting up a Kubernetes cluster in Microsoft Azure.

Google Kubernetes Engine; Explain Like I’m Five! By Aymen El Amri, Faun

This is a very effective guide to Google Kubernetes Engine. The author explains how to get started in a step-by-step manner. This is a great article if you are just starting out with Google Cloud Platform.

Kubernetes on CentOS 7 with Firewalld by Nilesh Jayanandana, Platformer Cloud

Managing Kubernetes on a cloud-provided service is easy. Managing it by yourself is a different game altogether. This article provides a guide to setting up a Kubernetes cluster from scratch on CentOS.

Configuring HA Kubernetes cluster on bare metal servers with kubeadm By Alexi Nixhegolenko, Medium

This article series provides a guide to setting up Kubernetes on bare metal Ubuntu servers.

Comparing Kubernetes Networking Providers: Flannel, Calico, Canal, and Weave by Justin Ellingwood, Rancher

When running Kubernetes clusters by yourself, you need a thorough understanding of the available Kubernetes network providers in order to decide which ones to use in your cluster. This article provides you with that information.

Deploying Applications and Services
We run Kubernetes to deploy applications on it. The links in this section will discuss how to run various workloads on Kubernetes.

Kubernetes 101: Pods, Nodes, Containers, and Clusters by Daniel Sanche, Medium

This article introduces the main resources and concepts required to run applications and services on top of Kubernetes.

Kubernetes Deployment Tutorial with YAML by Matthew Palmer

This short tutorial helps you get started deploying a simple application on Kubernetes.

What Is a Service Mesh, and Why Do You Need One? by Daniel Berman, Logz.io

Microservice architectures can get complicated, as can trying to monitor them. Service meshes take the cacophony and turn it into a symphony. Get the low-down from Daniel Berman on these tools and how they relate to Kubernetes.

Istio vs. Linkerd vs. Consul: A Comparison of Service Meshes by Gedalyah Reback, Logz.io

This continues the theme of the last article, but takes a more detailed dive into comparing the three major service meshes on the market.

Getting external traffic into Kubernetes – ClusterIp, NodePort, LoadBalancer, and Ingress by Horacio Gonzales, OVHcloud

This article discusses how to expose your applications as services on the internet, what the different service types are, and how to map dns domains to services using ingress resources.

Enable Rolling updates in Kubernetes with Zero downtime by by Nilesh Jayanandana, Platformer

This article discusses how to enable zero downtime updates on deployments in a Kubernetes cluster.

Kubernetes – Autoscaling by tutorialspoint

This tutorial examines autoscaling with Kubernetes. This is an in-depth guide that introduces you to the Kubernetes resource objects HorizontalPodAutoscaler and VerticalPodAutoscaler.

Kubernetes Helm 101 by Huy Du, Dwarves Foundation

Helm is a package manager for Kubernetes which allows you to deploy pre-built application stacks on top of Kubernetes. This guide explains how to get started with Helm deployments in Kubernetes.

Kubernetes ConfigMaps and Secrets by Sandeep Dinesh, Google Cloud Community

Every application has configuration files and environment variables associated with it. This article explains how to mount configuration files and provides an overview of environment variables in any Kubernetes deployment.

Deploy your first scalable PHP/MySQL Web application in Kubernetes by Adnan Sidiqqi, Faun

This article provides a definitive guide to deploying a PHP/MYSQL based web application on a Kubernetes cluster.

Logging and Monitoring Kubernetes
Monitoring and Logging are integral parts of every production grade system. They enable engineers and DevOps staff to receive system status updates, debug issues, and maintain system sanity. The following articles discuss the main tools used for monitoring and logging in Kubernetes.

A Practical Guide to Kubernetes Logging by Daniel Berman, Logz.io

Managing logs is essential in any system. This definitive guide gives you details on how to handle application- and cluster-level logs in Kubernetes.

Kubernetes Log Analysis with Fluentd, Elasticsearch and Kibana by Roi Ravhon, Logz.io

A continuation of the previous article, this resource focuses on the ELK Stack. It explains how you can effectively stream logs with Fluentd into Elasticsearch and visualize them in Kibana.

Kubernetes Monitoring: Best Practices, Methods, and Existing Solutions by Daniel Berman, Logz.io

This article provides an overview of the Kubernetes monitoring stack and describes the existing tools and solutions available for various use case requirements.

Logging Kubernetes on AKS with the ELK Stack and Logz.io by Daniel Berman, Logz.io

Logging Kubernetes on GKE with the ELK Stack and Logz.io by Daniel Berman, Logz.io

These two give you a basic tutorial for monitoring AKS and GKE with open-source ELK Stack and with the Logz.io managed monitoring solution.

Production grade Kubernetes Monitoring using Prometheus by Vaibhav Thakur, Faun

Prometheus is one of the most popular tools in the modern stack used to monitor applications running on Kubernetes. This article provides a guide to setting up Prometheus with Kubernetes.

Storage
Applications often require a persistent layer to handle storage. Containers running on Kubernetes are no exception. The following articles discuss options for managing storage in Kubernetes.

Understanding Kubernetes storage basics by IBM Cloud

This article will help you learn Kubernetes practices for handling the persistence layer in an application.

Kubernetes: How to Actually Do StatefulSets by Devin Hurley, ITNext

This article discusses how to deploy stateful applications in Kubernetes as a StatefulSet resource.

Kubernetes – Volumes by tutorialspoint

This guide discusses the various volume types that exist in Kubernetes and how to mount them onto containers.

Security
kubernetes security
Security is an important factor in any environment. This section lists some resources for better understanding the implementation of Kubernetes security.

How to Secure a Kubernetes Cluster, by Daniel Berman, Logz.io

This is a critical topic. Kubernetes clusters are a constant but necessary headache for DevOps teams. This introduces you to making sure that the framework is secure.

Kubernetes Security Best Practices by Asaf Yigal, Logz.io

Our CTO takes to the blog to go over the most essential practices and how to best apply them when doing Kubernetes security.

Kubernetes Security — Are your Container Doors Open? by Gourav Gulati, Faun

This article discusses how to secure your containers and Kubernetes deployments. It’s a great starting point for a beginner.

Kubernetes and Security by Rohit Mathur, Faun

This article discusses Kubernetes security in general as well as the key factors to be considered when assessing Kubernetes security.

OPA Gatekeeper: Policy and Governance for Kubernetes by Kubernetes

Open Policy Agent is a popular Kubernetes plug-in which enables you to enforce policies to your Kubernetes users.

In that case you might be interested in kube-hunter, an open source Kubernetes penetration testing by Liz Rice

This article is about kube-hunter, the popular Kubernetes penetration testing tool which helps you to audit your cluster.

Seccomp in Kubernetes — Part I: 7 things you should know before you even start! by ITNext

In this two-part blog series, the author discusses a few gotchas in Kubernetes security and best practices that should be followed in a production grade Kubernetes cluster.

Playgrounds / Sandboxes
As a newcomer to Kubernetes, you will definitely need a Kubernetes playground in which to build and break things. These are a few of the resources that provide playgrounds.

Getting started with MicroK8s
Getting Started with Kubernetes using MicroK8s by Daniel Berman, Logz.io

Running Kubernetes on the cloud is easy, but it can be expensive. If you want to do a test run locally on your development machine, this article on MicroK8s explains how to do that.

Katacoda – Interactive Learning Platform for Software Engineers by Katcoda

This is one of the best online playgrounds to run and test Kubernetes. They even have free labs and tutorials for you to try out.

Setup Kubernetes with Minikube on a Bare Metal Server by Scaleway Elements

You can convert your development machine to a Kubernetes playground by installing Minikube. To do so, follow the instructions in this article. The previously mentioned MicroK8s only works with Ubuntu servers, but Minikube works with any OS distribution.

Conclusion
Kubernetes is not something you can master in a day—or even in a week. It requires you to learn the concepts properly and apply those concepts practically in a real-world project, so be patient as you make your way through these resources. 

There are two Kubernetes certificates that you can earn: Certified Kubernetes Administrator and Certified Kubernetes Application Developer. Both of these require that you take practical exams; to pass them, you have to have some Kubernetes experience. The above resources will help you on that journey.

As of the time of this article’s publication, Microsoft is making the book Kubernetes Concepts and Deployment free for a limited time. Take advantage of this offer while you can, since it is another very good resource.

Good luck with the learning process!

***
If you liked this article, go follow me on [Twitter](https://twitter.com/juliafmorgado) (where I share my tech journey) daily, connect with me on on [LinkedIn](https://www.linkedin.com/in/juliafmorgado/), check out my [IG](https://www.instagram.com/juliafmorgado/), and make sure to subscribe to my [Youtube](https://www.youtube.com/c/JuliaFMorgado) channel for more amazing content!!
