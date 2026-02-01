# GKE Microservices Project (Backend + Frontend)

This project demonstrates a **simple microservices architecture deployed on Google Kubernetes Engine (GKE)** using Docker, Artifact Registry, and Kubernetes manifests. It is designed as a **learning-first DevOps project**, focusing on fundamentals rather than automation at the start.

---

## 📌 Project Overview

* **Backend**: Python Flask application
* **Frontend**: Nginx serving a static HTML page
* **Container Registry**: Google Artifact Registry
* **Orchestration**: Kubernetes (GKE)
* **Namespace**: `dev`

The backend and frontend are deployed as separate services inside the same Kubernetes namespace.

---

## 📂 Directory Structure

```
gke-microservices-project/
├── backend
│   ├── app.py
│   └── Dockerfile
├── frontend
│   ├── index.html
│   ├── Dockerfile
│   └── nginx.conf
└── k8s
    ├── namespaces
    │   └── dev.yaml
    ├── backend
    │   ├── deployment.yaml
    │   └── service.yaml
    └── frontend
        ├── deployment.yaml
        └── service.yaml
```

---

## 🧱 Backend Service

### Application

* Python Flask app
* Exposes `/` endpoint
* Runs on port `5000`

### Docker

* Base image: `python:3.10-slim`
* Flask installed via pip

### Kubernetes

* Deployment with **2 replicas**
* Service type: **LoadBalancer**

---

## 🎨 Frontend Service

### Application

* Static HTML page
* Served using **Nginx**

### Docker

* Base image: `nginx:latest`
* Custom `index.html`

### Kubernetes

* Deployment with **2 replicas**
* Service type: **LoadBalancer**

---

## ☸️ Kubernetes Setup

### Namespace

All resources are deployed inside the `dev` namespace:

```bash
kubectl apply -f k8s/namespaces/dev.yaml
```

### Apply Backend

```bash
kubectl apply -f k8s/backend/
```

### Apply Frontend

```bash
kubectl apply -f k8s/frontend/
```

---

## 🚀 Accessing the Application

After deployment, fetch the external IPs:

```bash
kubectl get svc -n dev
```

* Frontend URL → Browser access
* Backend URL → `curl` or browser

---

## 🛠️ Tools Used

* Google Cloud Platform (GCP)
* Google Kubernetes Engine (GKE)
* Docker
* Google Artifact Registry
* Kubernetes (kubectl)
* Git & GitHub

---

## 🎯 Learning Goals

* Understand containerization with Docker
* Push images to Artifact Registry
* Deploy and expose services in Kubernetes
* Debug common Kubernetes issues (CrashLoopBackOff, ImagePullBackOff)
* Organize real-world DevOps project structure

---

## 🔮 Future Improvements

* Use **Ingress** instead of LoadBalancer
* Add **ConfigMaps & Secrets**
* Backend-to-Frontend internal service communication
* CI/CD with GitHub Actions
* Terraform for infrastructure provisioning

---

## 🧹 Cleanup

To delete everything:

```bash
kubectl delete namespace dev
gcloud container clusters delete <cluster-name>
```

---

## ✨ Author

**Subhojit Das**
Aspiring DevOps Engineer | RHCSA | CKA

---

> This project is intentionally built step-by-step to strengthen core DevOps concepts before automation.
