## Overview

A Pulumi's Cloud Native Python SDK Project to target any Kuberenets environment to provision a cluster , configure and deploy applications, and update them as required.
To learn more about the Pulumi Kuberenets visit the [Pulumi documentation][https://www.pulumi.com/docs/iac/get-started/kubernetes/).

- [Pulumi Kubernetes SDK]
  - [Overview](#overview)
    - [What is Pulumi?](#what-is-pulumi)
    - [Creating Resources on Pulumi Kubernetes?](#creating-resources-on-kubernetes)
    - [Prerequisites](#prerequisites)
      - [Pulumi CLI](pulumi-cli)
      - [Pulumi Cloud Account](pulumi-cloud-account)
      - [Run Minikube Cluster](run-minikube-cluster)
        - [minikube download](minikube-download)
      - [The Kubernets command line tool kubectl](kubernetes-command-line-tool)
        - [kubectl download](kubectl-download)
      - [Python 3.X is installed] (python-install) 
  - [Deploy the Operator](#deploy-the-operator)
    - [Using Helm](#using-helm)
    - [Using Pulumi](#using-pulumi)
    - [Dev Install](#dev-install)
    - [From Source](#from-source)
  - [Create Pulumi Stack Resources](#create-pulumi-stack-resources)
    - [Examples](#examples)
  - [Stack CR Documentation](#stack-cr-documentation)
  - [Prometheus Metrics Integration](#prometheus-metrics-integration)
  - [Development](#development)

### What is Pulumi?

Pulumi is an open source infrastructure-as-code tool for creating, deploying, and managing cloud infrastructure in the programming language of your choice. If you are new to Pulumi, please consider visiting the [getting started](https://www.pulumi.com/docs/get-started/) first to familiarize yourself with Pulumi and concepts such as [Pulumi stacks](https://www.pulumi.com/docs/intro/concepts/stack/) and [backends](https://www.pulumi.com/docs/intro/concepts/state/).

### Creating Resources on Kubernetes

In Pulumi, resources represent the fundamental units that make up your infrastructure, such as virtual machines, networks, storage and databases. A resource is used to define and manage an infrastructure object in your Pulumi configuration. (https://www.pulumi.com/tutorials/creating-resources-kubernetes/). In this repo, resources has been created and hosted on simple Nginx server hosted Kubernets and further deployed to make Nginx deployment accessible. 

### Prerequisites

The following steps should be completed before start using Kubernetes:

## Pulumi CLI

Download and install Pulumi (https://www.pulumi.com/docs/iac/download-install/)

## Pulumi Cloud account
Create login on (https://app.pulumi.com/) and navigate to app.pulumi.com. 
GitHub identity used as to sign up. 

## Run Minikube Cluster
minikube is local Kubernets, focusing on making it easy to learn and develop for Kubernetes.
Docker container environment is used to start ```minikube start```

# minikube download
To configure and Install minikube
(https://minikube.sigs.k8s.io/docs/start/?arch=%2Fmacos%2Farm64%2Fstable%2Fbinary+download)

On successful installation
Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default

## The Kubernets command line tool kubectl
# kubetctl download
To configure and install kubectl
(https://kubernetes.io/docs/tasks/tools/)

## Python 3.X is installed


### From Source

To build and install the operator from this repository:

1. Build the operator image: `make build-image` (produces `pulumi/pulumi-kubernetes-operator:v2.0.0`).
2. Push or load the image into your cluster's registry.
3. Deploy to your current cluster context: `make deploy`.

This approach deploys a Kustomization directory located at `./operator/config/default`.

## Create Pulumi Stack Resources

The following are examples to create Pulumi Stacks in Kubernetes that are managed and run by the operator.

Some of the examples use Pulumi Cloud as a state backend, and require that a Pulumi access token
be stored into a Kubernetes Secret. For example, here's now to create a secret from your `PULUMI_ACCESS_TOKEN` environment variable.

```bash
kubectl create secret generic -n default pulumi-api-secret --from-literal=accessToken=$PULUMI_ACCESS_TOKEN
```

### Examples

Working with sources:

- [Git repositories](./examples/git-source)
- [Flux sources](./examples/flux-source)
- [Program resources](./examples/program-source)
- [Custom sources](./examples/custom-source)

Better together with Pulumi IAC:

- [Pulumi (TypeScript)](./examples/pulumi-ts)

Advanced configurations:

- [Workspace customization](./examples/custom-workspace)

## Stack CR Documentation

Detailed documentation on Stack Custom Resource is available [here](./docs/stacks.md).

## Prometheus Metrics Integration

Details on metrics emitted by the Pulumi Kubernetes Operator as instructions on getting them to flow to Prometheus are available [here](./docs/metrics.md).
