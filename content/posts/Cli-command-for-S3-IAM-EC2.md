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
***

{{< admonition type=tip title="(command for create bucket on s3)" open=true >}}

`aws s3 mb s3://Testbucket/`

{{< /admonition >}}

                


***
{{< admonition type=tip title="(command for copy file from source to S3)" open=true >}}

`aws s3 cp jpg.jpg s3://Testbucket/ `

{{< /admonition >}}
    


***
{{< admonition type=tip title="(command to delete the object from bucket )" open=true >}}

`aws s3 rm s3://Testbucket/115493.jpg `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to dowload file from s3 )" open=true >}}

`aws s3 cp s3://skpnew-27-03/website.jpg /home `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to show regions in aws in text form )" open=true >}}

`aws ec2 describe-regions --output text `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to show regions in aws in table form )" open=true >}}

`aws ec2 describe-regions --output table `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to create group  )" open=true >}}

`aws iam create-group --group-name mygroup  `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to create user )" open=true >}}

`aws iam create-user --user-name myuser `

{{< /admonition >}}


***
{{< admonition type=tip title="(command to delete user)" open=true >}}

`aws iam delete-user --user-name newuser2 `

{{< /admonition >}}


***
{{< admonition type=tip title="(command to show all policies in iam )" open=true >}}

`aws iam list-policies --output table `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to attach policy on group )" open=true >}}

`aws iam attach-group-policy --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess --group-name newgroup `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to attach user with group)" open=true >}}

`aws iam add-user-to-group --user-name myuser --group-name mygroup `

{{< /admonition >}}



***
{{< admonition type=tip title="(to create access key for user)" open=true >}}

`aws iam create-login-profile --user-name myuser --password abcd1234 `

{{< /admonition >}}


***
{{< admonition type=tip title="(to show access key and secret access key)" open=true >}}

`aws iam create-access-key --user-name myuser `

{{< /admonition >}}



***
{{< admonition type=tip title="(to create a key pair for ec2 instance )" open=true >}}

`aws ec2 create-key-pair --key-name mynewkey --query 'keyMaterial' --output text > mynewkey.pem `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to create a security group)" open=true >}}

`aws ec2 create-security-group --group-name mygroup --description "security group for my instance" `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to create network acl)" open=true >}}

`aws ec2 create-network-acl  --vpc-id vpc-abcdefghijklmn `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to setting the security group)" open=true >}}

`aws ec2 authorize-security-group-ingress --group-name mygroup --protocol tcp --port 3389 --cidr 103.255.5.65/32 `

{{< /admonition >}}



***
{{< admonition type=tip title="(to create a new instance command)" open=true >}}

`aws ec2 run-instances --image-id ami-07ebfd5b3428b6f4d --count 1 --instance-type t2.micro --key-name mynewkey --security-groups mygroup `

{{< /admonition >}}



***
{{< admonition type=tip title="(command will show you detail of instances which are on aws region)" open=true >}}

``aws ec2 describe-instances --query 'Reservations[*].Instances[*].[InstanceId,State,Name,LaunchTime,PublicIpAddress]' `

{{< /admonition >}}


 
***
{{< admonition type=tip title="(describe region with helpful patren to show)" open=true >}}

`aws ec2 describe-regions --output text | cut -f 3 `

{{< /admonition >}}


***
{{< admonition type=tip title="(to show instances id running )" open=true >}}

`aws ec2 describe-instances --output text | grep INSTANCES | cut -f 8 `

{{< /admonition >}}



***
{{< admonition type=tip title="(to show instances id )" open=true >}}

``aws ec2 describe-instances --output text --query 'Reservations[*].Instances[*].[InstanceId,PublicDnsName,State.Name]' `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to stop the instance)" open=true >}}

` aws ec2 stop-instances --instance-ids i-05a234103ce5f4243 `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to start the instance)" open=true >}}

` aws ec2 start-instances --instance-ids i-05a234103ce5f4243 `

{{< /admonition >}}



***
{{< admonition type=tip title="(command to terminate the instance)" open=true >}}

` aws ec2 terminate-instances --instance-ids i-05a234103ce5f4243 `

{{< /admonition >}}


 
***
{{< admonition type=tip title="(command to create a vpc)" open=true >}}

` (aws ec2 create-vpc --cidr-block 10.0.0.0/16  --query Vpc.VpcId --output text) `

{{< /admonition >}}



***
{{< admonition type=tip title="(show vpc id)" open=true >}}

` echo $vpc_id `

{{< /admonition >}}


 
***
{{< admonition type=tip title="(command to create the subnet)" open=true >}}

` subnet_id=$(aws ec2 create-subnet --cidr-block 10.0.0.0/24 --vpc-id $vpc_id --query Subnet.SubnetId --output text) `

{{< /admonition >}}

***
[Let me know.](mailto:yahya.gulshan@gmail.com)
