# Kubernetes Deployment (EKS)

## Backend

- Deployment: `productsapideployment`
- Service: `productssvc` (ClusterIP only)
- Reads DB config from Secret: `products-db`

## Frontend

- Deployment: `ecommstoreappdeployment`
- Service: `ecommstoresvc` (LoadBalancer)
- Nginx proxies `/api/*` to `productssvc`

## Verification

```bash
kubectl get pods
kubectl get svc
kubectl logs deploy/productsapideployment --tail=50
kubectl rollout status deploy/productsapideployment
kubectl rollout status deploy/ecommstoreappdeployment
```
