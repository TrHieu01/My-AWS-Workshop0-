---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

In this section, you need to summarize the contents of the workshop that you **plan** to conduct. -->

# EduTrust — AI-Powered Online Exam Proctoring Platform
## Fullstack solution with AWS for exam proctoring and smart learning support

### 1. Executive Summary
EduTrust is an online exam management platform designed for educational environments (schools and training centers) to digitize the exam workflow, provide AI-based proctoring, and support learning via an intelligent chatbot. The system serves 3 main user groups: **Admin** (school), **Teacher** (create exams, monitor), and **Student** (take exams, view results). The backend uses Python FastAPI with MongoDB, Redis, Amazon S3, and a YOLO model to detect cheating via webcam. The frontend is built with Next.js and Tailwind CSS and deployed on AWS Amplify.

### 2. Problem Statement
### Current Problems
Online exams face multiple challenges: manual proctoring is labora intensive, cheating is difficult to detect (phones, multiple faces in frame, leaving the camera), there is no centralized system to manage classes  exams results, and students lack intelligent learning support tools.

### The Solution
EduTrust provides a comprehensive platform including:
- **Class & Exam Management**: Admin creates classes, assigns homeroom/subject teachers; teachers create multiple choice exams with secret keys and start/end times.
- **AI Proctoring**: Integrates YOLOv26n to detect violations in real time (MULTIPLE_FACES, FACE_DISAPPEARED, FORBIDDEN_OBJECT). Evidence images are stored in Amazon S3 and logged in MongoDB.
- **AI Learning Assistant**: Multi agent system (Pydantic AI) helps students search knowledge, ask questions, and find learning materials.
- **Authentication & Security**: JWT (via Cognito) with role based access control (RBAC).

### Benefits and ROI
The solution reduces teachers manual workload, improves transparency and fairness, and automates grading with evidence stored in S3. Operational cost stays low by leveraging MongoDB Atlas (free tier), Redis Cloud, and AWS S3/Amplify. Estimated AWS cost is under 5 USD/month for a midâ€‘size school.

### 3. Solution Architecture
EduTrust applies a **fullstack monorepo** architecture with a Python FastAPI backend and a Next.js frontend, deployed via Docker. Data is stored in MongoDB (users, exams, classes, submissions, violations), session/conversation cache uses Redis, and violation images are stored in Amazon S3. The architecture is shown below:

![EduTrust Solution Architecture](/images/2-Proposal/edutrust-architect.png)

### Services & Technology (Aligned with Architecture)
- **AWS Amplify + CloudFront**: Hosts the Next.js frontend and delivers content via CDN.
- **Amazon Route 53 + AWS ACM**: DNS and TLS/HTTPS certificate management.
- **AWS WAF**: Web application firewall protection.
- **Amazon VPC (public/private subnets)**: Network isolation and segmentation.
- **Application Load Balancer (ALB)**: Distributes traffic to backend services.
- **Amazon EC2 Auto Scaling**: Scales backend compute based on load.
- **Amazon ECR**: Container registry for backend images.
- **Amazon S3**: Stores violation images, ALB logs, and Terraform state.
- **Amazon DynamoDB**: Key-value data store (as shown in the architecture).
- **Amazon ElastiCache for Redis**: Cache/session layer for fast access.
- **Amazon Cognito**: Authentication and user management.
- **Amazon CloudWatch + VPC Flow Logs + SNS**: Monitoring, logs, and alerting.
- **AWS KMS + SSM Parameter Store + PrivateLink**: Secrets and secure internal access.
- **Terraform + GitHub Actions**: Infrastructure as Code and CI/CD automation.

### Application Stack
- **FastAPI**: Async backend API framework with automatic docs.
- **Next.js + Tailwind CSS**: Frontend app with modern UI.
- **YOLOv26n (Ultralytics)**: AI object detection for proctoring.
- **Pydantic AI + LiteLLM**: Multi-agent orchestration for the chatbot.
- **Docker**: Containerization with multi-stage builds.

### Component Design
- **Authentication (Auth)**: JWT access/refresh tokens, session via cookies, RBAC (admin/teacher/student).
- **Class Management**: Assign homeroom/subject teachers, add/remove students, auto update status (active/inactive).
- **Exam Management**: Create MCQ exams, auto generate secret keys, control start/end time, auto grading on submit.
- **Camera Proctoring (Detection)**: CameraService receives frames, YOLO detects violations, ViolationLogger writes MongoDB + S3, ScreenshotUtils captures evidence.
- **AI Agent**: UnifiedAgent orchestrates subâ€‘agents (technical, social, general, web_search) with tool delegation and WebSocket streaming.

### 4. Technical Implementation
**Implementation Phases**
The project is divided into 5 main phases:
1. **Learn core AWS services**: Get familiar with services in the architecture (VPC, EC2/ALB/ASG, S3, ECR, Cognito, CloudWatch, KMS, SSM, WAF) and the CI/CD + IaC workflow.
2. **Research & design**: Study key technologies (FastAPI, Next.js, YOLO, Pydantic AI), design the database schema, API contracts, and overall system architecture.
3. **Build core features**: Implement auth (Cognito JWT), class CRUD, exam management, submissions, and auto grading.
4. **Integrate AI & camera**: Integrate YOLO for violation detection, build the multi-agent chatbot, connect S3 and Redis.
5. **Frontend & testing**: Complete the Next.js dashboards for 3 roles, end-to-end testing, performance optimization, and Dockerization.

**Technical Requirements**
- **Backend**: Python >= 3.11, FastAPI, Motor (async MongoDB driver), Redis >= 5.0, Boto3 (AWS SDK), Ultralytics (YOLO), Pydantic AI + LiteLLM, Kreuzberg (document parsing), SlowAPI (rate limiting).
- **Frontend**: Next.js 16, React 19, Tailwind CSS v4, Lucide React (icons), React Markdown + KaTeX (math rendering), ONNX Runtime Web, next-intl (i18n).
- **Infrastructure**: Docker (multi-stage build), MongoDB Atlas, Redis Cloud, Amazon S3, AWS Amplify, Logfire (observability).

### 5. Timeline & Milestones
- **Week 1–2**: Learn AWS services in the architecture (VPC, EC2/ALB/ASG, S3, ECR, Cognito, CloudWatch, KMS/SSM, WAF) and CI/CD + IaC.
- **Week 3–4**: Research technologies, design architecture and database schema.
- **Week 5–6**: Build core backend (auth, classes, exams, submissions).
- **Week 7–8**: Integrate YOLO detection, AI chatbot (multi-agent), and S3 storage.
- **Week 9**: Build the frontend dashboard (admin/teacher/student views).
- **Week 10**: Integration testing, performance optimization, and Dockerization.

### 6. Budget Estimation
**Assumptions**
- Small environment (small staging/production), low-to-medium traffic.
- Backend runs on EC2 Auto Scaling (t3.small, 2 instances) behind an ALB 24/7.
- Frontend hosted on Amplify + CloudFront with WAF enabled.
- Violation evidence stored in S3 (~10–20 GB/month).

**Estimated monthly infrastructure costs**
- VPC Endpoints (interface endpoints for ECR/SSM/STS/Logs…): ~30–60 USD
- EC2 Auto Scaling (2 × t3.small): ~30–40 USD
- Application Load Balancer: ~16–25 USD
- Amazon S3 (evidence images, ALB logs, Terraform state): ~2–6 USD
- Amazon CloudFront + Amplify: ~1–5 USD
- AWS WAF: ~5–10 USD
- Amazon ElastiCache (Redis — small cache): ~15–25 USD
- Amazon DynamoDB (low traffic): ~1–3 USD
- Amazon ECR (image storage): ~1–3 USD
- Amazon Cognito (<= 50k MAU): ~0–2 USD
- Amazon CloudWatch + VPC Flow Logs + SNS: ~5–10 USD
- AWS KMS + SSM Parameter Store: ~1–3 USD
- Data Transfer: ~2–6 USD

**Total estimate**: ~110–195 USD/month (includes VPC Endpoints; depends on traffic and S3 usage).

**Third-party API costs**
- OpenAI/LiteLLM API: depends on usage.
- External search services (if used): depends on plan.

### 7. Risk Assessment
**Risk matrix**
- Low YOLO accuracy (false positives/negatives): High impact, medium probability.
- Student camera/network disconnects: Medium impact, medium probability.
- API budget overrun (LLM calls): Medium impact, low probability.
- Switching from MongoDB to MySQL increases schema/query complexity: Medium-to-high impact, medium probability.

**Mitigation strategies**
- YOLO: Tune confidence threshold (min 0.5), alert only after multiple consecutive frames, allow teachers to review violations manually.
- Network: Client-side detection with ONNX Runtime Web as fallback, store violations locally and sync when network is available.
- API cost: Rate limiting (SlowAPI), budget alerts, use lighter models for simple tasks.
- Database: Repository layer abstraction, schema normalization, prepare migration scripts if switching to MySQL.

**Contingency plans**
- Fall back to manual proctoring (teachers monitor camera streams) if AI detection fails.
- Use SQLite/local storage fallback if MongoDB Atlas is unavailable.
- Docker images enable fast redeploy on other cloud providers (avoid AWS lock-in).

### 8. Expected Outcomes
**Technical improvements**: Automate online exam proctoring with AI (YOLO) instead of manual monitoring. Automate MCQ grading and store violation evidence images in S3. Provide a multi-agent AI chatbot to support students 24/7.

**Long-term value**: The platform can scale to multiple schools, support multilingual UI (next-intl), integrate additional exam types (e.g., essay with AI-assisted grading), and evolve into a complete education SaaS product. Accumulated violation data can be used to improve detection models over time.
