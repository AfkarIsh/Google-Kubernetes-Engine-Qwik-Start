# Google Kubernetes Engine: Qwik Start

A complete walkthrough of orchestration using **Google Kubernetes Engine (GKE)**.

---

## 🗺️ High-Level Project Overview

In this lab, you successfully performed **orchestration** using **Google Kubernetes Engine (GKE)**.

Instead of manually configuring virtual machines, installing dependencies, and managing network routing step-by-step, you commanded Google Cloud to spin up a managed environment. GKE automatically handled the infrastructure provisioning, container deployment, load balancing, and cleanup.

---

## 🛠️ Detailed Component Breakdown

### 1. The GKE Cluster (`lab-cluster`)

* **What it is:** A group of Compute Engine virtual machine instances (called **Nodes**) bundled together to run your containerized applications.
* **The Details:** Your cluster automatically deployed with **3 nodes** using an `e2-medium` machine type in the `us-east4-c` zone. It includes a built-in Kubernetes Control Plane that continuously health-checks your machines to ensure they stay up and running.

### 2. The Container Image (`hello-app:1.0`)

* **What it is:** A lightweight, standalone, executable package that includes everything needed to run your piece of software (code, runtime, system tools, system libraries, and settings).
* **The Details:** GKE pulled this specific image version from a Google Container Registry bucket (`gcr.io/google-samples/hello-app:1.0`).

### 3. The Deployment (`hello-server`)

* **What it is:** A Kubernetes object that manages your stateless applications.
* **The Details:** When you ran `kubectl create deployment`, you instructed Kubernetes to create and look after a copy of your container. If that container ever crashes, the deployment automatically spins a new one back up to take its place.

### 4. The Service (`LoadBalancer`)

* **What it is:** A resource that routes external internet traffic into your internal cluster containers.
* **The Details:** By default, containers are isolated. Exposing it as a `LoadBalancer` spins up a physical Google Cloud Load Balancer with a unique public **External IP** address, mapping port `8080` so anyone on the web can reach your app.

### 5. Cluster Deletion (`gcloud container clusters delete`)

* **What it is:** The teardown phase of your infrastructure.
* **The Details:** Deleting the cluster removes the 3 compute instances and the load balancer. In a cloud environment, this is crucial to prevent ongoing billing charges once your workload is no longer needed.

---

## 🎯 Final Checklist Status

* **Task 1: Set a default compute zone** — `SUCCESS` (Configured to `us-east4-c`)
* **Task 2: Create a GKE cluster** — `SUCCESS` (`lab-cluster` status changed to `RUNNING`)
* **Task 3: Get authentication credentials** — `SUCCESS` (Kubeconfig credentials linked to Cloud Shell)
* **Task 4: Deploy an application** — `SUCCESS` (Created deployment `hello-server`)
* **Task 5: Create a Kubernetes Service** — `SUCCESS` (LoadBalancer exposed and public IP allocated)
* **Task 6: Delete the cluster** — `SUCCESS` (Targeted explicit zone deletion to wipe the infrastructure cleanly)

Your lab tracking on the [Google Kubernetes Engine: Qwik Start](https://www.skills.google/games/7176/labs/44463) page should now reflect your completed progress steps perfectly!