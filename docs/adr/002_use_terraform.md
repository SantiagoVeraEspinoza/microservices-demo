# ADR-002: Use Terraform for Infrastructure Provisioning

Status: Accepted

## Context:
The system requires a reproducible, automated way to provision and manage cloud infrastructure (GKE cluster, networking, and related resources). Manual provisioning would be error-prone, non-repeatable, and slow for iterative development and testing.

We also need a way to safely destroy and recreate environments as part of CI/CD workflows.

## Decision:
Use Terraform as the Infrastructure as Code (IaC) tool to manage all GCP resources, including the GKE cluster and supporting infrastructure.

## Consequences:

### Positive
- Fully reproducible infrastructure across environments.
- Supports automated lifecycle management (apply/destroy) in CI/CD pipelines.
- Strong integration with GCP provider.
- Declarative configuration improves maintainability and reviewability.
- Enables environment resets for testing and debugging.
- Widely adopted tool with strong community support.

### Negative
- State management complexity (remote state required for team setups).
- Terraform-specific learning curve.
- Debugging failures can be non-trivial in large plans.
- Potential drift if manual changes are made outside IaC.