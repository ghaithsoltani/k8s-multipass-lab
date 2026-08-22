# Phase 2 — Core Skills

## Key kubectl commands

```bash
# Get resources
kubectl get pods
kubectl get pods -o wide          # shows which node each pod is on
kubectl get pods -w               # watch in real time
kubectl get all                   # pods + services + deployments
kubectl get all --all-namespaces  # everything in the cluster

# Inspect
kubectl describe pod POD_NAME     # full details + events
kubectl logs POD_NAME             # container logs
kubectl exec -it POD_NAME -- bash # shell inside the container

# Apply / delete
kubectl apply -f file.yaml        # create or update
kubectl delete -f file.yaml       # delete everything in the file
kubectl delete pod POD_NAME       # delete one pod

# Scale
kubectl scale deployment NAME --replicas=4

# Port forward (for local testing)
kubectl port-forward service/NAME 8080:80
```

## YAML structure — every manifest has 4 sections

```yaml
apiVersion: apps/v1   # which K8s API handles this
kind: Deployment      # what type of resource
metadata:             # name, labels
  name: my-app
spec:                 # desired state — what you want
  replicas: 2
  ...
```

## What we learned
- Pods land on worker nodes automatically (scheduler decides)
- Deployment manages pods — if one dies, it restarts it
- Service gives pods a stable IP and DNS name
- ClusterIP = internal only, not reachable from outside
- Scale up/down with one command, no downtime
