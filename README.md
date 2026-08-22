# CI/CD webhook test
## CI/CD Pipeline Test
# E-Commerce DevOps CI/CD Project

## Project Overview

This project demonstrates a real-time DevOps CI/CD pipeline for deploying an E-Commerce application using GitHub, Jenkins, Docker, Docker Hub and AWS EC2.

## Architecture

Developer
   |
   | Git Push
   v
GitHub
   |
   | Webhook
   v
Jenkins
   |
   | Docker Build
   v
Docker Image
   |
   | Push
   v
Docker Hub
   |
   | Pull
   v
AWS EC2
   |
   | Docker Container
   v
E-Commerce Application

## Technologies Used

- Git
- GitHub
- Jenkins
- Docker
- Docker Hub
- AWS EC2
- Ubuntu
- Python
- Flask
- CI/CD
- Docker Healthcheck

## CI/CD Pipeline Flow

1. Developer pushes code to GitHub.
2. GitHub Webhook triggers Jenkins automatically.
3. Jenkins checks out the latest source code.
4. Jenkins builds the Docker image.
5. Jenkins creates a versioned Docker image.
6. Jenkins tags the image as `latest`.
7. Jenkins logs into Docker Hub securely.
8. Jenkins pushes the Docker images to Docker Hub.
9. Jenkins pulls the latest image on EC2.
10. Jenkins stops the old container.
11. Jenkins removes the old container.
12. Jenkins starts a new container.
13. Docker Healthcheck verifies the application.
14. Application becomes available on port 5000.

## Docker Images

Docker Hub Repository:

`dhaneshpathare/ecommerce-devops`

Images:

- `dhaneshpathare/ecommerce-devops:7`
- `dhaneshpathare/ecommerce-devops:latest`

## Deployment

Application runs inside Docker on AWS EC2.

Container:

`ecommerce-app`

Port:

`5000:5000`

## Health Check

Docker HEALTHCHECK verifies the application endpoint:

`http://localhost:5000`

Expected response:

`E-Commerce DevOps Application is Running!`

Container status:

`Up (healthy)`

## Security

AWS Security Group allows:

- SSH - Port 22
- HTTP - Port 80
- Custom TCP - Port 5000

Ubuntu UFW was verified as inactive during deployment testing.

## Testing

The CI/CD pipeline was tested using a GitHub README change.

Result:

`Started by GitHub push by dhanesh-pathare`

Final result:

`Finished: SUCCESS`

Docker container:

`Up (healthy)`

## Result

The project successfully implements automated CI/CD deployment from GitHub to Jenkins, Docker Hub and AWS EC2.

GitHub Push
→ Jenkins
→ Docker Build
→ Docker Hub
→ EC2 Deployment
→ Health Check
→ Live Application

## Interview Explanation

"I implemented an automated CI/CD pipeline using GitHub, Jenkins, Docker, Docker Hub and AWS EC2. A GitHub push triggers Jenkins through a webhook. Jenkins builds and versions the Docker image, pushes it to Docker Hub, pulls the latest image on EC2, replaces the old container and deploys the new version. Docker HEALTHCHECK verifies that the application is running successfully."
