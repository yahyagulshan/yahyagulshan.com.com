---
title: "Configuring Firewall Rules in Google Cloud (GCP)"
date: 2023-09-09T04:06:22Z
author:
authorLink:
description:
tags:
- White list Ip
- GCP
categories:
- Tutorial
draft: false
hiddenFromHomePage: true
---

## Step 1: Access the GCP Console

Open the Google Cloud Platform (GCP) console in your web browser.


***

## Step 2: Navigate to Compute Engine

In the GCP console, navigate to the "Compute Engine" section.

***
## Step 3: Access VM Instances

Select "VM Instances" from the Compute Engine menu.

***

## Step 4: Select Your Target Instance

Choose the VM instance for which you want to configure firewall rules.
Open the instance by clicking on it.

***

## Step 5: Configure Network Interface

Inside the VM instance details, find and select "Network interface."

{{< image src="/img/ConfiguringFirewall/network.png" caption=" Network ">}}

***

## Step 6: Choose a Network

Click on "Network" to select the desired Virtual Private Cloud (VPC) network associated with the instance.

***

## Step 7: Access Firewall Rules

Within the VPC network settings, locate and select "Firewall."

{{< image src="/img/ConfiguringFirewall/firewallrule.png" caption=" firewall rule ">}}

***

## Step 8: Create a Firewall Rule

At the top of the Firewall page, click on "Create Firewall Rule."

{{< image src="/img/ConfiguringFirewall/createfirewall-rule.png" caption=" firewall rule ">}}

***

## Step 9: Configure Firewall Rule Details

Fill in all the required information for your firewall rule.
Pay special attention to the "Priority" field; ensure you set it appropriately based on your requirements.
Save the firewall rule.
By following these steps, you can create and configure firewall rules for your Google Cloud VM instance, enhancing network security and access control.

***




