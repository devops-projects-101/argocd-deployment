# 🚀 ArgoCD GitOps Repository: Grade Submission API

This repository contains the Kubernetes manifests for deploying the **Grade Submission API** application using a GitOps workflow managed by **ArgoCD**.

---

## 🏗️ Project Overview

This repository serves as the "source of truth" for the application's desired state. Any changes to the `deployment.yaml` file, such as updating the container image tag, will be automatically detected and applied to the target Kubernetes cluster by ArgoCD.

The application is deployed as a single Kubernetes manifest file (`deployment.yaml`) that includes both the Deployment and the Service.

### Application Details

| Component | Type | Details |
| :--- | :--- | :--- |
| **Application** | Grade Submission API (`grade-submission-api`) | Node.js/JavaScript application |
| **Namespace** | `default` | Target Kubernetes Namespace |
| **Deployment Image** | `ghcr.io/devops-projects-101/js-app-k8s:1594b0932d028d2ec07e020fdff43cdcbfa36e78` | Hosted on GitHub Container Registry (GHCR) |
| **Exposure** | `ClusterIP` Service on Port `80` | Internal cluster access |

---

## 💾 Kubernetes Manifest (`deployment.yaml`)

The manifest defines the resources required for the application:

### 1. Deployment (`grade-submission-api`)

* **Replicas:** `1`
* **Container Port:** `3000`
* **Resource Limits:** 500m CPU, 256Mi Memory
* **Image Pull Secret:** Uses `ghcr-secret` to authenticate with GitHub Container Registry.

### 2. Service (`grade-submission-api`)

* **Type:** `ClusterIP`
* **Port Mapping:** Maps external port `80` to the container port `3000`.

```yaml
apiVersion: apps/v1
kind: Deployment
# ... (Full Deployment manifest content)
---
apiVersion: v1
kind: Service
# ... (Full Service manifest content)
