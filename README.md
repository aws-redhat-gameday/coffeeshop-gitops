# Coffeeshop infrastructure

## Pre-requisites

- ROSA cluster
- OpenShift GitOps operator
- OpenShift AMQ operator

### Deployment

Install the ArgoCD application to deploy the coffeeshop app and its dependencies (Kafka)

```bash
oc apply -f argocd/application.yaml
```

### Cleanup

```bash
oc delete -f argocd/application.yaml
```
