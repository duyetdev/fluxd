# flux-get-started

[![CircleCI](https://circleci.com/gh/fluxcd/flux-get-started.svg?style=svg)](https://circleci.com/gh/fluxcd/flux-get-started)

We published a step-by-step run-through on how to use Flux and Helm Operator [over
here](https://github.com/fluxcd/flux/blob/master/docs/tutorials/get-started-helm.md).

## Getting started
https://docs.fluxcd.io/en/latest/tutorials/get-started/


Add the Flux repository:
```
helm repo add fluxcd https://charts.fluxcd.io
```

Apply the Helm Release CRD:
```
kubectl apply -f setup/crds.yaml
```

Create the flux namespace:

```
kubectl create ns flux
```

Install Flux and HelmOperator
```
kubectl apply -f setup/flux-ssh-secret.yaml
helm upgrade -i flux --namespace flux -f setup/flux-dev-values.yaml fluxcd/flux
helm upgrade -i helm-operator --namespace flux -f setup/helm-operator-dev-values.yaml fluxcd/helm-operator
```
