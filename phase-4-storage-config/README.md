# Phase 4 — Storage and Config

## The problem volumes solve
Pods are ephemeral — when they die, all data inside is lost.
PersistentVolumes keep data alive independently of pods.

## Storage objects

| Object | Role |
|--------|------|
| PersistentVolume (PV) | Actual storage on disk |
| PersistentVolumeClaim (PVC) | App's request for storage |
| StorageClass | How to create storage automatically |

K3s uses `local-path` StorageClass — automatically creates PVs on node disk.

## Proof of persistence
1. Write data to MongoDB pod
2. Delete the pod
3. Deployment recreates pod in ~1 second
4. Data is still there — stored on PVC, not inside the pod

## Key manifest sections
```yaml
volumeMounts:
- name: mongo-storage
  mountPath: /data/db     # where MongoDB stores data inside container

volumes:
- name: mongo-storage
  persistentVolumeClaim:
    claimName: mongodb-pvc  # connects pod to the PVC
```

## Commands
```bash
kubectl get pvc                    # see claims
kubectl get pv                     # see actual volumes
kubectl describe pvc mongodb-pvc   # full details
```
