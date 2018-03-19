# Enable Horizontal Autoscaling

A Horizontal Pod Autoscaler automatically scales the number of pods in a Deployment based on observed CPU utilization.

In order to use HorizontalPodAutoscaler resources, you must define compute resource limits for your 

## Instructions

#### Create Deployment, Service, and HorizontalPodAutoscaler:

```bash
kubectl create -f resources
```

#### Apply load:

The below command will deploy a Pod to apply load to the `myapp-svc` Service. Note that we are using [Kubernetes DNS](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/) to reach the service.
```bash
kubectl run myapp-load-generator --image=busybox --limits cpu=800m,memory=128Mi --command -- sh -c "while true; do wget -q -O- http://myapp-svc.default.svc.cluster.local; done"
```

Observe your number of replicas scale up:
```bash
kubectl get hpa --watch
```

#### Remove resources:
```bash
kubectl delete deployment myapp-load-generator
kubectl delete -f resources
```

## References

https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale

https://kubernetes.io/docs/concepts/configuration/manage-compute-resources-container

https://kubernetes.io/docs/concepts/services-networking/dns-pod-service
