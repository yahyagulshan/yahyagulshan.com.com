---
title: "How to install Kubernetes"
date: 2024-01-18T04:06:22Z
author:
authorLink:
description:
tags:
- Kubernetes
- Install
- Minikube

categories:

draft: false
hiddenFromHomePage: true
---

# Install Kubernetes on Ubuntu

* `sudo apt update -y`
* `curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64`

### Install Minikube 

* `sudo install minikube-linux-amd64 /usr/local/bin/minikube`
* `minikube version`
* `curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"`
* `chmod +x ./kubectl`
* `sudo mv kubectl /usr/local/bin/`
* `kubectl version --client --output=yaml`
*  `minikube start --vm-driver docker`
* `sudo usermod -aG docker $USER && newgrp docker`
* `minikube start --vm-driver docker`
* `minikube status`
* `kubectl cluster-info`
* `kubectl get nodes`
* `minikube addons list`
* `kubectl config view`
* `minikube dashboard` (It will open the Kubernetes dashboard in the web browser.)
* To stop the minikube, run `minikube stop`
* To delete the minikube, run `minikube delete`
* To Start the minikube, run `minikube start`
