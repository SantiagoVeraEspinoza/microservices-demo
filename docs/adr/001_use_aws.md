# ADR-001: Use AWS

Status: Pending

## Context:
Need target cloud provider.

## Decision:
Use AWS.

## Consequences:
### Positive
- Mature cloud ecosystem with strong infrastructure primitives.
- Production-grade managed Kubernetes through EKS.
- Strong Terraform integration for infrastructure automation.
- Better visibility into infrastructure components and DevOps practices.
- Flexible monitoring integrations (CloudWatch, Prometheus, Grafana).

### Negative
- Higher operational complexity than more opinionated Kubernetes platforms.
- Increased configuration surface (IAM, networking, node groups).
- Less predictable cost structure.
- Potential vendor lock-in through AWS-native integrations.
- Longer setup and troubleshooting cycles.