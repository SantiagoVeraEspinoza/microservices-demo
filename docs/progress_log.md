# Progress Log

## Day 1
- Forked repository
- Deployed the project manually to GCP

Challenges:
- Understanding the base software
- Some services occupy too many resources, causing GCP free tier to reach it's max quota

Next:
- Run the project with much less resources to meet quota
- Test deploying with terraform to later use this in pipelines

## Day 2
- Reduced resources
- Able to run all services with updated kubernetes manifest
- Attempted to run with terraform

Challenges:
- Adjust resources to free tier account quota
- Terraform apply had many issues with quota limits, fixed it by adjusting deployment to work by zones instead of regions (acceptable for POC)
- Needs vertical scaling for all the 11 microservices

Next:
- Increase resources for terraform allocation and couple with kubernetes cluster

## Day 3
- Polished terraform deploy
- Implemented GitHub actions pipeline to create and destroy deployments
- Created bucket for terraform state

Challenges:
- Pending

Next:
- Pending