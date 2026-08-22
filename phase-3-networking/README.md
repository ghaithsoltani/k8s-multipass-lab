# Phase 3 — Networking

## Namespaces
Namespaces isolate resources inside the same cluster.
Cross-namespace DNS format: `service-name.namespace.svc.cluster.local`

```bash
kubectl create namespace dev
kubectl get all -n dev
kubectl delete namespace dev
```

## Service types

| Type | Access | Use case |
|------|--------|---------|
| ClusterIP | Inside cluster only | Pod-to-pod |
| NodePort | NodeIP:Port from outside | Dev/testing |
| LoadBalancer | Cloud LB IP | Production cloud |

## Ingress
One IP, many hostnames → different services.
K3s uses Traefik as the Ingress controller (pre-installed).

```bash
kubectl get ingress
kubectl describe ingress demo-ingress
```

Add hostnames to /etc/hosts for local testing:

## Key concepts
- Namespaces = folders for K8s resources
- ClusterIP = internal, NodePort = external port, Ingress = hostname routing
- Traefik handles all Ingress rules in K3s automatically
- Same cluster IP, different hostname → different app
