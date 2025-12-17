# MongoDB & Mongo Express Deployment on Kubernetes with AWS EBS

##  Project Overview

This project demonstrates how to deploy a **MongoDB database** with **Mongo Express web interface** on **Kubernetes**, using **AWS EBS** for persistent storage.

The deployment includes:

* MongoDB with **persistent storage** using EBS
* Mongo Express web interface to manage the database
* Kubernetes **Secrets** for credentials
* Kubernetes **ConfigMap** for database configuration
* LoadBalancer Services for external access
* Full lifecycle management (Deploy + PVC + PV + StorageClass + Cleanup)

---

##  Technologies Used

* Kubernetes (Deployments, Services, PVC, PV, StorageClass, Secrets, ConfigMaps)
* AWS EBS for persistent storage
* MongoDB database
* Mongo Express web interface

---

##  Project Structure

```
mongodb-project/
├── mongodb-secret.yaml       # Secret for MongoDB credentials
├── mongodb-sc.yaml           # StorageClass for MongoDB (EBS)
├── mongodb-pvc.yaml          # PersistentVolumeClaim for MongoDB
├── mongodb-app.yaml          # MongoDB Deployment
├── mongodb-svc.yaml          # MongoDB Service
├── mongodb-cm.yaml           # ConfigMap for Mongo Express
├── mongo-express-app.yaml    # Mongo Express Deployment
└── mongo-express-svc.yaml    # Mongo Express Service (LoadBalancer)
```

---

##  How to Deploy

### 1- Create AWS Credentials Secret

```bash
kubectl create secret generic aws-secret \
  --namespace kube-system \
  --from-literal "key_id=<AWS_ACCESS_KEY_ID>" \
  --from-literal "access_key=<AWS_SECRET_ACCESS_KEY>"
```

---

### 2- Create MongoDB Secret

```bash
kubectl apply -f mongodb-secret.yaml
```

---

### 3- Set up Storage

```bash
kubectl apply -f mongodb-sc.yaml
kubectl apply -f mongodb-pvc.yaml
```

---

### 4- Deploy MongoDB

```bash
kubectl apply -f mongodb-app.yaml
kubectl apply -f mongodb-svc.yaml
```

Check Pods and PVC:

```bash
kubectl get po
kubectl get pvc
kubectl get pv
```

---

### 5- Deploy Mongo Express

```bash
kubectl apply -f mongodb-cm.yaml
kubectl apply -f mongo-express-app.yaml
kubectl apply -f mongo-express-svc.yaml
```

---

### 6- Access Mongo Express

Get the external IP of the LoadBalancer service:

```bash
kubectl get svc mongo-express-svc
```

Open in browser:

```
http://<EXTERNAL-IP>:8081
```

---

### 7- Cleanup Resources

```bash
kubectl delete -f mongodb-project/
```

---

##  Key Learning Outcomes

* Deploy MongoDB with persistent storage on Kubernetes (AWS EBS)
* Deploy Mongo Express web interface with ConfigMap and Secrets
* Use StorageClasses, PVCs, PVs, and LoadBalancer Services
* Manage full Kubernetes lifecycle for database applications
* Understand integration between Kubernetes and AWS cloud storage

---

##  Author

ahmed mostafa






---

### ✅ نسخة مفصلة (لـ Projects أو Experience section)

**MongoDB & Mongo Express Deployment on Kubernetes**

* Deployed a MongoDB database with Mongo Express web interface on Kubernetes using AWS EBS for persistent storage.
* Managed **Secrets** for credentials and **ConfigMaps** for configuration.
* Configured **StorageClasses, PVCs, PVs, and LoadBalancer Services**.
* Implemented full Kubernetes lifecycle management including deployment, scaling, and cleanup.

---

### 🔹 نسخة مختصرة (لـ CV محدود المساحة)

* Deployed MongoDB + Mongo Express on Kubernetes with AWS EBS storage, Secrets, ConfigMaps, and LoadBalancer.

---


