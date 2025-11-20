📘 Task 5 – Kubernetes Deployment using Minikube

This project is part of the DevOps Internship – Task 5, where the goal is to deploy and manage applications on a Kubernetes cluster using Minikube, kubectl, and Docker.

🚀 Objective

Install & run a Kubernetes cluster locally using Minikube

Create Kubernetes objects using YAML

Deploy an application using a Deployment

Expose the application using a Service (NodePort)

Scale the deployment

View logs, describe resources, and take screenshots

Push all YAML + screenshots to GitHub

🛠️ Tools Used

Minikube

Kubernetes (kubectl)

Docker Engine (WSL2 backend)

Ubuntu (WSL2)

Git & GitHub

📂 Project Structure
task5-kubernetes/
│
├── deployment.yaml
├── service.yaml
├── screenshots/
│     ├── pods_running.png
│     ├── service_list.png
│     ├── app_open_in_browser.png
│     ├── scaled_pods.png
│     └── pod_describe.png
│
└── README.md

📄 YAML Files
1. deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: hello-app
  template:
    metadata:
      labels:
        app: hello-app
    spec:
      containers:
      - name: hello-container
        image: nginx
        ports:
        - containerPort: 80

2. service.yaml
apiVersion: v1
kind: Service
metadata:
  name: hello-service
spec:
  type: NodePort
  selector:
    app: hello-app
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30036

📌 Commands Used
Start Minikube
minikube start --driver=docker

Apply Deployment
kubectl apply -f deployment.yaml
kubectl get pods

Apply Service
kubectl apply -f service.yaml
kubectl get svc

Access Application
minikube service hello-service

Scale Deployment
kubectl scale deployment hello-deployment --replicas=3
kubectl get pods

Describe Pod
kubectl describe pod <pod-name>

🖼️ Screenshots Included

Pods running

Service created

Application opened in browser

Scaled pods

Describe pod output

All screenshots are stored inside the screenshots/ folder.

🎯 Outcome

By completing this task, I learned:

How Kubernetes deployments work

How to expose pods using services

How scaling works in Kubernetes

How to inspect Kubernetes resources

How Minikube simulates a real Kubernetes cluster locally

📤 Submission

This repository contains:

✔ YAML files
✔ Screenshots
✔ README explanation

🙌 Thank You!

Feel free to check the YAML files and steps to understand the entire Kubernetes workflow.
