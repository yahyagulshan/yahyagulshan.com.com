---
title: "CLI Commands For AWS (S3-EC2-IAM)"
date: 2023-02-27T04:06:22Z
author:
authorLink:
description:
tags:
- AWS
- Cli commands
- Automation
categories:
- Work
draft: false
hiddenFromHomePage: true
---

aws s3 mb s3://Testbucket/                (command for create bucket on s3)

aws s3 cp jpg.jpg s3://Testbucket/     (command for copy file from source to S3)

aws s3 rm s3://Testbucket/115493.jpg (command to delete the object from bucket )

aws s3 cp s3://skpnew-27-03/website.jpg /home (command to dowload file from s3 )

aws ec2 describe-regions --output text (command to show regions in aws in text form )

aws ec2 describe-regions --output table (command to show regions in aws in table form )

aws iam create-group --group-name mygroup  (command to create group  )

aws iam create-user --user-name myuser (command to create user  )

aws iam delete-user --user-name newuser2 (command to delete user)

aws iam list-policies --output table (command to show all policies in iam )

aws iam attach-group-policy --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess --group-name newgroup (command to attach policy on group )


aws iam add-user-to-group --user-name myuser --group-name mygroup (command to attach user with group)

aws iam create-login-profile --user-name myuser --password abcd1234 (to create access key for user)

aws iam create-access-key --user-name myuser (to show access key and secret access key)

aws ec2 create-key-pair --key-name mynewkey --query 'keyMaterial' --output text > mynewkey.pem (to create a key pair for ec2 instance )

aws ec2 create-security-group --group-name mygroup --description "security group for my instance" (command to create a security group)

aws ec2 create-network-acl  --vpc-id vpc-abcdefghijklmn (command to create network acl)

aws ec2 authorize-security-group-ingress --group-name mygroup --protocol tcp --port 3389 --cidr 103.255.5.65/32 (command to setting the security group)

aws ec2 run-instances --image-id ami-07ebfd5b3428b6f4d --count 1 --instance-type t2.micro --key-name mynewkey --security-groups mygroup (to create a new instance command)

aws ec2 describe-instances --query 'Reservations[*].Instances[*].[InstanceId,State,Name,LaunchTime,PublicIpAddress]' (command will show you detail of instances which are on aws region)

aws ec2 describe-regions --output text | cut -f 3 (describe region with helpful patren to show)

aws ec2 describe-instances --output text | grep INSTANCES | cut -f 8 (to show instances id running )

aws ec2 describe-instances --output text --query 'Reservations[*].Instances[*].[InstanceId,PublicDnsName,State.Name]' (to show instances id )

aws ec2 describe-instances --output table --query 'Reservations[*].Instances[*].[InstanceId,PublicDnsName,State.Name]' (to show instance id in table formate)

aws ec2 stop-instances --instance-ids i-05a234103ce5f4243 (command to stop the instance)

aws ec2 start-instances --instance-ids i-05a234103ce5f4243 (command to start the instance)


aws ec2 terminate-instances --instance-ids i-05a234103ce5f4243 (command to terminate the instance)

(aws ec2 create-vpc --cidr-block 10.0.0.0/16  --query Vpc.VpcId --output text) (command to create a vpc)

echo $vpc_id (show vpc id)

subnet_id=$(aws ec2 create-subnet --cidr-block 10.0.0.0/24 --vpc-id $vpc_id --query Subnet.SubnetId --output text) (command to create the subnet)

