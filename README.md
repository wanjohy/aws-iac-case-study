# AWS Infrastructure as Code with CloudFormation

> **Case study.** The templates were written for commercial environments, so they are private. This repository describes the design and results.

**Role:** Cloud engineer: template design, networking and security, and rollout.

**Stack:** AWS CloudFormation (YAML) · VPC · public and private subnets · EC2 · security groups · IAM

---

## The problem

Setting up AWS environments by hand was slow and error-prone, and dev, staging and production drifted apart.

## What I built

- **Reusable CloudFormation templates** for a full network and compute stack
- **VPC** with public and private subnets across availability zones, route tables and internet/NAT gateways
- **Security groups** with least-privilege rules, and **IAM roles** instead of long-lived keys
- **EC2** and application resources parameterised per environment (dev / staging / production)
- **Outputs and cross-stack references** so application stacks plug into the shared network

## Results

- Environment setup time cut by about **80%**
- Identical, reviewable environments, with changes tracked in version control

## Architecture

```
 CloudFormation
   ├── network stack:  VPC · subnets (public/private, multi-AZ) · route tables · IGW/NAT
   ├── security stack: security groups · IAM roles
   └── app stack:      EC2 / ECS resources (parameters per environment)
```

---

📫 Bernard Wanjohi Gitahi · [Portfolio](https://bernardwanjohi.web.app) · bernardgitahi2018@gmail.com
