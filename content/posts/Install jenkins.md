---
title: "How to Install Jenkins on Ubuntu"
date: 2024-01-18T04:06:22Z
author:
authorLink:
description:
tags:
- Jenkins
- Install
- Ubuntu


categories:

draft: false
hiddenFromHomePage: true
---

# Install Jenkins on Ubuntu-22.04

## Prerequisites

### Minimum hardware requirements:

* 256 MB of RAM

* 1 GB of drive space (although 10 GB is a recommended minimum if running Jenkins as a Docker container)

#### Commands for Installing Jenkins on Ubuntu 22.04

* `sudo apt update`
--- 
* `sudo apt install openjdk-17-jre`
---
* `java --version`
---
* `curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \\n  /usr/share/keyrings/jenkins-keyring.asc > /dev/null`
---
* `sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \\n  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key`
---
* `echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \\n  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \\n  /etc/apt/sources.list.d/jenkins.list > /dev/null`
---
* `sudo apt update`
---
* `sudo apt install Jenkins`
---
* if getting some error during installing Jenkins on ubuntu troubleshooting it with below commands.
---
* `cat /etc/apt/sources.list.d/jenkins.list`
---
* add key `wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -\n`
---
* again run `sudo apt install jenkins`
---
* `sudo systemctl start Jenkins` or `/etc/init.d/jenkins start`
---
* `sudo systemctl enable --now jenkins`
---
* `sudo ufw allow 8080`
---
* `sudo ufw enable`
---
* `sudo ufw status`
---
* Now open Jenkins on your browser using `http://localhost:8080`
---
* now give the password which are stored in this location `sudo cat /var/lib/jenkins/secrets/initialAdminPassword` 
---
* Copy that and paste on the browser 
---
* New page opens here create new username and password for login to Jenkins.

{{< image src="/img/credentials/jenkins-install.png" caption=" follow the instruction ">}}