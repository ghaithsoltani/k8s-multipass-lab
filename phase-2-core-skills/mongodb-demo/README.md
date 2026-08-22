# Demo — MongoDB + Mongo Express

## Architecture

## Files

| File | Purpose |
|------|---------|
| mongo-secret.yaml | base64-encoded DB credentials |
| mongo-configmap.yaml | database URL (mongodb-service) |
| mongo-deployment.yaml | MongoDB pod + ClusterIP service |
| mongoexpress-deployment.yaml | Mongo Express pod + NodePort service |

## Deploy order (order matters)

```bash
kubectl apply -f mongo-secret.yaml
kubectl apply -f mongo-configmap.yaml
kubectl apply -f mongo-deployment.yaml
# wait for MongoDB Running
kubectl apply -f mongoexpress-deployment.yaml
```

## Access

```bash
# Get node IP
multipass list

# Open in browser
http://NODE_IP:30432
```

## Key concepts
- Secret → stores sensitive data as base64, injected as env vars
- ConfigMap → stores non-sensitive config, injected as env vars
- ClusterIP → internal only, pods talk to each other via service name
- NodePort → opens a port on every node, reachable from outside
- K8s DNS resolves service names automatically inside the cluster
