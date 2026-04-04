---
title : "Tá»•ng quan kiáº¿n trÃºc"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 4.1. </b> "
---

#### Giá»›i thiá»‡u

EduTrust lÃ  há»‡ thá»‘ng há»— trá»£ há»c táº­p vÃ  giÃ¡m sÃ¡t thi báº±ng AI Camera, Ä‘Æ°á»£c triá»ƒn khai trÃªn AWS Ä‘á»ƒ Ä‘áº£m báº£o má»Ÿ rá»™ng, báº£o máº­t vÃ  váº­n hÃ nh á»•n Ä‘á»‹nh. Workshop nÃ y táº­p trung vÃ o setup kiáº¿n trÃºc vÃ  luá»“ng triá»ƒn khai chuáº©n cho nhÃ³m.

#### Kiáº¿n trÃºc AWS tá»•ng quan

Internet â†’ Amplify â†’ Application Load Balancer â†’ EC2 Auto Scaling â†’ Backend services

![Kiáº¿n trÃºc EduTrust](/images/2-Proposal/edutrust-architect.png)

#### ThÃ nh pháº§n chÃ­nh (theo layer)

**Client/Presentation Layer**

+ **Amplify**: host frontend vÃ  káº¿t ná»‘i custom domain.

**Traffic/Delivery Layer**

+ **Application Load Balancer**: phÃ¢n phá»‘i request vÃ o backend.

**Compute/Service Layer**

+ **EC2 Auto Scaling**: cháº¡y cÃ¡c backend services theo táº£i.
+ **Backend services**: API, xá»­ lÃ½ AI, camera events, auth.

**Data Layer**

+ **Data**: lÆ°u trá»¯ log, video, vÃ  káº¿t quáº£ bÃ i thi (S3/DB).

#### Danh sÃ¡ch dá»‹ch vá»¥ sá»­ dá»¥ng

**Lá»›p giao diá»‡n & biÃªn (Frontend & Edge)**

+ AWS Amplify
+ AWS WAF
+ AWS Route 53
+ AWS ACM

**Lá»›p Ä‘á»‹nh danh (Identity)**

+ Amazon Cognito

**Lá»›p máº¡ng (Networking)**

+ Amazon VPC (public/private subnets)
+ Internet Gateway
+ NAT Gateway
+ Application Load Balancer

**Lá»›p tÃ­nh toÃ¡n & container (Compute & Container)**

+ Amazon EC2
+ EC2 Auto Scaling
+ Amazon ECR

**Lá»›p dá»¯ liá»‡u & lÆ°u trá»¯ (Data & Storage)**

+ Amazon S3 (frontend assets, logs, Terraform state)
+ Amazon RDS
+ Amazon ElastiCache for Redis

**Lá»›p quan sÃ¡t & giÃ¡m sÃ¡t (Observability)**

+ Amazon CloudWatch
+ VPC Flow Logs
+ Amazon SNS

**Lá»›p báº£o máº­t & cáº¥u hÃ¬nh (Security & Configuration)**

+ AWS KMS
+ AWS Systems Manager Parameter Store
+ AWS PrivateLink

**Lá»›p tá»± Ä‘á»™ng hoÃ¡ triá»ƒn khai & IaC (CI/CD & IaC)**

+ GitHub Actions
+ Packer
+ Terraform

#### TÃ­nh sáºµn sÃ ng cao (HA) vÃ  Multi-AZ

+ EC2 Auto Scaling cháº¡y trÃªn nhiá»u AZ Ä‘á»ƒ Ä‘áº£m báº£o HA.
+ Application Load Balancer tá»± Ä‘á»™ng phÃ¢n phá»‘i lÆ°u lÆ°á»£ng giá»¯a cÃ¡c AZ.
+ Dá»¯ liá»‡u quan trá»ng lÆ°u trÃªn dá»‹ch vá»¥ managed (RDS/S3) Ä‘á»ƒ tÄƒng Ä‘á»™ bá»n.

#### Tá»•ng quan kiáº¿n trÃºc vÃ  nhiá»‡m vá»¥

+ **Amplify**: phá»¥c vá»¥ giao diá»‡n ngÆ°á»i dÃ¹ng, káº¿t ná»‘i domain vÃ  HTTPS.
+ **Application Load Balancer**: lÃ m lá»›p Ä‘iá»u phá»‘i, Ä‘á»‹nh tuyáº¿n request tá»›i backend.
+ **EC2 Auto Scaling**: Ä‘áº£m báº£o backend tá»± má»Ÿ rá»™ng khi táº£i tÄƒng.
+ **Backend services**: xá»­ lÃ½ nghiá»‡p vá»¥, AI, camera, auth.
+ **Data layer**: lÆ°u trá»¯ dá»¯ liá»‡u thi, log, video vÃ  káº¿t quáº£.

#### Luá»“ng chÃ­nh trong workshop

1. NgÆ°á»i dÃ¹ng truy cáº­p frontend qua Amplify.
2. Frontend gá»i API qua Application Load Balancer.
3. Backend xá»­ lÃ½ logic, gá»i AI vÃ  nháº­n sá»± kiá»‡n tá»« camera.
4. Dá»¯ liá»‡u Ä‘Æ°á»£c lÆ°u trá»¯ vÃ  hiá»ƒn thá»‹ láº¡i cho ngÆ°á»i dÃ¹ng.
