---
title: "jenkins-kubernetes-pipeline"
date: 2024-01-14T04:06:22Z
author:
authorLink:
description:
tags:
- Kubernetes
- Docker
- Jenkins
- 
categories:
- OpenVPN
draft: false
hiddenFromHomePage: true
---

# Jenkins Kubernetes Pipeline for Containerized PHP Web Application - A Step-by-Step Guide

* In this blog post, we'll walk through the process of setting up a Jenkins pipeline to containerize a PHP web application and deploy it to Kubernetes Minikube. Before we dive into the details, make sure you have the following prerequisites in place:

* for creating all the steps follow this repos [Access the GitHub repo here](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline)

# Prerequisites

1- Installed Jenkins on the local system or any VM. [how to install Jenkins](https://www.jenkins.io/doc/book/installing/)
     
[for add credentials](https://www.jenkins.io/doc/book/using/using-credentials/#:~:text=From%20the%20Jenkins%20home%20page,Add%20Credentials%20on%20the%20left.) 
     
[for jenkins plugins](https://www.jenkins.io/doc/book/managing/plugins/)

2- Installed Kubernetes minikube. [how to install](https://kubernetes.io/docs/setup/)

3- Installed Docker.[how to install](https://docs.docker.com/engine/install/)

4- Make sure Jenkins has a connection with Kubernetes  [how to make connection](https://medium.com/@devayanthakur/minikube-configure-jenkins-kubernetes-plugin-25eb804d0dec)

5- DockerHub Repository:
Have a DockerHub repository ready to store your Docker images.

# How to configure Jenkins Project

* after installing Jenkins open it on Browser.

   ---
 ![Screenshot from 2024-01-12 18-39-04](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/9e68ad15-43a1-443e-bae9-407e5d03b8f7)

* click on manage jennkins

  ---
![Screenshot from 2024-01-12 18-40-31](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/9da07e5e-6d19-423d-9e79-ad16ccc5f9d4)

* click on  Credentials

  ---
 ![Screenshot from 2024-01-12 18-41-53](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/c97d975c-f2be-4cac-8bab-f1aa2c755308)

* then add credentials for Dockerhub and Kubernetes and GitHub. (for GitHub password should be "token")

* After creating the credentials create Pipeline for that click on newItem

---
 ![Screenshot from 2024-01-12 18-46-08](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/ed35b900-1c74-42dc-b5ca-22e426aeb537)

* then give suitable name click on "pipeline" and press "ok"

---
 ![Screenshot from 2024-01-12 18-47-24](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/1372fcae-3936-48d3-ab24-093606de9cb6)

* new page open open click on Github project and give the link of github repo ![Screenshot from 2024-01-12 18-49-45](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/3a159ae1-cb14-41b9-ad2f-52e16a490059)

* In the last "Pipeline" section in `defination` select "pipeline script fo SCM". In repository again give the github repo link. for credentials select "none". in "branches to build" give your branch name and then save.
![Screenshot from 2024-01-12 18-52-08](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/102837de-a251-45a7-bb37-ab510899e10d)![Screenshot from 2024-01-12 18-56-40](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/f24dbd03-7f3e-4cda-8987-b56351a2fa5d)

* now press "build now"

---
![Screenshot from 2024-01-12 20-11-36](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/d6780edf-9ffb-4664-9484-59f8899ab2a9)

* pipeline should be running

---
![Screenshot from 2024-01-12 20-12-54](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/ce50cbd9-3af6-4144-8d93-c380941f0f8e)

 * this repo we have `Dockerfile` and `index.php` file. these files are for creating php web page.
![Screenshot from 2024-01-11 21-15-00](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/fb7ab2cc-ca83-40a7-8e4b-af814cfc8937)

# Important Note (To run the auto-trigger pipeline our Jenkins should be on a Public host like "EC2" )
* For auto trigger we need to create a webhook on the GitHub repo because the webhook needs to communicate over the public IP.

# Steps for autotrigger pipeline
* First we need to create the webhook on our GitHub repo for this go to setting > webhook > Add webhook 

---
![Screenshot from 2024-01-13 00-44-10](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/abf5cd71-27d5-4904-adfa-60fcd602ac6e)

* here give the info Jenkins "Ec2" publicIP with "8080" Port and click add webhook.

---
  ![Screenshot from 2024-01-13 00-46-18](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/434e680b-cb46-4cd0-97a2-9bf93dbd543b)

* Now go to Jenkins open the Project click on "configure"

  ---
  ![Screenshot from 2024-01-13 00-49-12](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/bdbc72d0-c0e3-4d6c-9a04-cfacd666569a)

* configuration page opens here find "Build Triggers" and click on "GitHub hook trigger for GITScm polling"

 ---
 ![Screenshot from 2024-01-13 00-50-25](https://github.com/yahyagulshan/jenkins-kubernetes-pipeline/assets/59036269/d0a1ca88-66d0-4710-a3dc-3cb6d3fc2158)

 * Now when we commit new changes on Github with the Specified Branch our Jenkins pipeline should trigger automatically.

# Jenkinsfile Overview

The Jenkinsfile orchestrates the pipeline:

* 1- Builds the Docker image.
* 2- Pushes the image to the DockerHub repository.
* 3- Deploys the image to Kubernetes Minikube.

# Note: Customize the Jenkinsfile

* Change the DockerHub credentials in line #16.
* Update the username in line #17.
* Change the Kubernetes credentials in line #28.

# Kubernetes Manifest File (deployment.yaml)

The `deployment.yaml` file creates a Pod and Service in Kubernetes Minikube.

# `account.yaml ` File Details: 

* This file is used for creating a service account with the secret for the Kubernetes-plugin in Minikube.

* Feel free to adapt these files and configurations based on your project requirements. Happy coding! 🚀

