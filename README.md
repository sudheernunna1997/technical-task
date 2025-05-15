# FastAPI Kubernetes Interview Task

This repository contains a small FastAPI application intended for a technical interview task.

## Technical Task

Imagine this is a production application that needs to be deployed to a Kubernetes cluster.

Your task is to:

- Fork this repository.
- Understand the application code.
- Create a **Dockerfile** to containerise the application.
- Write a **Kubernetes Deployment YAML** file that deploys the application correctly.
- **Implement automated testing** using a CI tool of your choice (e.g., GitHub Actions, GitLab CI, Jenkins), running the tests in the provided `tests.py` script.
- **Build and deploy** the application locally using your preferred Kubernetes environment (e.g., Minikube, Kind).

---

## Resource Requirements

Please assume the following **resource needs** for the container:

| Resource | Recommended Value |
|:---------|:-------------------|
| CPU Request | `100m` |
| CPU Limit | `250m` |
| Memory Request | `128Mi` |
| Memory Limit | `512Mi` |

You are expected to define these in your Deployment YAML.

FastAPI Kubernetes Deployment

Tools Used

- FastAPI– Python web framework for building APIs
- Docker – For containerizing the application
- kind (Kubernetes IN Docker) – To create a local Kubernetes cluster
- kubectl – To interact with the Kubernetes cluster
  
Follow these steps to run the FastAPI app on a local Kubernetes cluster using kind.

Make sure the following are installed:

- Docker Desktop
- kubectl
- kind
  
Build and Push the Docker Image:

If you want to use your own image:

docker build -t <your-dockerhub-username>/fastapi-app:latest .
docker push <your-dockerhub-username>/fastapi-app:latest

In my case, the image is already built and pushed:

sudheer123143/fastapi-app:latest

 Apply Kubernetes Manifests
 
kubectl apply -f deployment.yaml

Check the Deployment

kubectl get pods
kubectl get svc
Access the App:

If you're using NodePort, use the following command,

kubectl port-forward service/fastapi-service 8080:80

Now open your browser and go to,

http://localhost:8080

 Output,
 
{"message":"Hello from production environment!"}

Continuous Integration (CI) with GitHub Actions

This project uses GitHub Actions to automate testing and building the Docker image on every push or pull request.
The CI workflow:
- Checks out the code
- Sets up Python environment
- Installs dependencies
- Runs tests (if any)
How to use the CI workflow
- The workflow triggers on every push and pull request to the main branch.
- You can check the Actions tab on GitHub to see the status of your workflows.




