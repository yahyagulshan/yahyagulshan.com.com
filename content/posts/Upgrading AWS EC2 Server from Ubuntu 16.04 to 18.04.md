---
title: "Upgrading AWS EC2 Server from Ubuntu 16.04 to 18.04"
date: 2023-09-09T04:06:22Z
author:
authorLink:
description:
tags:
- Update
- Ubuntu 16.04
- Ubuntu 18.04
categories:
- Tutorial
draft: false
hiddenFromHomePage: true
---

## Before proceeding with the upgrade

Before proceeding with the upgrade, ensure that you have taken a backup of your server. This is a critical step to prevent data loss in case of any issues during the upgrade.


***
## Login to the AWS Console:
Access your AWS account and navigate to the EC2 dashboard.

***

## Create an AMI (Amazon Machine Image):
Select the EC2 instance that you want to upgrade.
Click on the "Actions" button and choose "Image" > "Create Image."
Follow the prompts to create an AMI of your EC2 instance. This is your backup image.

***


## SSH into the Server:

Once the AMI creation is completed, SSH into your EC2 server using your preferred terminal.

## Check Available Disk Space:

Before proceeding with the upgrade, it's essential to check the available disk space.
Run the following command to check disk space:

`df -lh`

## Perform the Upgrade:

Run the following commands to upgrade your Ubuntu server:
Update package lists:
`sudo apt-get update`
Perform a distribution upgrade:
`sudo apt-get dist-upgrade`
Install the update manager core:
`sudo apt-get install update-manager-core`
Initiate the release upgrade:
`sudo do-release-upgrade`
Follow all instructions provided during the upgrade procedure and carefully monitor each step.

## Restart the Server:

After the upgrade is complete, a system restart is required.
Confirm by pressing "yes" to complete the procedure.
Once the server restarts, your Ubuntu upgrade is complete.

## Check the Ubuntu Version:

To verify that the upgrade was successful and your system is now running Ubuntu 18.04, run the following command:
`cat /etc/os-release`

By following these steps, you can safely and effectively upgrade your AWS EC2 server from Ubuntu 16.04 to Ubuntu 18.04. Remember to back up your data and exercise caution while upgrading to avoid any data loss or service interruption.
