# AWS Infrastructure Setup

## EC2 Instances (Tooling Hosts)

- jenkins (master) — Jenkins UI + controller
- jenkins-slave — build agent (Maven/Docker/kubectl)
- sonar — SonarQube server
- nexus — Nexus Repository Manager
- kube (optional) — management host for kubectl + kubeconfig (training approach)
- EKS NodeGroup instances — run pods

## Ports (Typical Lab Setup)

> Prefer SG-to-SG or lock to your IP.

- Jenkins: 8080, 22
- SonarQube: 9000, 22
- Nexus: 8081, 22
- RDS MySQL: 3306 (restricted)
- Frontend ELB: 80

## Region

ap-south-1 (Mumbai)
