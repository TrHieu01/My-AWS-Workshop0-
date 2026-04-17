---
title : "WAF Frontend"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 4.6.4 </b> "
---

#### Objectives

Protect the frontend layer (CloudFront) using WAF.

#### Manage Amplify-Created WAF

When deploying an application using AWS Amplify, a web ACL (WAF) is usually automatically created and attached to your frontend's CloudFront Distribution. You do not need to create it manually from scratch.

![WAF](/images/5-Workshop/4.6-frontend-deployment-security/4.7.4-waf-frontend/waf.png)



*Check WAF*

#### Note

1. Always prioritize enabling monitor mode (Count) first, combine it with reviewing CloudWatch logs, before switching to full blocking mode (Block) if necessary to avoid disrupting valid users.
