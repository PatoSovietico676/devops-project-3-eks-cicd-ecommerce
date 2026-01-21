# CI/CD Pipelines

## Backend Pipeline Summary

- Checkout App + Infra repos
- Maven build (skip tests)
- SonarQube scan
- Upload JAR to Nexus
- Docker build using infra Dockerfile
- Docker push to Docker Hub
- Deploy to EKS (apply + set image + rollout)

## Frontend Pipeline Summary

- Checkout App + Infra repos
- Copy nginx default.conf for build
- Docker build using infra Dockerfile
- Docker push to Docker Hub
- Deploy to EKS (apply + set image + rollout)

## Why Jenkins Master–Slave

Master stays stable (UI + scheduling).
Slave runs heavy tasks (build, docker, kubectl).
Scales easily by adding more agents.
