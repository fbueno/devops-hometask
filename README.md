# DevOps Home Task – Blue/Green Runbook (Starter)

| dir / file | purpose |
|------------|---------|
| `k8s/` | Base v1 (blue) Deployment + Service. |
| `ansible/playbook.yml` | Empty playbook – candidate writes tasks to spin up **green** Deployment and patch the Service. |
| `argo/workflow-skeleton.yaml` | Bare-bones workflow – candidate wires steps, rollback, masking, etc. |
| `.github/workflows/ci.yml` | Self-test pipeline (kind + Argo) – will go green only after the task is solved. |

## Quick start

```bash
# local smoke-test
kind create cluster --name argo-task
kubectl apply -f k8s/           # deploy v1
argo submit argo/workflow-skeleton.yaml -n argo   # once workflow implemented
```
