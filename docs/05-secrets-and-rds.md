# Secrets & RDS (No Hardcoding)

## Why Secrets

DB credentials must not be committed to Git.
Spring Boot reads DB config from environment variables injected by Kubernetes Secret.

## Secret Keys Used

- SPRING_DATASOURCE_URL
- SPRING_DATASOURCE_USERNAME
- SPRING_DATASOURCE_PASSWORD

## Create/Update Secret via CLI (No Secret File Committed)

Run this on a machine that has kubectl access to the cluster:

```bash
kubectl create secret generic products-db \
  --from-literal=SPRING_DATASOURCE_URL="jdbc:mysql://REAL-ENDPOINT:3306/DBNAME" \
  --from-literal=SPRING_DATASOURCE_USERNAME="REAL-USER" \
  --from-literal=SPRING_DATASOURCE_PASSWORD="REAL-PASS" \
  --dry-run=client -o yaml | kubectl apply -f -

Verify:

kubectl get secret products-db
kubectl describe secret products-db

Deployment Must Reference the Secret

In backend deployment:

envFrom:
- secretRef:
    name: products-db

RDS Security Group Rule (Critical)

Inbound 3306 should be restricted to:

EKS worker node SG (best)
OR

VPC CIDR (training safe option)

Avoid 0.0.0.0/0.
```
