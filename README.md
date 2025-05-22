### Overview

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
      - [The Kubernets command line tool kubectl](The-Kubernets-command-line-tool-kubectl)
        - [Kubernetes installation and configuration](Kubernetes-installation-and-configuration)
        - [Kubernetes setup](kubernetes-setup)
        - [kubectl download](kubectl-download)
      - [Python 3.X is installed] (python-install) 
  - [Pulumi and Kubernetes Create Project](Pulumi-and-Kubernetes-Create-Project)
  - [Create Infrastructure with Pulumi Deployments](Create-Infrastructure-with-Pulumi-Deployments)
  - [Create Organization](Create-Organization)
  - [Create Stack](Create-Stack)
  - [Start Deployment](Start-Deployment)
    
## What is Pulumi?

Pulumi is an open source infrastructure-as-code tool for creating, deploying, and managing cloud infrastructure in the programming language of your choice. If you are new to Pulumi, please consider visiting the [getting started](https://www.pulumi.com/docs/get-started/) first to familiarize yourself with Pulumi and concepts such as [Pulumi stacks](https://www.pulumi.com/docs/intro/concepts/stack/) and [backends](https://www.pulumi.com/docs/intro/concepts/state/).

## Creating Resources on Kubernetes

In Pulumi, resources represent the fundamental units that make up your infrastructure, such as virtual machines, networks, storage and databases. A resource is used to define and manage an infrastructure object in your Pulumi configuration. (https://www.pulumi.com/tutorials/creating-resources-kubernetes/). In this repo, resources has been created and hosted on simple Nginx server hosted Kubernets and further deployed to make Nginx deployment accessible. 

## Prerequisites

The following steps should be completed before start using Kubernetes:

# Pulumi CLI

Download and install Pulumi (https://www.pulumi.com/docs/iac/download-install/)
brew install pulumi/tap/pulumi 

# Pulumi Cloud account
Create login on (https://app.pulumi.com/) and navigate to app.pulumi.com. 
GitHub identity used as to sign up. 

# Run Minikube Cluster
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

# Kubernetes-installation-and-configuration
Your Pulumi program is required to import the pulumi/kubernetes provider package to allow the Pulumi CLI to authenticate and interact with a running Kubernetes cluster.

By default, Pulumi will use a local kubeconfig if available, or one can be passed as a provider argument in the request.
Installation
The Kubernetes provider is available as a package in all Pulumi languages:
Python: pulumi-kubernetes

# Set-up
By default, Pulumi will look for a kubeconfig file in the following locations, just like kubectl:

The environment variable: $KUBECONFIG,
Or in current user’s default kubeconfig directory: ~/.kube/config
If the kubeconfig file is not in either of these locations, Pulumi will not find it, and it will fail to authenticate against the cluster. Set one of these locations to a valid kubeconfig file, if you have not done so already.

Verify the cluster is configured and up by running kubectl get pods.
## Python 3.X is installed
## Create Infrastructure with Pulumi Deployments
Pulumi deployments is a fully managed service designed to automate the infrastruture. It provides the building blocks designed for scaling cloud ifra with tools to power public and private cloud platforms, APIs and self service infra portals. Deployment can be triggered through multiple methods
1. REST API
2. Integrating with github (Push to deploy)
3. Initiate from Pulumi cloud console.

# Create Organization
Organizations are a space to collaborate on shared project and stacks.
Select the create an organization and provide it with the name.
You can join an organization or can invite members to join an organization.
You can switch between organization.

# Create Stack
Every Pulumi program is deployed to stack. A stack is an isolated, independent and configurable instance of pulumi program.
A project can have as many stack you need. 
`keshakumar@Keshas-Laptop iac_project_1 % pulumi stack init iac_project_1-dev
Created stack 'iac_project_1-dev'
` 
If you get the error 
`Error:
Diagnostics:
  pulumi:pulumi:Stack (iac_project_1-iac_project_1-dev):
    error: update failed
  kubernetes:core/v1:Namespace (webserver):
    error: configured Kubernetes cluster is unreachable: unable to load Kubernetes client configuration from kubeconfig file. Make sure you have:
    
  set up the provider as per https://www.pulumi.com/registry/packages/kubernetes/installation-configuration/
  invalid configuration: no configuration has been provided, try setting KUBERNETES_MASTER environment variable

Before you begin: You need to have a Kubernetes cluster, and the kubectl command-line tool must be configured to communicate with your cluster`

2. Start the kubernetes
   minikube start
3. Set the minikube context
keshakumar@Keshas-Laptop iac_project_1 % kubectl config get-contexts
keshakumar@Keshas-Laptop iac_project_1 % export KUBECONFIG=~/.kube/config

4. Stack clean up
To Release the resources taken by “pulumi destroy”
To delete the stack “pulumi stack rm $stack_name”

# Start Deployment
with github integration. After Pulumi github integration
`pulumi org set-default sprasad_github_integration`

Stack → settings → deploy → git 




