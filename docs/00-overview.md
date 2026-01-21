# Project Overview

## Title

3-Tier E-Commerce Application CI/CD on AWS EKS  
(Jenkins + SonarQube + Nexus + Docker Hub + Kubernetes + RDS MySQL)

## Objective

Implement an end-to-end CI/CD workflow to:

- Pull code from Git automatically
- Build backend (Maven)
- Run code quality scan (SonarQube)
- Upload JAR to Nexus
- Build/push Docker images to Docker Hub with version tags
- Deploy to AWS EKS using kubectl
- Connect backend to RDS securely using Kubernetes Secrets
- Expose only frontend via LoadBalancer and route API internally to avoid CORS

## Key Design Decision (CORS-Free)

Browser calls only the frontend domain and uses relative `/api/*`.
Nginx proxies `/api/*` internally to backend ClusterIP service.
Result: CORS is avoided by architecture (same-origin for browser).
