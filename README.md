# DevOps Task - CI/CD Demo

## Summary
Simple Node.js app (single endpoint that shows a logo) with CI/CD pipeline using Jenkins, Docker, Amazon ECR and ECS (EC2 launch type). This repo contains application code, Jenkinsfile, Dockerfile, and documentation.

## Repo layout
- `app/` - Node.js app
- `Dockerfile` - image build instructions
- `Jenkinsfile` - pipeline (build, push to ECR, register task def, update ECS service)
- `deployment-proof/` - screenshots

## How to run (high-level)
1. Push this repo to GitHub (`dev` branch for work, `main` for final).
2. Create ECR repo (or allow pipeline to create it).
3. Create ECS cluster (EC2 launch type) and add 1 t2.micro container instance (free-tier).
4. Create Task Execution Role (`AmazonECSTaskExecutionRolePolicy`).
5. Launch Jenkins on a separate EC2 instance; install Docker, AWS CLI, jq.
6. Add Jenkins credential `aws-creds` (username=AWS_ACCESS_KEY_ID, password=AWS_SECRET_ACCESS_KEY).
7. In Jenkins create a Pipeline job pointing to this repo and run it.
8. After successful run, visit `http://<ECS_INSTANCE_PUBLIC_IP>:3000` or the ALB DNS for public access.

## Deployment proof
See `/deployment-proof` folder for screenshots and deployed URL.

## Viewing logs & monitoring
- CloudWatch log group: `/ecs/devops-task`
- ECS service and tasks: AWS Console → ECS → Clusters → your cluster

