# Phase 1 — Foundation

## What we built
A 2-node Kubernetes cluster running on local Ubuntu VMs using Multipass + K3s.

## Cluster info
- Master node: k8s-master (10.245.99.83) — control-plane
- Worker node: k8s-worker1 — runs your workloads
- K8s version: v1.36.3+k3s1

## Commands used

```bash
# Launch VMs
multipass launch --name k8s-master  --cpus 2 --memory 2G --disk 10G
multipass launch --name k8s-worker1 --cpus 2 --memory 2G --disk 10G

# Install K3s on master
multipass shell k8s-master
curl -sfL https://get.k3s.io | sh -

# Join worker
multipass exec k8s-worker1 -- bash -c "curl -sfL https://get.k3s.io | \
  K3S_URL=https://MASTER_IP:6443 \
  K3S_TOKEN=YOUR_TOKEN sh -"

# Configure kubectl on host
multipass exec k8s-master -- sudo cat /etc/rancher/k3s/k3s.yaml > ~/.kube/config
sed -i "s/127.0.0.1/MASTER_IP/" ~/.kube/config

# Verify
kubectl get nodes
```

## Key concepts learned
- Kubernetes needs a control-plane (master) and worker nodes
- K3s is lightweight K8s — same API, less overhead, perfect for local dev
- kubectl talks to the cluster via kubeconfig (~/.kube/config)
- Multipass gives real Ubuntu VMs, not containers or emulation
