# Phase 5 — Helm

## What Helm does
Package manager for Kubernetes. One chart deploys a full application.

## Key concepts

| Term | Meaning |
|------|---------|
| Chart | Package of K8s YAML templates |
| Release | A deployed instance of a chart |
| Values | Variables that customize the chart |
| Repository | Collection of charts (like apt sources) |

## Commands
```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm search repo bitnami/mongodb
helm install my-mongo bitnami/mongodb --values values.yaml
helm list
helm history my-mongo
helm upgrade my-mongo bitnami/mongodb --values values.yaml
helm rollback my-mongo 1
helm uninstall my-mongo
```

## Why Helm over raw YAML
- One values file controls everything
- Upgrade and rollback with one command
- Community charts for every major app
- Revision history built in
