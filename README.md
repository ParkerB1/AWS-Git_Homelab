# AWS S3 Static Website with CloudFront, CI/CD, and Monitoring

This project demonstrates the design, deployment, and automation of a secure, globally distributed static website using AWS cloud services. The solution leverages Amazon S3 for static hosting, CloudFront for content delivery, Route 53 for DNS management, ACM for HTTPS, IAM for secure automation, CloudWatch for monitoring, and GitHub Actions for CI/CD.

The project was built as a hands-on cloud homelab to showcase foundational AWS architecture, automation, monitoring, and troubleshooting skills relevant to entry-level cloud and cloud support roles.

**Live Site:** https://parkerbs3.com

---

## Architecture Overview

**Request Flow:**

User → Squarespace (Domain Registrar) → Route 53 → CloudFront (CDN) → S3 Origin

### Services Used
- **Amazon S3** – Hosts static website content
- **Amazon CloudFront** – Global CDN, HTTPS delivery, and access logging
- **AWS Certificate Manager (ACM)** – SSL/TLS certificate management
- **Amazon Route 53** – DNS hosting using AWS name servers
- **AWS IAM** – Secure permissions for CI/CD automation
- **Amazon CloudWatch** – Metrics, alarms, and monitoring
- **Amazon SNS** – Email notifications for alerts
- **GitHub Actions** – CI/CD pipeline for automated deployments
- **Squarespace** – Third-party domain registrar

---

## Features

- Static website hosting on Amazon S3
- HTTPS enabled using ACM-managed SSL certificates
- Global content delivery via CloudFront
- Automated CI/CD deployments with GitHub Actions
- Secure IAM-based access for automation
- DNS management using Route 53 with external registrar
- Monitoring, alerting, and log-based troubleshooting

---

## Deployment & Configuration

### 1. Domain Registration & DNS
- Purchased custom domain through Squarespace
- Updated domain name servers to AWS Route 53 name servers
- Managed DNS records (A/ALIAS) in Route 53 pointing to CloudFront

### 2. S3 Static Website Hosting
- Created an S3 bucket configured for static website hosting
- Uploaded frontend assets (HTML, CSS, JavaScript)
- Configured bucket policies to allow CloudFront access

### 3. CloudFront Distribution
- Configured CloudFront with the S3 bucket as the origin
- Enabled HTTPS using an ACM-issued certificate
- Optimized caching behavior for static content
- Enabled **CloudFront access logging** for request-level visibility

### 4. IAM & CI/CD Automation
- Created IAM permissions allowing GitHub Actions to securely update the S3 bucket
- Implemented a GitHub Actions workflow (.yml) to deploy site updates
- Deployment options:
  - Automatically on every push to the main branch
  - Manually via GitHub Actions workflow dispatch
- Enforced least-privilege access for deployment automation

### 5. Monitoring, Alerts & Logging
- Enabled CloudWatch metrics for CloudFront
- Monitored:
  - Request count
  - 4xx error rates
  - 5xx error rates
- Configured CloudWatch alarms to publish notifications to an SNS topic
- SNS topic sends email alerts when thresholds are exceeded
- Enabled CloudFront access logs to an S3 bucket to investigate recurring 4xx errors
- Used access logs to analyze request paths, response codes, and client behavior

---

## Skills Demonstrated

- AWS cloud architecture fundamentals
- Third-party domain registrar integration with AWS DNS
- Secure static website hosting and HTTPS configuration
- CDN caching and request flow understanding
- IAM permissions and least-privilege access
- CI/CD automation using GitHub Actions
- Monitoring, alerting, and log-based troubleshooting
- Root-cause analysis using CloudFront access logs

---

## Challenges & Troubleshooting

- Integrated a third-party domain registrar (Squarespace) with Route 53
- Resolved S3 bucket policy and IAM permission issues for CI/CD access
- Investigated recurring CloudFront 4xx alerts using access logs
- Debugged CloudFront caching behavior and origin configuration
- Troubleshot SSL certificate validation and HTTPS issues
- Diagnosed CI/CD deployment failures and permission errors
- Tuned CloudWatch alarm thresholds to reduce alert noise