# Proof of Concept: ArgoCD GitOps for AsciiArtify

## 1. Kubernetes Cluster Setup

We use **minikube** with the **Podman** driver as the recommended local Kubernetes environment.

```bash
podman machine init
podman machine start
minikube start --driver=podman
kubectl get nodes
```

---

## 2. Install ArgoCD
Create a dedicated namespace and install ArgoCD using the official manifests:
```bash

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get pods -n argocd
```

---

## 3. Access the ArgoCD Web UI

To access the ArgoCD UI locally, forward the service port:

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Open your browser and navigate to:

https://localhost:8080

---

### 4. Obtain the Initial Admin Password

The initial admin password is auto-generated and stored in a Kubernetes secret:

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

Use this password to log in with the username admin.

---

### Summary

This PoC demonstrates deployment of ArgoCD on a local Kubernetes cluster (minikube with Podman), enabling the AsciiArtify team to use a GitOps approach for continuous deployment.

---