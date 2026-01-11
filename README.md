# InfraGuard

## What InfraGuard Is
InfraGuard is a production-style AWS infrastructure project focused on secure networking, controlled access, scalability, and cost-aware design.  
The goal is to demonstrate how cloud infrastructure should be **designed before problems occur**, not reacted to after.

---

## Architecture Overview
InfraGuard uses a custom VPC with public and private subnets across multiple availability zones.  
Traffic enters through an Application Load Balancer in public subnets, while compute resources run in private subnets with no direct internet exposure.  
Outbound internet access is controlled via a single NAT Gateway as a deliberate cost optimization.

---

## Security Decisions
- No SSH access to EC2 instances
- Systems Manager Session Manager used for instance access
- EC2 instances run in private subnets only
- Least-privilege IAM roles attached to compute resources
- Security Groups used as primary traffic control mechanism

---

## Cost Decisions
- Single NAT Gateway instead of multi-AZ NAT to reduce baseline costs
- Minimal Auto Scaling capacity (min=1, max=2)
- No managed databases or unnecessary always-on services
- Budget alerts configured to enforce cost visibility

---

## What Is Intentionally NOT Included
- HTTPS / TLS termination
- Databases (RDS, DynamoDB)
- Infrastructure as Code (Terraform / CloudFormation)
- Frontend UI or dashboards
- Multi-region redundancy

These exclusions are intentional to keep the project focused on core infrastructure fundamentals.
