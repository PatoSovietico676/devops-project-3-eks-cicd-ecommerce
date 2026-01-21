# DEVOPS PROJECT 3 — 3-Tier E-Commerce CI/CD on AWS EKS

**Jenkins + SonarQube + Nexus + Docker Hub + Kubernetes (EKS) + AWS RDS MySQL**

## Overview

This project demonstrates an industry-style CI/CD workflow for a 3-tier e-commerce application deployed on AWS EKS:

- **Frontend:** Angular served by **Nginx**
- **Backend:** Java Spring Boot REST API
- **Database:** AWS RDS MySQL
- **Runtime:** AWS EKS (Kubernetes)
- **CI/CD:** Jenkins (Master–Slave) + SonarQube + Nexus + Docker Hub

## Key Outcome (Design Highlight)

✅ **Single public endpoint** (Frontend LoadBalancer)  
✅ Backend is **internal-only** (ClusterIP)  
✅ `/api/*` calls are routed internally via Nginx → backend service (`productssvc`)  
✅ **CORS-free** from browser perspective (same origin)

---

## Repositories Used (App Code)

> Keep app source code in separate repos; this repo is the **portfolio hub** + infra + pipeline references.

- Backend Repo: `01_products_api_project3`
- Frontend Repo: `vinodses_ecomm_store_project3`
- Infra Repo (optional): `project3-infra` (or use `/infra` in this repo)

---

## Architecture (High Level)

### CI/CD Flow

GitHub → Jenkins Master → Jenkins Slave (build/push/deploy) → Docker Hub → EKS → RDS

### Runtime Flow

User → Frontend ELB → Frontend Pod (Nginx)

- Serves Angular UI
- Proxies `/api/*` → `productssvc` (ClusterIP) → Backend Pod → RDS

See: `docs/01-architecture.md`

---

## Proofs / Screenshots (Add yours)

Place your screenshots in `screenshots/`:

- AWS EC2 Instances page
- Jenkins Nodes (Master/Slave)
- Backend pipeline success
- Frontend pipeline success
- `kubectl get svc` showing LB vs ClusterIP
- Working application in browser

---

## Kubernetes Quick Commands

```bash
kubectl get pods
kubectl get svc
kubectl rollout status deployment/productsapideployment
kubectl rollout status deployment/ecommstoreappdeployment
```
