# Student Marketplace Helm Deployment 

This project deploys a production-style three-tier web application on Kubernetes, using Traefik as the Ingress controller, cert-manager for automated TLS certificate management, and MetalLB to provide LoadBalancer functionality in a bare-metal environment. External HTTPS traffic enters the cluster via a MetalLB-assigned IP and is terminated at Traefik, which performs host-based routing using IngressRoute CRDs and forwards requests to internal ClusterIP services. The frontend tier handles user interaction and communicates with the backend tier over the cluster network, while the backend implements business logic and accesses the database tier, which is isolated from external access and backed by persistent storage. TLS certificates are issued and renewed automatically by cert-manager and consumed by Traefik without downtime, resulting in a secure, cloud-agnostic, and scalable architecture that closely mirrors real-world production Kubernetes deployments.

## Features

Frontend: React/Vite application

Backend: Flask API with JWT authentication

Database: PostgreSQL StatefulSet with persistent storage

Ingress: Supports routing through Traefik

Dynamic configuration using values.yaml

## Prerequisites

Kubernetes cluster (e.g., MicroK8s, Minikube)

Helm 3 installed

Traefik ingress controller enabled

MetalLB for LoadBalancer support (MicroK8s)

## Helm Deployment

1. Deploy the application using the provided Helm chart:

```helm install student-marketplace ./helm-chart```

2. Upgrade deployment after changes:

```helm upgrade student-marketplace ./helm-chart```

3. Uninstall deployment:

```helm uninstall student-marketplace```
