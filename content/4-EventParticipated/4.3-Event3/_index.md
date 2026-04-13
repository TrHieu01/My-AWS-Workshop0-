---
title: "Event 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Reflection Report: "Cloud Mastery Series #3: AWS Networking, IAM & Security"

### Event Information

- **Event Name:** Cloud Mastery Series #3: AWS Networking, IAM & Security
- **Date & Time:** April 11, 2026
- **Location:** FPTU - Hall Academic A 
- **Role:** Attendee / Learner

<div style="text-align: center;">
  <img src="/images/4-EventParticipated/event3.jpg" alt="Event 3 photo" style="max-width: 920px; width: 100%; height: auto;" />
</div>

### Event Objectives

- Understand AWS networking fundamentals: VPC, subnets, routing, NAT, and blast-radius design.
- Learn how to protect workloads at the network layer with Security Groups and Network ACLs.
- Build a strong IAM foundation: least privilege, SSO, and multi-account guardrails (SCPs / permission boundaries).
- Explore AWS managed services for network and application protection (WAF, Shield, Network Firewall, Firewall Manager).

### Speakers

- Lam An Thinh — Networking on AWS
- Nguyen Phan Quoc Viet — Networking on AWS
- Huynh Hoang Long — Identity & Access Management
- Dang Thi Minh Thu — Identity & Access Management
- Lam Tuan Kiet — AWS Network & Application Protection

### Key Highlights

#### AWS Networking Foundations

- Designing for smaller blast radius by splitting resources across Availability Zones and subnets.
- Internet egress patterns:
  - **Internet Gateway (IGW)** for public subnets.
  - **NAT Gateway** for private subnet outbound access (SNAT, outbound-only behavior via state tracking).
- NAT Gateway operational notes:
  - **Zonal vs. Regional mode** tradeoffs.
  - Performance scaling (from 5 Gbps up to 100 Gbps) and the **port exhaustion** risk (~55,000 concurrent connections per IP to a single destination).
  - Monitoring via CloudWatch metrics.
#### Security Group (SG) vs. Network ACL (NACL)

- **Security Group**
  - Resource-level protection at the **ENI** level.
  - **Stateful**: return traffic is automatically allowed once the connection is established.
  - **Allow-only** model with implicit deny; aligns with a "Zero Trust" mindset.
- **Network ACL**
  - Subnet boundary firewall (applies to all traffic in/out of a subnet).
  - **Stateless**: inbound and outbound must be allowed explicitly (including ephemeral ports for response traffic).
  - Supports **explicit deny** rules; evaluated in **rule number order**, with a default "deny all" at the end.

#### IAM, SSO, and Guardrails

- IAM core concept: manage **users, groups, roles, and permissions** to enforce authentication and authorization.
- Best practices:
  - Apply **least privilege**.
  - **Delete root access keys** after setup; avoid using root for daily operations.
  - Avoid `"*"` in actions/resources when writing policies.
  - Enable **MFA** and rotate passwords/credentials regularly.
- **SSO (Single Sign-On)** for centralized access across multiple AWS accounts (often tied to AWS Organizations).
- Governance controls:
  - **SCPs** set the **maximum available permissions** across accounts in an organization (they never grant permissions; they only filter).
  - **Permission boundaries** set the maximum permissions for a specific IAM user/role within an account.
- Credential strategy:
  - Prefer **short-term credentials** via **STS** (15 minutes to 36 hours) over long-term IAM user access keys.
  - Use AWS IAM Identity Center for login to rely on short-term credentials behind the scenes.
- **IAM Access Analyzer** helps flag risky policies (e.g., `Principal: *`) even when conditions exist.

#### Network & Application Protection on AWS

- **AWS WAF**: filters/monitors HTTP(S) requests and mitigates common web attacks (SQLi, XSS); integrates with CloudFront, ALB, API Gateway.
- **AWS Shield**: managed DDoS protection (Standard is automatic/free; Advanced adds enhanced and cost protection).
- **AWS Network Firewall**: VPC-level security boundaries with stateful/stateless filtering and intrusion prevention.
- **AWS Firewall Manager**: centralized policy deployment for WAF/Shield/Network Firewall across multi-account environments.

### Key Takeaways

- Security is layered: start with identity, then network segmentation, then application protections.
- Treat IAM as the primary control plane: enforce least privilege, MFA, and short-lived credentials.
- Know the difference between stateful SG controls and stateless NACL controls to avoid "it works sometimes" networking issues.
- Managed protection services (WAF/Shield/Firewall Manager) reduce operational overhead while improving coverage.

### How I Apply This to My Work

- Design AWS environments with clear public/private subnet boundaries and predictable routing.
- Restrict administrative access (avoid opening SSH to `0.0.0.0/0`) and use SGs as the default per-resource guardrail.
- Adopt IAM Identity Center (SSO) for access, enforce MFA, and limit long-term access keys.
- Add WAF in front of public endpoints and evaluate Shield/Network Firewall as the system scales.

### Event Experience

The materials provided a practical, defense-in-depth view of AWS: from routing and NAT considerations, to identity governance, to managed security services that protect both the network and the application layer.
