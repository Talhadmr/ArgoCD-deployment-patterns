# ArgoCD Patterns and Best Practices

Welcome to the ArgoCD Patterns repository. This project demonstrates different architectural approaches to managing Kubernetes applications using ArgoCD.

The repository is structured into specific branches, each dedicated to a distinct ArgoCD management pattern. Please adhere to the branch guide below to locate the configuration that suits your needs.

## 🔀 Branch Guide

We utilize a branch-based strategy to separate different implementation patterns.

### 1. App of Apps Pattern
* **Branch:** [`app-of-apps`](#)
* **Description:**
    Switch to this branch to explore the **App of Apps** pattern. In this structure, a single "Root Application" is responsible for managing other Applications (children).
    * Ideal for managing a cluster bootstrapping process.
    * Demonstrates how to hierarchically structure manifests.
    * Includes the `root-app.yaml` and the directory structure for child apps.

### 2. ApplicationSet Pattern
* **Branch:** [`applicationset`](#)
* **Description:**
    Switch to this branch to see the **ApplicationSet** controller implementation. This pattern automates the generation of ArgoCD Applications based on specific generators (List, Git, Cluster, etc.).
    * Ideal for multi-cluster deployments or monorepos with uniform directory structures.
    * Demonstrates how to dynamically generate applications without defining them manually one by one.

---

## 🚀 Getting Started

To use the configurations provided in this repository, you must clone the repo and checkout the specific branch you wish to deploy.

### Prerequisites
* A running Kubernetes Cluster.
* ArgoCD installed and running in the `argocd` namespace.
* `kubectl` command-line tool configured.

### Deployment Instructions

#### Option A: Deploying the App of Apps
1.  Switch to the relevant branch:
    ```bash
    git checkout app-of-apps
    ```
2.  Review the root application manifest and apply it:
    ```bash
    # Apply the root app to bootstrap the cluster
    kubectl apply -f root-app.yaml -n argocd
    ```

#### Option B: Deploying the ApplicationSet
1.  Switch to the relevant branch:
    ```bash
    git checkout applicationset
    ```
2.  Apply the ApplicationSet manifest:
    ```bash
    # Ensure the ApplicationSet controller is running, then apply:
    kubectl apply -f applicationset.yaml -n argocd
    ```

---
