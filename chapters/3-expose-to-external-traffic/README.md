# Expose to External Traffic

A Kubernetes Service is an abstraction which defines a logical set of Pods and a policy by which to access them - sometimes called a micro-service.

In this example we will create a Service to route traffic to the Pod running our application.

## Instructions

#### Create Pod and Service:

Note: 

```bash
kubectl create -f resources
```

#### Visit the service URL:

```bash
minikube service myapp-svc --url
```

#### Remove resources:
```bash
kubectl delete -f resources
```

## References

https://kubernetes.io/docs/concepts/services-networking/service
