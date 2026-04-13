---
title: "Event 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Bài thu hoạch "Cloud Mastery Series #3: AWS Networking, IAM & Security"

### Thông tin sự kiện

- **Tên sự kiện:** Cloud Mastery Series #3: AWS Networking, IAM & Security
- **Thời gian:** Ngày 11 tháng 04 năm 2026 (slide không ghi rõ khung giờ)
- **Địa điểm:** FPTU - Hall Academic A 
- **Vai trò:** Người tham dự 

<div style="text-align: center;">
  <img src="/images/4-EventParticipated/event3.jpg" alt="Hình ảnh Event 3" style="max-width: 920px; width: 100%; height: auto;" />
</div>

### Mục tiêu sự kiện

- Nắm nền tảng networking trên AWS: VPC, subnet, routing, NAT và tư duy thiết kế giảm blast radius.
- Hiểu cách bảo vệ workload ở tầng mạng bằng Security Group và Network ACL.
- Củng cố IAM: nguyên tắc least privilege, SSO và guardrails trong môi trường multi-account (SCPs / permission boundaries).
- Tìm hiểu các dịch vụ AWS hỗ trợ bảo vệ network & ứng dụng (WAF, Shield, Network Firewall, Firewall Manager).

### Diễn giả

- Lam An Thinh — Networking on AWS
- Nguyen Phan Quoc Viet — Networking on AWS
- Huynh Hoang Long — Identity & Access Management
- Dang Thi Minh Thu — Identity & Access Management
- Lam Tuan Kiet — AWS Network & Application Protection

### Điểm nổi bật

#### Nền tảng AWS Networking

- Thiết kế để giảm blast radius bằng cách phân tách tài nguyên theo Availability Zone và subnet.
- Các mô hình Internet egress:
  - **Internet Gateway (IGW)** cho public subnet.
  - **NAT Gateway** cho private subnet đi ra ngoài Internet (SNAT, chỉ cho phép traffic phản hồi dựa trên state).
- Lưu ý vận hành NAT Gateway:
  - So sánh **Zonal** và **Regional**.
  - Khả năng mở rộng hiệu năng (từ 5 Gbps đến 100 Gbps) và rủi ro **port exhaustion** (~55.000 kết nối đồng thời / 1 IP tới cùng 1 đích).
  - Theo dõi bằng CloudWatch.

#### Security Group (SG) và Network ACL (NACL)

- **Security Group**
  - Bảo vệ theo tài nguyên ở mức **ENI**.
  - **Stateful**: cho phép traffic phản hồi tự động khi kết nối đã được cho phép.
  - Chỉ có **Allow**, mặc định deny; phù hợp tư duy "Zero Trust".
- **Network ACL**
  - Firewall ở biên subnet (áp dụng cho toàn bộ traffic vào/ra subnet).
  - **Stateless**: phải cấu hình rõ inbound/outbound (bao gồm ephemeral ports để nhận phản hồi).
  - Có **Deny**; rule chạy theo **thứ tự số** và có rule "deny all" mặc định ở cuối.

#### IAM, SSO và Guardrails

- IAM là dịch vụ quản lý **users, groups, roles, permissions** để đảm bảo xác thực và phân quyền.
- Best practices:
  - Áp dụng **least privilege**.
  - **Xóa root access keys** sau khi thiết lập; hạn chế dùng root cho công việc hằng ngày.
  - Tránh dùng `"*"` trong actions/resources khi viết policy.
  - Bật **MFA** và xoay vòng mật khẩu/credentials định kỳ.
- **SSO (Single Sign-On)** giúp đăng nhập tập trung cho nhiều tài khoản AWS (thường đi kèm AWS Organizations).
- Cơ chế kiểm soát quyền:
  - **SCPs** đặt **ngưỡng quyền tối đa** cho các account trong tổ chức (SCP không cấp quyền, chỉ lọc).
  - **Permission boundaries** đặt quyền tối đa cho từng IAM user/role trong một account.
- Chiến lược credentials:
  - Ưu tiên **short-term credentials** qua **STS** (15 phút đến 36 giờ) thay vì access keys dài hạn.
  - Dùng AWS IAM Identity Center để đăng nhập và tự động dùng short-term credentials.
- **IAM Access Analyzer** hỗ trợ phát hiện policy rủi ro (ví dụ `Principal: *`) kể cả khi có điều kiện.

#### Bảo vệ Network & Ứng dụng trên AWS

- **AWS WAF**: lọc/giám sát HTTP(S), giảm thiểu tấn công phổ biến (SQLi, XSS); tích hợp CloudFront, ALB, API Gateway.
- **AWS Shield**: chống DDoS (Standard miễn phí/tự động; Advanced tăng cường bảo vệ và hỗ trợ chi phí).
- **AWS Network Firewall**: tạo security boundary trong VPC với lọc stateful/stateless và intrusion prevention.
- **AWS Firewall Manager**: quản trị policy tập trung cho WAF/Shield/Network Firewall trên môi trường multi-account.

### Kết quả rút ra

- Bảo mật cần theo lớp: identity → network segmentation → application protection.
- IAM là "xương sống" của kiểm soát truy cập: least privilege, MFA và short-lived credentials.
- Hiểu rõ SG (stateful) vs NACL (stateless) giúp tránh lỗi mạng kiểu "lúc được lúc không".
- Dịch vụ managed (WAF/Shield/Firewall Manager) giúp giảm overhead vận hành và tăng độ phủ bảo vệ.

### Ứng dụng vào công việc

- Thiết kế môi trường AWS theo ranh giới public/private rõ ràng và routing dễ kiểm soát.
- Hạn chế mở cổng quản trị (tránh mở SSH ra `0.0.0.0/0`), ưu tiên dùng SG để kiểm soát theo tài nguyên.
- Dùng IAM Identity Center (SSO), bật MFA và hạn chế access keys dài hạn.
- Triển khai WAF cho các endpoint public và cân nhắc Shield/Network Firewall khi hệ thống mở rộng.

### Trải nghiệm sự kiện

Tài liệu mang đến góc nhìn thực tế về defense-in-depth trên AWS: từ routing/NAT, đến quản trị danh tính (IAM), và các dịch vụ bảo vệ ở tầng network lẫn application.
