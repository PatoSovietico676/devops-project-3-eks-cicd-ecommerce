# Architecture

## CI/CD Flow (Build & Deploy)

1. Developer pushes code to GitHub
2. Jenkins (pollSCM) detects changes
3. Jenkins Master schedules job
4. Jenkins Slave executes heavy tasks:
   - Build (Maven / Node)
   - SonarQube scan
   - Nexus upload (backend)
   - Docker build & push
   - kubectl apply + rollout

## Runtime Request Flow (User Traffic)

1. User opens the frontend ELB URL
2. Nginx serves Angular static files
3. Angular calls API using relative path: `/api/...`
4. Nginx proxies `/api/*` to `http://productssvc`
5. Backend pod fetches data from AWS RDS MySQL

## Why Backend Has No ELB

Backend service is `ClusterIP`:

- reachable only inside Kubernetes
- not exposed to internet
- reduces attack surface and removes public CORS needs
