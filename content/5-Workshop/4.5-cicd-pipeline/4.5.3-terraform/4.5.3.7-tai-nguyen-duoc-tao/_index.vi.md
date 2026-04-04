---
title : "Các tài nguyên được tạo sau khi chạy Terraform"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b> 4.5.3.7 </b> "
---

#### Tổng quan

Phần này tổng hợp các tài nguyên AWS được tạo hoặc cập nhật sau khi chạy `terraform apply`. Đưa hình chụp màn hình hoặc output kiểm tra tại đây (AWS Console, CLI, hoặc dashboard) để chứng minh hạ tầng đã được provision đúng.

#### Network & VPC

**VPC**

![VPC](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/vpc.png)

**Subnets**

![Subnets](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/subnets.png)

**Route Tables**

![Route Tables](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/route-tables.png)

**NAT Gateway**

![NAT Gateway](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/nat-gateway.png)

**Elastic IP**

![Elastic IP](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/elastic-ip.png)

**VPC Endpoints**

![VPC Endpoints](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/vpc-endpoints.png)

**Security Groups**

![Security Groups](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/security-groups.png)

#### Load Balancer & Routing

**Application Load Balancer (ALB)**

![ALB](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/alb.png)

**Target Group (Summary)**

![Target Group Summary](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/target-group-summary.png)

**Target Group (Targets)**

![Target Group Targets](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/target-group-targets.png)

#### Compute

**Launch Template**

![Launch Template](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/launch-template.png)

**Auto Scaling Group**

![Auto Scaling Group](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/asg.png)

#### Storage

**S3 Buckets**

![S3 Buckets](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/s3-buckets.png)

#### IAM & Security

**Backend IAM Role & Instance Profile**

![Backend IAM Role](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/iam-backend-role.png)

**EC2 Instances (Instance Profile)**

![EC2 Instances - Instance Profile](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/instance-profile.png)

**VPC Flow Log IAM Role**

![VPC Flow Log IAM Role](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/iam-vpc-flow-log-role.png)

**KMS Key**

![KMS Key](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/kms-key.png)

**SSM Parameter**

![SSM Parameter](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/ssm-parameter.png)

#### Identity (Cognito)

**User Pool**

![Cognito User Pool](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/cognito-user-pool.png)

**App Client**

![Cognito App Client](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/cognito-app-client.png)

**Users**

![Cognito Users](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/cognito-users.png)

**Groups**

![Cognito Groups](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/cognito-groups.png)

#### Observability

**CloudWatch Log Groups**

![CloudWatch Log Groups](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/cloudwatch-log-groups.png)

**CloudWatch Alarms**

![CloudWatch Alarms](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/cloudwatch-alarms.png)

**SNS Topic**

![SNS Topic](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/sns-topic.png)

#### Container Registry

**ECR Repository**

![ECR Repository](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/ecr-repo.png)

**ECR Images**

![ECR Images](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/ecr-images.png)

#### WAF

**Web Application Firewall**

![WAF](/images/5-Workshop/4.5-cicd-pipeline/4.5.3-terraform/4.5.3.7-tai-nguyen-duoc-tao/waf.png)
