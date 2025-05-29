# Disclaimer

There are a lot of room for improvement. From the top of my head I can think of:

- Make ansible and workflow more dynamic so it's possible to deploy any version/color
    - Allow branch/tag as inputs in workflow for example
    - Verify if the color being deployed is the same as the live one
- Improve CI messages because it's too noisy
- Use secrets and not a public repo
- Specify only required permissions for service accounts
- Provide previous built docker images so it doesnt spend time installing tools
- Clean the linting messages/warnings


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
