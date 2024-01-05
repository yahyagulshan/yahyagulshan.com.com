---
title: "Setting Up AWS S3, GitHub, ACM, and CloudFront for Static Website Hosting"
date: 2024-01-02T04:06:22Z
author:
authorLink:
description:
tags:
- Setting static website
- Cloudfront
- Automation
categories:
- Tutorial
draft: false
hiddenFromHomePage: true
---

[Access the GitHub repo here](https://github.com/yahyagulshan/yahyagulshan.com)
## 1. Create S3 Bucket for Static Website Hosting


Create an S3 bucket named "abc.com"
Set the bucket as a static website page:
Open the S3 bucket and go to "Properties."
In the last option, enable static website hosting.

<!-- {{< image src="/img/setting-up-aws-s3-github/S3-bucket.png" caption=" Open URL ">}} -->

## 2. Configure Bucket Policy for Public Access
* In the S3 bucket, navigate to "Permissions."

* Edit the bucket policy and add the following policy, replacing the S3 bucket ARN:

`Bucket policy`
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::abc.com/*"
        }
    ]
}

<!-- {{< image src="/img/setting-up-aws-s3-github/policy.png" caption=" Open URL ">}} -->

## 3. Configure GitHub Repository

Open link https://github.com/yahyagulshan/yahyagulshan.com
Change the "config.toml" file:

* Update the S3 URL and static website URL at line #8 and line #23.

<!-- {{< image src="/img/setting-up-aws-s3-github/config-toml.png" caption=" Open URL ">}} -->

## 4. Add Secrets to GitHub Repository

* In GitHub repository settings, go to "Secrets and variables" > "Actions."
* Add the following security secrets:
* AWS access key
* Secret access key


<!-- {{< image src="/img/setting-up-aws-s3-github/secret.png" caption=" Open URL ">}} -->

## 5. Run the GitHub Actions Pipeline

* Trigger the GitHub Actions pipeline to send necessary materials to AWS S3.

## 6. Create AWS ACM SSL Certificate

* Open AWS ACM page and click on "Request a Public Certificate."
* Provide the domain name (e.g., "abc.com") and select DNS validation.

## 7. Add values in Cloudflare 

* Add the "CNAME name" and "CNAME value" to your domain registrar (e.g., Cloudflare) for DNS validation.

## 8. Create CloudFront Distribution

* Go to CloudFront and click on "Create Distribution."
* Choose the S3 bucket as the origin domain.
* Click on "Create Distribution" and wait for verification.


<!-- {{< image src="/img/setting-up-aws-s3-github/create-distribution.png" caption=" Open URL ">}}

{{< image src="/img/setting-up-aws-s3-github/default-cache.png" caption=" Open URL ">}}

{{< image src="/img/setting-up-aws-s3-github/default-cache-2.png" caption=" Open URL ">}}


{{< image src="/img/setting-up-aws-s3-github/web-application-firewall.png" caption=" Open URL ">}}


{{< image src="/img/setting-up-aws-s3-github/fire-wall-2.png" caption=" Open URL ">}} -->


## 9. Configure CloudFront Origin Domain

* Go to CloudFront > Origins > Edit.
* Change the origin domain value by copying the S3 static website hosting URL (without http/).
* Save the changes.


<!-- {{< image src="/img/setting-up-aws-s3-github/edit-origin.png" caption=" Open URL ">}}


{{< image src="/img/setting-up-aws-s3-github/static-website.png" caption=" Open URL ">}} -->



## 10. Redirect Domain to CloudFront

* Copy the URL of the CloudFront distribution.
* Create a CNAME record on Cloudflare or your domain registrar with the CloudFront URL as the value.
* After populating the value, your website will display the CloudFront content.

* Now, your static website is hosted on AWS S3, served through CloudFront, and secured with an ACM SSL certificate. The entire deployment process is      automated through GitHub Actions.

