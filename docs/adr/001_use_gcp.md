# ADR-001: Use GCP

Status: Accepted

## Context:
Need a target cloud provider to deploy the Online Boutique microservices application, collect performance metrics, and automate the infrastructure lifecycle.

The selected provider should reduce setup complexity, support Kubernetes and gRPC workloads natively, integrate well with observability tooling, and allow fast iteration within the challenge time constraints.

## Decision:
Use GCP as the target cloud provider, with GKE as the managed Kubernetes platform.

## Consequences:

### Positive
- Strong native compatibility with the Online Boutique reference implementation.
- Faster Kubernetes provisioning through GKE.
- Lower operational overhead due to managed control plane abstractions.
- Better alignment with Google-originated tooling and documentation.
- Strong Terraform provider support for infrastructure automation.
- Native integration with Cloud Monitoring and Logging.
- Better support for gRPC workloads and HTTP/2 load balancing.

### Negative
- Partial vendor lock-in through GCP-native integrations.
- Less infrastructure-level exposure compared to AWS (more abstraction, less control).
- Potential cost growth if resources are not cleaned up properly.
- Reduced cloud-provider portability if architecture depends heavily on GKE-specific features.
- Requires learning GCP-specific IAM and networking concepts if unfamiliar.