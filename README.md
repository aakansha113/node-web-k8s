# 🚀 Node Web App Deployment on Kubernetes (Minikube)

This repository contains a **Node.js web application** containerized using **Docker** and deployed on **Kubernetes (Minikube)**.
The project demonstrates an **end-to-end DevOps workflow**:
**Node.js → Docker → Docker Hub → Kubernetes (Minikube)**

---

## 📁 Project Structure

```
project
├── Dockerfile
├── README.md
├── package.json
├── package-lock.json
├── node_modules
├── public
├── src
```

---

## 🐳 Docker Image

Docker image is already built and pushed to Docker Hub:

```
aakansha113/node-web-app:latest
```

🔗 Docker Hub Repository:
[https://hub.docker.com/repository/docker/aakansha113/node-web-app/general](https://hub.docker.com/repository/docker/aakansha113/node-web-app/general)

---

## ⚙️ Prerequisites

Make sure you have the following installed:

* Docker
* Minikube
* kubectl
* Git

Verify installation:

```
docker --version
minikube version
kubectl version --client
```

---

## ▶️ Start Minikube

Start Minikube using Docker driver:

```
minikube start --driver=docker
```

Check status:

```
minikube status
```

---

## 📦 Kubernetes Deployment (Imperative – No YAML)

### 1️⃣ Create Deployment

```
kubectl create deployment node-web-app \
  --image=aakansha113/node-web-app:latest
```

Verify deployment:

```
kubectl get deployments
kubectl get pods
```

---

### 2️⃣ Expose Deployment as Service

Expose the app using **NodePort**:

```
kubectl expose deployment node-web-app \
  --type=NodePort \
  --port=3000
```

Check service:

```
kubectl get services
```

---

### 3️⃣ Access Application (Option 1 – Minikube Service)

```
minikube service node-web-app
```

This command will automatically open the app in the browser.

---

### 4️⃣ Access Application (Option 2 – Port Forwarding)

```
kubectl port-forward service/node-web-app 3000:3000
```

Now open in browser:

```
http://localhost:3000
```

---

## 🔍 Logs & Debugging

View pod logs:

```
kubectl get pods
kubectl logs <pod-name>
```

Describe pod:

```
kubectl describe pod <pod-name>
```

---

## 🧹 Cleanup Resources

Delete service and deployment:

```
kubectl delete service node-web-app
kubectl delete deployment node-web-app
```

Stop Minikube:

```
minikube stop
```

---

## 🎯 Key Learnings

* Containerizing a Node.js app using Docker
* Pushing image to Docker Hub
* Deploying applications on Kubernetes using **imperative kubectl commands**
* Exposing services using NodePort
* Accessing applications via Minikube & Port Forwarding

---

## 👩‍💻 Author

**Akshu Hujare**
Aspiring DevOps Engineer 🚀

---

## ⭐ If you like this project

Give it a ⭐ on GitHub and feel free to fork & experiment!


