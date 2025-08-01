Description - Deploy Grafana(docker image) using amazon ECS with fargate

This project involves deploying the official grafana/grafana Docker image on Amazon ECS using Fargate launch type. AWS Fargate allows you to run containers without managing servers. Grafana will be accessible via a public IP on port 3000, which is the default port for Grafana’s web UI.

Deliverables - Screenshots showing
- ECS cluster and running service
- Task definition with grafana/grafana image
- security group allowing port 3000 access
- Grafana login page in browser