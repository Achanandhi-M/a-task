# GoLang Date & Time Web Application

## Overview
This project is a simple GoLang web application that displays the current date and time. The application is containerized using Docker, pushed to DockerHub, and deployed to Kubernetes with two replicas using a declarative approach. The application is exposed to the internet using a Kubernetes LoadBalancer service.

## Project Structure
```
├── Dockerfile
├── main.go
├── k8s-manifests/
│   ├── deployment.yaml
│   ├── service.yaml
└── README.md
```

## Step 1: Create and Push Docker Image

### Build and Run Locally
Ensure you have Go installed and set up.

```sh
# Clone the repository
git clone <repo-url>
cd <repo-name>

# Run the application locally
go run main.go
```

### Docker Build and Push

```sh
# Build the Docker image
docker build -t achanandhi/a-image:v1 .

# Login to DockerHub
docker login

# Push the image to DockerHub
docker push achanandhi/a-image:v1
```

## Step 2: Deploy to Kubernetes

### Apply Deployment and Service Manifests
Ensure you have a Kubernetes cluster running and kubectl configured.

```sh
kubectl apply -f k8s-manifests/deployment.yaml
kubectl apply -f k8s-manifests/service.yaml
```

### Verify Deployment

```sh
kubectl get pods
kubectl get deployments
kubectl get services
```

## Step 3: Access the Application

Once deployed, you can access the application using the external IP of the LoadBalancer service:

```sh
kubectl get svc my-go-app-service
```

Find the `EXTERNAL-IP` and open it in your browser.

## Conclusion
This project demonstrates deploying a simple GoLang web application on Kubernetes using Docker. It follows best practices by using a multi-stage build and declarative Kubernetes manifests for deployment. 🎉

