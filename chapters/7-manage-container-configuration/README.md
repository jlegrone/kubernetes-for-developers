# Configure Container Image

ConfigMaps allow you to decouple configuration artifacts from image content to keep containerized applications portable.

In this example we will define a Pod capable of serving HTTP traffic using the `node:alpine` image by mounting the source code for our application as a ConfigMap.

## Instructions

#### Create Deployment, Service, and ConfigMap:
```bash
kubectl create -f resources
```

Visit the service URL:
```bash
minikube service myapp-svc --url
```

#### Remove resources:
```bash
kubectl delete -f resources
```

## References

https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap

https://kubernetes.io/docs/tasks/inject-data-application/define-environment-variable-container
