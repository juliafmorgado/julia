---
title: "How to Build a Web App on AWS with AWS Amplify, Lambda, DynamoDB and API Gateway"
author: "Julia Furst Morgado"
date: 2024-02-27T10:46:05.964Z
draft: true
cover:
    image: https://blog-imgs-23.s3.amazonaws.com/how-to-pass-kcna.png
tags: 
    - AWS
categories: 
    - Tech
slug: /how-to-build-web-app-aws
---

Are you new to AWS? — This tutorial is designed for YOU.

In we will create a super simple web application and learn how to deploy it to a virtual Linux server on AWS.

It will teach you the basics of the complete software development lifecycle, and will make you understand each step in the complete workflow and what goes into that.

Welcome to step-by-step guide to building a web application using AWS
In this article, I will show you how to build a simple web application on AWS. First, we will create a static web application that displays “Hello World.” Then, we will discover how to incorporate different AWS features into the web application and see how they work together. 

This project is an excellent introduction to the cloud computing platforms. If you are new and just getting into cloud services, don’t worry. It’s never too late to start learning something new. I am glad you made it here. 

In this project, as you can guess from the title, we will use AWS, which stands for Amazon Web Services; an excellent cloud platform with endless services for so many various use cases from training machine learning models to hosting websites and applications (Around 200 AWS services are available as of writing this article). 

This is what we're going to do and you can go ahead and challenge yourself to do it by yourself first and then check the tutorial to see the answers.

- Step 1: Deploy code on AWS Amplify
- Step 2: Create an AWS Lambda Serverless function, test it and connect it to the web app
- Step 3: Create Rest API with API Gateway
- Step 4: Create DynamoDB table
- Step 5: Set up IAM Policies and Permissions
- Step 6: Update frontend code with Rest API

## Step 1: Deploy code on AWS Amplify

In this step, we will learn how to deploy static resources for our web application using the AWS Amplify console. 

Basic web development knowledge will be helpful for this part. We will create our HTML file. Here is the code snippet of the page:




