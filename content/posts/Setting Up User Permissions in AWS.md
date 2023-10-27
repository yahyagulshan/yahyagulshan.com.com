---
title: "Setting Up User Permissions in AWS"
date: 2022-11-05T04:06:22Z
author:
authorLink:
description:
tags:
- AWS
- PERMISSION
- READONLY
categories:
- Best Practices
draft: false
---

***

## 1. **Create a User and Assign to a Group**

Start by creating a user and attaching them to a specific group.



## 2. **Assign ReadOnly Permissions**

Next, provide the group with permissions for read-only access.

## 3. **Utilize AWS-Managed Policy**

AWS offers a range of AWS-managed policies, which are pre-configured for common use cases. In this scenario, we recommend using the "[ReadonlyAccess.](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1#/policies/arn:aws:iam::aws:policy/ReadOnlyAccess$jsonEditor/)" policy. It already contains the necessary permissions that match your requirements.



By following these steps, you can efficiently set up user permissions and ensure the right level of access with AWS-managed policies.