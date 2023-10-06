# Coffeeshop infrastructure

## Pre-requisites

- ROSA cluster
- OpenShift GitOps operator
- OpenShift AMQ operator

### Build

This phase uses an Argo CD application to create build pipelines (Tekton pipelines).

The pipelines build the container images required for the `barista-node` and `coffeeshop-service` services and push them into the OpenShift internal registry.

The pipelines get created in a project namespace named `coffeeshop-build`.

```bash
oc apply build/argocd/application.yaml
```

Run the Tekton pipelines:

```bash
oc apply -f build/tekton/pipelinerun
```

### Deployment

Install the Argo CD application to deploy the `barista-node` and `coffeeshop-service` services and their dependencies (Kafka)

Once the build phase is completed, run:

```bash
oc apply -f deploy/argocd/application.yaml
```

The services get deployed in a project namespace named `coffeeshop-deploy`.

### Cleanup

```bash
oc delete -f build/argocd/application.yaml
oc delete -f deploy/argocd/application.yaml
```
