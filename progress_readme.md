# DevOps + AI Use Case

## Overview
What was solved.

## Architecture
General diagram.

## Tech Stack
- Terraform
- Kubernetes
- Prometheus
- Grafana
- GitHub Actions

## Deployment Steps
1. Set the Google Cloud project and region and ensure the Google Kubernetes Engine API is enabled.

   ```sh
   export PROJECT_ID=<PROJECT_ID>
   export ZONE=us-central1-a
   gcloud services enable container.googleapis.com \
     --project=${PROJECT_ID}
   ```

2. Apply Terraform
   ```sh
   cd ./terraform
   terraform apply
   ```

3. Get cloud credentials
   ```sh
   gcloud container clusters get-credentials online-boutique --zone $ZONE --project $PROJECT_ID
   ```

4. Deploy Online Boutique to the cluster.

   ```sh
   kubectl apply -f ../release/kubernetes-manifests.yaml
   ```

5. Wait for the pods to be ready.

   ```sh
   kubectl get pods
   ```

   After a few minutes, you should see the Pods in a `Running` state:

   ```
   NAME                                     READY   STATUS    RESTARTS   AGE
   adservice-76bdd69666-ckc5j               1/1     Running   0          2m58s
   cartservice-66d497c6b7-dp5jr             1/1     Running   0          2m59s
   checkoutservice-666c784bd6-4jd22         1/1     Running   0          3m1s
   currencyservice-5d5d496984-4jmd7         1/1     Running   0          2m59s
   emailservice-667457d9d6-75jcq            1/1     Running   0          3m2s
   frontend-6b8d69b9fb-wjqdg                1/1     Running   0          3m1s
   loadgenerator-665b5cd444-gwqdq           1/1     Running   0          3m
   paymentservice-68596d6dd6-bf6bv          1/1     Running   0          3m
   productcatalogservice-557d474574-888kr   1/1     Running   0          3m
   recommendationservice-69c56b74d4-7z8r5   1/1     Running   0          3m1s
   redis-cart-5f59546cdd-5jnqf              1/1     Running   0          2m58s
   shippingservice-6ccc89f8fd-v686r         1/1     Running   0          2m58s
   ```

6. Access the web frontend in a browser using the frontend's external IP.

   ```sh
   kubectl get service frontend-external | awk '{print $4}'
   ```

   Visit `http://EXTERNAL_IP` in a web browser to access your instance of Online Boutique.

7. Once you are done with it, delete the GKE cluster.

   ```sh
   terraform destroy
   ```

Deleting the cluster may take a few minutes.

## Monitoring
Metrics recolected.

## Automation
Pipelines overview.

## AI Agent Design
Link to AI agent SDD.

## Evidence
Screenshots, URLs, logs.
### Screenshots
- First run: ![First run proof](./docs/img/evidence/01_first_run.jfif)
- Got pipelines working: ![Got pipelines working proof](./docs/img/evidence/02_working_pipelines.jpeg)

### Progress Logs
- [Progress log](docs/progress_log.md).

### Architecture Design Records
- [Why GCP?](docs/adr/001_use_gcp.md).

## Tradeoffs
What was simplified and why.