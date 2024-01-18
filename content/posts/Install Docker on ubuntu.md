---
title: "How to install Docker on ubuntu-22.04"
date: 2024-01-18T04:06:22Z
author:
authorLink:
description:
tags:
- Docker
- Install


categories:

draft: false
hiddenFromHomePage: true
---
# Install Docker on Ubuntu 22.04

* for install Docker on ubuntu machine need to update the system.
---
* `sudo apt-gte update`
---
## 1- Set up Docker's apt repository.

---
* Add Docker's official GPG key:
---
`sudo apt-get update`
`sudo apt-get install ca-certificates curl gnupg`
`sudo install -m 0755 -d /etc/apt/keyrings`
`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg`
`sudo chmod a+r /etc/apt/keyrings/docker.gpg`

---
* Add the repository to Apt sources:
---

`echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \`
 ` sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
 `sudo apt-get update`

---
* Install the Docker packages.
---
`sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin `

---
* Verify that the Docker Engine installation is successful by running the hello-world image.

`sudo docker run hello-world`