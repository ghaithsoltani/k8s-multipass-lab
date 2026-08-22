# Kubernetes Learning Lab — Multipass Edition

A hands-on Kubernetes project built entirely on local Ubuntu VMs.
No cloud provider. No shortcuts.

## What's inside

| Phase | Topic | Key skills |
|-------|-------|-----------|
| phase-1-foundation | Cluster setup | Multipass, K3s, kubeconfig |
| phase-2-core-skills | Core K8s | kubectl, YAML, MongoDB demo |
| phase-3-networking | Networking | Namespaces, Services, Ingress |
| phase-4-storage-config | Storage | PVC, ConfigMap, Secret, StatefulSet |
| phase-5-advanced-tools | Advanced | Helm, RBAC, Operators |
| phase-6-production | Production | Microservices, Helm chart, Helmfile |

## Stack
- **Runtime**: Multipass VMs (Ubuntu 26.04) + K3s v1.36
- **Tools**: kubectl, Helm v3, Helmfile, Traefik Ingress
- **Apps**: MongoDB, Mongo Express, custom microservices
- **Storage**: local-path StorageClass with PersistentVolumes

## Highlights
- 2-node cluster (control-plane + worker) on local VMs
- Full microservices app deployed 2 ways: raw YAML and Helm chart
- Helmfile managing multiple releases across namespaces
- RBAC with Roles, ClusterRoles, and ServiceAccounts
- StatefulSet with ordered pod startup and per-pod PVCs
- Ingress hostname routing (frontend.local, api.local)

## Quick start
```bash
# Spin up the cluster
bash scripts/setup-cluster.sh

# Deploy microservices with Helm
helm install microservices-app phase-6-production/microservices-chart

# Or deploy everything with Helmfile
cd phase-6-production && helmfile apply
```
