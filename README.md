# InfraGuard

InfraGuard is a production-style AWS infrastructure project focused on secure networking,
high availability, auto-healing, monitoring, and cost governance.

## Architecture Overview
- Custom VPC with public and private subnets across multiple AZs
- Internet-facing Application Load Balancer
- Private EC2 instances behind ALB
- Auto Scaling Group for self-healing
- NAT Gateway for controlled outbound internet access
- CloudWatch alarms for monitoring
- AWS Budget for cost control

## Security Decisions
- EC2 instances run in private subnets (no public IPs)
- ALB is the only internet-facing component
- Security groups enforce ALB → EC2 traffic only
- No SSH access; Systems Manager used instead

## High Availability & Resilience
- Multi-AZ deployment
- Auto Scaling Group replaces unhealthy instances automatically
- ALB health checks ensure traffic only reaches healthy targets

## Monitoring & Cost Control
- CloudWatch alarms configured for infrastructure health
- AWS Budget configured to monitor monthly spend
- Identified NAT Gateway and ALB as major cost drivers

## What This Project Demonstrates
- Real-world AWS networking
- Secure-by-design infrastructure
- Auto-healing systems
- Cost-aware cloud architecture

## Intentionally Not Included
- Application-level logic
- CI/CD pipelines
- Infrastructure as Code (future enhancement)
