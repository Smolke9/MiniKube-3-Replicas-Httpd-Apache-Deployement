# 🚀 Kubernetes Deployment of httpd (Apache) with 3 Replicas

This project demonstrates how to create a Kubernetes Deployment with 3 replicas of the `httpd` (Apache) container using `kubectl`.

---

## 🧰 Prerequisites

- Minikube or any Kubernetes cluster running
- kubectl installed and configured

---

## 📦 Step 1: Start Minikube (if using Minikube)

```bash
minikube start
```

---

## 📄 Step 2: Create Deployment YAML

Create a file named `httpd-deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: httpd-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: httpd
  template:
    metadata:
      labels:
        app: httpd
    spec:
      containers:
      - name: httpd
        image: httpd:latest
        ports:
        - containerPort: 80
```

Save and exit the file.

---

## 🚀 Step 3: Apply the Deployment

```bash
kubectl apply -f httpd-deployment.yaml
```

---

## 🔍 Step 4: Verify the Deployment and Pods

```bash
kubectl get deployments
kubectl get pods
kubectl get rs
```

---

## 🌐 Step 5: Expose the Deployment (Optional)

```bash
kubectl expose deployment httpd-deployment --type=NodePort --port=80
```

---

## 🌍 Step 6: Access the Service

Get the service URL (Minikube only):

```bash
minikube service httpd-deployment --url
```

Open the URL in your browser.

---

## 🧹 Cleanup

### 🗑️ Option 1: Delete Only Pod (Temporary)

```bash
kubectl delete pod <pod-name>
```

> ⚠️ Pod will be recreated automatically by the Deployment.

### 🗑️ Option 2: Delete Entire Deployment (Recommended)

```bash
kubectl delete deployment httpd-deployment
```

### 🗑️ Option 3: Delete Service (if exposed)

```bash
kubectl delete service httpd-deployment
```

---

## ✅ Final Check

```bash
kubectl get all
```

> This command will show all resources (pods, deployments, services, etc.)

---

## 💡 Bonus: Example with nginx Deployment Pod Deletion

```bash
kubectl delete pod nginx-deploy-8467876bbf-2v429
```

> But it will be recreated unless the deployment is also deleted:

```bash
kubectl delete deployment nginx-deploy
```

---

## 📸 Useful for Assignment Screenshots

```bash
kubectl get deployments
kubectl get pods
kubectl describe deployment httpd-deployment
kubectl get svc
```

---

## 📁 Directory Structure

```
.
├── httpd-deployment.yaml
└── README.md
```

---


