# 🚀 Deploying NGINX on a Kind Kubernetes Cluster with External Access

This guide provides step-by-step instructions to set up an NGINX web server on a [Kind](https://kind.sigs.k8s.io/) Kubernetes cluster and expose it to your local network using a `NodePort` service and Kind's port mapping feature.

---

## 📋 Prerequisites

- [Docker](https://www.docker.com/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Kind](https://kind.sigs.k8s.io/)

---

## 🏗️ Step-by-Step Setup

###  1: clone the repo
```bash
git clone https://github.com/AhmedSayed7/NGINX-on-Kind-Kubernetes-Cluster.git
cd NGINX-on-Kind-Kubernetes-Cluster
```
### 2: Create Kind Cluster with Port Mapping
Make sure kind-config.yaml includes a port mapping for 30080:
```bash
kind create cluster --config kind-config.yaml
```
This maps container port 30080 to host port 30080, allowing NodePort access from other machines.
### 3: Deploy NGINX
```bash
kkubectl apply -f nginx-deployment.yaml
```
### 4: kubectl apply -f nginx-deployment.yaml
```bash
kubectl get pods
kubectl get svc nginx
```
You should see the nginx service running with type: NodePort and nodePort: 30080.



## 🌐 Accessing NGINX
From the host machine:
```bash
http://localhost:30080
```
## From another PC on the same network:
```bash
http://<host-machine-ip>:30080
```
