# 🚀 Kubernetes Minikube Setup & Namespace Management

## 📌 Project Overview

This project demonstrates the setup of a local Kubernetes cluster using Minikube on Ubuntu (WSL) and explores Kubernetes namespace management. The objective is to understand the basics of Kubernetes, cluster creation, namespace isolation, pod deployment, and resource management.

Kubernetes is a container orchestration platform used to automate deployment, scaling, and management of containerized applications. Minikube provides a lightweight local Kubernetes environment for learning and development purposes.

---

## 🛠️ Technologies Used

* Ubuntu (WSL)
* Docker
* Kubernetes
* Kubectl
* Minikube

---

## 🏗️ Architecture

```text
Windows System
      │
      ▼
Ubuntu (WSL)
      │
      ├── Docker
      ├── Kubectl
      └── Minikube
              │
              ▼
      Kubernetes Cluster
              │
              ▼
         Namespace
              │
              ▼
             Pod
```

---

## ⚙️ Installation and Configuration

### 1. Update Ubuntu Packages

```bash
sudo apt update
sudo apt upgrade -y
```
<img width="1919" height="558" alt="image" src="https://github.com/user-attachments/assets/bae3fce0-a108-4954-8f37-6fbdd6d35e96" />


### 2. Install Docker

```bash
sudo apt install docker.io -y
```
<img width="1919" height="236" alt="image" src="https://github.com/user-attachments/assets/0c19a333-3ed5-4095-a43a-687f0fe52ca2" />

Verify Docker installation:

```bash
docker --version
docker ps
```
<img width="1917" height="209" alt="image" src="https://github.com/user-attachments/assets/f03a27fb-d872-497a-abee-dea1b5d825ee" />


### 3. Install Kubectl

Download kubectl:

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

Make executable:

```bash
chmod +x kubectl
```

Move to system path:

```bash
sudo mv kubectl /usr/local/bin/
```
<img width="1919" height="734" alt="image" src="https://github.com/user-attachments/assets/870e74fa-5023-4dba-9eb3-f9e893255a1b" />


Verify installation:

```bash
kubectl version --client
```
<img width="1908" height="67" alt="image" src="https://github.com/user-attachments/assets/204173ef-fbfa-4d15-8763-e287cadc947b" />

### 4. Install Minikube

Download Minikube:

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

Install:

```bash
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

Verify:

```bash
minikube version
```
<img width="1919" height="720" alt="image" src="https://github.com/user-attachments/assets/f57144eb-0298-44b8-ba76-55309d19b6ab" />


---

## 🚀 Starting the Kubernetes Cluster

Start Minikube using Docker driver:

```bash
minikube start --driver=docker
```

Verify cluster status:

```bash
kubectl get nodes
```

Expected output:

```text
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   XXm   v1.xx.x
```

---

## 📦 Namespace Management

List existing namespaces:

```bash
kubectl get namespaces
```

Create a new namespace:

```bash
kubectl create namespace development
```

Verify namespace creation:

```bash
kubectl get namespaces
```

---

## 🌐 Pod Deployment

Deploy an Nginx pod inside the namespace:

```bash
kubectl run web-server --image=nginx -n development
```

Check pod status:

```bash
kubectl get pods -n development
```

Expected output:

```text
NAME         READY   STATUS    RESTARTS   AGE
web-server   1/1     Running   0          XXs
```

---

## 📊 Resource Monitoring

View all resources in the namespace:

```bash
kubectl get all -n development
```

Describe namespace details:

```bash
kubectl describe namespace development
```

View pods from all namespaces:

```bash
kubectl get pods -A
```

---

## 🖥️ Kubernetes Dashboard

Launch the Kubernetes dashboard:

```bash
minikube dashboard
```

The dashboard provides a graphical interface for monitoring cluster resources, namespaces, pods, services, and workloads.

---

## 📷 Screenshots

The following screenshots are included as proof of execution:

* cluster-started.png
* cluster-nodes.png
* namespace-list.png
* pod-status.png
* dashboard-home.png
* dashboard-pods.png

---

## 🎯 Learning Outcomes

Through this project, the following concepts were explored:

* Kubernetes cluster setup using Minikube
* Docker integration with Kubernetes
* Kubectl command-line operations
* Namespace creation and management
* Pod deployment and monitoring
* Kubernetes Dashboard usage
* Basic Kubernetes resource administration

---

## ✅ Conclusion

Successfully installed Docker, Kubectl, and Minikube on Ubuntu (WSL), created a local Kubernetes cluster, managed namespaces, deployed an Nginx pod, monitored resources using kubectl commands, and explored the Kubernetes Dashboard. This project provided practical exposure to Kubernetes fundamentals and namespace-based resource isolation.
