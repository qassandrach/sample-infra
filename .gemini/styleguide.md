# Kubernetes Manifest Style Guide

# Introduction  
This style guide outlines the conventions for writing Kubernetes manifests at Company X.  
It aims to promote readability, maintainability, consistency, and security across all Kubernetes configurations.

# Key Principles  
* **Readability:** YAML manifests should be easy to understand for all team members.  
* **Maintainability:** Manifests should be simple to modify, version, and extend.  
* **Consistency:** A unified structure and naming scheme improves collaboration and review.  
* **Security:** Follow Kubernetes security best practices to reduce risk in production.  
* **Modularity:** Isolate concerns across files for reuse and clear change tracking.

# File Organization

## File Naming  
* Use lowercase with hyphens: `deployment-app.yaml`, `service-app.yaml`, `configmap-app.yaml`  
* Prefer one resource per file unless closely related  
* Store all manifests under a directory like `k8s/` or `manifests/`

## Directory Structure (Example)
k8s/
├── base/
│ ├── namespace.yaml
│ ├── deployment.yaml
│ ├── service.yaml
│ └── configmap.yaml
└── overlays/
├── dev/
│ └── kustomization.yaml
└── prod/
└── kustomization.yaml



# Manifest Structure

## Field Order (Recommended)
```yaml
apiVersion:
kind:
metadata:
  name:
  namespace:
  labels:
  annotations:
spec:
```
* Always define namespace explicitly.

* Group and order fields logically within spec.


## Labels and Annotations

```yaml
labels:
  app.kubernetes.io/name: my-app
  app.kubernetes.io/instance: my-app-prod
  app.kubernetes.io/version: "1.2.3"
  app.kubernetes.io/component: backend
  app.kubernetes.io/part-of: my-platform
  app.kubernetes.io/managed-by: kustomize
annotations:
  owner: team-devops
  documentation: https://docs.internal/my-app
```
