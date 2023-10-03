# Coffeeshop infrastructure

## Quest requirmenet

- 3 public ECR repositories
- FIS
  - Log group: FIScoffeeshop
  - IAM role: AWSFISIAMRole-coffeeshop
  - FIS experiment to delete pods

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
