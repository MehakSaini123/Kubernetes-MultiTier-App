# Kubernetes Multi-Tier Application

## Project Overview

This project demonstrates a simple multi-tier application deployed on Kubernetes using Nginx as the frontend and MySQL as the backend with persistent storage.

## Components

- Nginx Frontend
- MySQL Backend
- Persistent Volume (PV)
- Persistent Volume Claim (PVC)
- MySQL ClusterIP Service
- Nginx NodePort Service

## Project Structure

```
Kubernetes-MultiTier-App/
│── mysql-pv.yaml
│── mysql-pvc.yaml
│── mysql-deployment.yaml
│── mysql-service.yaml
│── nginx-deployment.yaml
│── nginx-service.yaml
│── README.md
└── screenshots/
```

## Deployment Commands

```bash
kubectl apply -f mysql-pv.yaml
kubectl apply -f mysql-pvc.yaml
kubectl apply -f mysql-deployment.yaml
kubectl apply -f mysql-service.yaml
kubectl apply -f nginx-deployment.yaml
kubectl apply -f nginx-service.yaml
```

## Verification Commands

```bash
kubectl get pv
kubectl get pvc
kubectl get deployments
kubectl get pods
kubectl get svc
kubectl get all
```

## Testing

### Verify MySQL

```bash
kubectl exec -it <mysql-pod-name> -- bash
mysql -uroot -ppassword
SHOW DATABASES;
```

### Verify Internal Networking

```bash
kubectl run testpod7 --image=busybox --restart=Never -it -- sh

nslookup mysql-service

wget -qO- nginx-service
```

## Results

- Successfully deployed MySQL with Persistent Volume.
- Successfully deployed Nginx frontend.
- Verified MySQL database creation.
- Verified Kubernetes DNS resolution.
- Verified communication between frontend and backend services.
- Successfully accessed the Nginx application through the NodePort service.