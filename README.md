# Minikube-Kubernetes-Demo
This repository demonstrates how to set up and run a simple Kubernetes cluster locally using **Minikube**. It includes deploying a MongoDB backend and a web application frontend with Kubernetes manifests.

Getting Started
1. Start Minikube
minikube start


This spins up a local single-node Kubernetes cluster.

2. Apply Kubernetes Manifests

Apply the MongoDB secret and deployments:

kubectl apply -f mongo-secret.yaml
kubectl apply -f mongo-deployment.yaml
kubectl apply -f webapp-deployment.yaml

3. Verify Pods and Services

Check the status of your pods:

kubectl get pods


Check the services:

kubectl get svc

4. Access the Web Application

If your web app service type is NodePort, get the Minikube IP and port:

minikube ip
kubectl get svc webapp-service


Then open http://<MINIKUBE_IP>:<NODE_PORT> in your browser.

Alternatively, run:

minikube service webapp-service


This opens the service URL in your default browser.

5. Updating the Web Application Image

If you update the container image for the web app in the deployment YAML:

Apply the changes:

kubectl apply -f webapp-deployment.yaml


Then restart the deployment to ensure pods use the new image:

kubectl rollout restart deployment webapp-deployment


Verify rollout status:

kubectl rollout status deployment/webapp-deployment
