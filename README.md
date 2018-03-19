# Kubernetes for Developers

## Prerequisites

This is an interactive tutorial; you will need a Minikube cluster running locally with the heapster addon enabled.

1. [Install Minikube](https://github.com/kubernetes/minikube#installation)
1. [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl)
1. `minikube start`
1. `minikube addons enable heapster`

You will also need the metrics API installed if it is not already:
https://kubernetes.io/docs/tasks/debug-application-cluster/core-metrics-pipeline/

When you're done, run `minikube stop`.

## Table of Contents

1. [Create a Pod](chapters/1-create-a-pod)
1. [Serve HTTP Traffic](chapters/2-serve-http-traffic)
1. [Expose to External Traffic](chapters/3-expose-to-external-traffic)
1. [Ensure High Availability](chapters/4-ensure-high-availability)
1. [Manage Deployments](chapters/5-manage-deployments)
1. [Autoscale Deployment](chapters/6-autoscale-deployment)
1. [Manage Container Configuration](chapters/7-manage-container-configuration)
