# Traefik Hub Helm Chart

## Introduction

This chart installs the Hub agent in a Kubernetes cluster.
The agent consists of two deployments: a controller and multiple authentication servers.

## Installation

### Prerequisites

1. [x] Helm **v3** [installed](https://helm.sh/docs/using_helm/#installing-helm): `helm version`
2. [x] Traefik's chart repository: `helm repo add traefik https://traefik.github.io/charts`

### Deploying Hub Agent for Kubernetes

```bash
helm install hub-agent traefik/hub-agent
```

You can customize the install with a `values` file. There are some [EXAMPLES](./EXAMPLES.md) provided.
Complete documentation on all parameters is in the [default file](./hub-agent/values.yaml)

## Upgrading Hub Agent for Kubernetes

One can check what has changed in the [Releases](https://github.com/traefik/hub-helm-chart/releases).

```bash
# Update repository
helm repo update
# See current Chart & Hub Agent version
helm search repo traefik/hub-agent
# Upgrade Hub Agent
helm upgrade hub-agent traefik/hub-agent
```

### Upgrading CRDs

With Helm v3, CRDs created by this chart can not be updated, cf the [Helm Documentation on CRDs](https://helm.sh/docs/chart_best_practices/custom_resource_definitions). Please read carefully release notes of this chart before upgrading CRDs.

```bash
kubectl apply --server-side --force-conflicts -k https://github.com/traefik/hub-helm-chart/hub-agent/crds/
```

## Uninstall

```bash
helm uninstall hub-agent
```

If hub-agent was installed in a specific namespace

```bash
helm uninstall hub-agent --namespace hub-namespace
```

## Contributing 

### Launch unit tests

```bash
make test
```
