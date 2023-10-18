---
title: "Creating openvpnserver and connect with local"
date: 2023-01-31T04:06:22Z
author:
authorLink:
description:
tags:
- OpenVPN
- Local

categories:
- OpenVPN
draft: false
hiddenFromHomePage: true
---

***

## Setting Up OpenVPN on AWS

***

### Step 1: Launch an EC2 Instance

Open the AWS Console.
Navigate to the EC2 service and click "Launch an Instance."

{{< image src="/img/openvpn/openvpn.png" caption="this is a Example of EC2 Launch Instance">}}

***

## Step 2: Select an OpenVPN AMI

In the "Browse for AMIs" section, search for "OpenVPN."
Choose an OpenVPN Amazon Machine Image (AMI) from the AWS Marketplace.


{{< image src="/img/openvpn/EC2.png" caption="this is a Example of AMI ">}}

## Step 3: Choose the First AMI

Select the first available OpenVPN AMI.
Click "Continue."

{{< image src="/img/openvpn/openvpami.png" caption="this is a Example of AMI ">}}

{{< image src="/img/openvpn/continoue.png" caption=" Click Continoue ">}}

***

## Step 4: Instance Configuration

Configure your EC2 instance settings as needed.
Create or select an Elastic IP for your instance. `This is essential for a stable connection.`

## Step 5: SSH into the Server

SSH into the newly created EC2 instance following the instructions provided in the screenshot.

{{< image src="/img/openvpn/follow1.png" caption=" follow the instruction ">}}

{{< image src="/img/openvpn/follow2.png" caption=" follow the instruction ">}}



***

## Step 6: Set Password for User 'openvpn'


After connecting to the server, set a password for the 'openvpn' user as per the screenshot's instructions.

{{< image src="/img/openvpn/setpassword.png" caption=" Set password ">}}

***

## Step 7: Access the OpenVPN Admin UI

Open the URL provided in the last step.
Access the Admin User Interface.
Enter your username and password when prompted.
Accept the terms and conditions.

{{< image src="/img/openvpn/openurl.png" caption=" Open URL ">}}

***

## Step 8: Establish a VPN Connection

Open your web browser and navigate to the provided URL (e.g., https://3.134.251.144/).
You'll be redirected to a login page.
Select your user-locked profile.

{{< image src="/img/openvpn/pressagree.png" caption=" Press agree ">}}

***

## Step 9: Download the Configuration File

Download the VPN configuration file to your local system.


{{< image src="/img/openvpn/chooseyoursystem.png" caption=" Choose Your System ">}}


After downloading, rename the file to `'user1.ovpn.'`


***

## Step 10: Connect to the VPN

Go to your local system and open the terminal.
Run the following command to establish the VPN connection:

`sudo openvpn --config /home/yahya/Downloads/yahyavpn1.ovpn`

Provide your username and password when prompted.

***

## Step 11: Verify the Connection

Your IP address should now be changed and static, indicating a successful VPN connection.
By following these steps, you can set up OpenVPN on an AWS EC2 instance and ensure secure and private internet access.

<!-- ########################## -->
<!-- #- **Azure DevOps:** [Setting up branch policy settings](https://learn.microsoft.com/en-us/azure/devops/repos/git/branch-policies?view=azure-devops&#tabs=browser)
#- **GitHub:** [Setting up status check policy](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/#defining-the-mergeability-of-pull-requests) -->