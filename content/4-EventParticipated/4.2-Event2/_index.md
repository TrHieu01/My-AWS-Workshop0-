---
title: "Event 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Reflection Report: “Cloud Mastery Series #2: DevOps Fundamentals & Infrastructure”

### Event Information

- **Event Name:** Cloud Mastery Series #2: DevOps Fundamentals & Infrastructure
- **Date & Time:** 09:00 – 12:00, April 04, 2026
- **Location:** FPTU — Hall Academic A
- **Role:** Attendee

### Event Objectives

- Build a structured understanding of Infrastructure as Code (IaC) and hands-on Terraform on AWS.
- Understand Kubernetes (K8s) architecture and how to manage modern applications in a cloud-native environment.
- Explore Elixir/Erlang as a tool for highly available and fault-tolerant DevOps systems.
- Learn through live demos and practical implementation techniques.

### Speakers

- Thinh Nguyen — FCAJ Cloud Engineer Trainee (IaC & Terraform)
- Bao Huynh — Junior Cloud Native Developer at Endava / Founder of ITea Lab (Kubernetes)
- Nguyen Ta Minh Triet — R&D Member at ITea Lab / SAP Developer Intern at Bosch GSV (Elixir)

### Key Highlights

#### Infrastructure as Code (IaC) with Terraform

- The shift from “ClickOps” to IaC to reduce human error and improve consistency.
- Comparison of AWS CloudFormation, AWS CDK, and Terraform (HCL).
- State management and core commands: `plan`, `apply`, `destroy`.

#### Kubernetes (K8s) Architecture

- Managing at scale with self-healing and auto-scaling.
- Core components: Control Plane, Worker Nodes, Pods, Deployments, and Services.
- Supporting tools: Helm (package management) and K9s (terminal UI for cluster ops).

#### Elixir in the DevOps Pipeline

- BEAM VM strengths: handling massive concurrency at low cost.
- “Let it crash” philosophy using supervision trees for self-recovery without manual intervention.
- Case study: migrating from Serverless (Node.js/Lambda) to Elixir to reduce costs drastically.

### Key Takeaways

- **Automation mindset:** infrastructure becomes versioned, reusable code.
- **Efficient cluster operations:** understanding why managed Kubernetes (e.g., EKS) helps reduce control-plane overhead.
- **Fault tolerance matters:** designing for recovery is more important than trying to write “never failing” code.
- **Cost optimization:** selecting the right tech (e.g., Elixir for concurrent workloads) can yield better ROI than traditional approaches.

### How I Apply This to My Work

- Standardize EduTrust infrastructure with Terraform to replicate environments (Dev/Staging/Prod).
- Consider containerizing EduTrust services with Docker and orchestrating with Kubernetes for higher availability.
- Learn more about event-driven patterns and resilient architectures and apply them to real-time features.

### Event Experience

The workshop delivered a logical learning journey from infrastructure to platform operations:

- Practical, hands-on demos (Terraform and K9s) that made the concepts concrete.
- Exposure to multiple perspectives, combining mainstream tools (AWS, Kubernetes) with high-performance approaches (Elixir).
- Valuable networking and discussions with speakers with real industry experience.

### Lessons Learned

- Modern infrastructure should be paired with IaC to ensure speed and safety.
- Kubernetes is powerful, but tools like Helm and K9s are essential for effective day-to-day operations.
- Be open to new languages/platforms (such as Elixir) when they solve reliability and cost problems better.

### Event Photos

(No photos available yet.)

### Conclusion

Cloud Mastery Series #2 provided a strong foundation in modern DevOps: IaC, Kubernetes operations, and reliability/cost tradeoffs. These lessons are directly applicable to building and operating EduTrust more professionally and at larger scale.
