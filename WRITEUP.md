# WRITEUP

## Tools & Services used
- GitHub (source repo)
- Jenkins (CI/CD server on EC2)
- Docker (build images)
- Amazon ECR (image registry)
- Amazon ECS (EC2 launch type)
- Amazon EC2 (Jenkins & ECS container instance)
- CloudWatch (logs & monitoring)

## Steps completed
1. Create Git repo and push code (app, Dockerfile, Jenkinsfile).
2. Setup Jenkins on EC2, added AWS credentials.
3. Built image in Jenkins, pushed to ECR.
4. Registered new ECS task definition revision pointing to new image.
5. Updated ECS service to deploy new revision.
6. Verified app reachable and logs visible in CloudWatch.

## Challenges faced & solutions
Service kept using sample image — cause: task definition was not re-registered. Solution: pipeline now registers new revision and updates service.

