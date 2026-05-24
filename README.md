# GKE Quickstart Project

This repository contains the setup to quickly spin up a Google Kubernetes Engine (GKE) cluster and deploy a live web application.

## 🚀 Quick Start / How to Run

### 1. Configure the Environment
Paste these commands into your Google Cloud Shell to target the correct zone:
```bash
gcloud config set compute/region us-east4
gcloud config set compute/zone us-east4-c
```

### 2. Launch the Cluster

Create the infrastructure (takes 3-5 minutes):

```bash
gcloud container clusters create --machine-type=e2-medium --zone=us-east4-c lab-cluster
```

### 3. Deploy & Expose the App

Run the application container and open it up to internet traffic:

```bash
kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:1.0
kubectl expose deployment hello-server --type=LoadBalancer --port 8080
```

### 4. Get Your Live URL

Run this command to find your public IP:

```bash
kubectl get service
```

*Wait for the `EXTERNAL-IP` to change from pending to a real IP address, then visit `http://<YOUR-EXTERNAL-IP>:8080` in your browser.*

---

## 🛑 Clean Up

When you are finished, don't forget to delete your cluster to avoid charges:

```bash
gcloud container clusters delete lab-cluster --zone=us-east4-c
```