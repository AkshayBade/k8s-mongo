# k8s-mongo
mongo express &amp; database hosted using k8s

## Prerequisites
- Hyperviser
- Local K8s setup: Using minikube.</p>
This project creates a mongodb pod which acts like mongodb database server.</p>
And mongo-express, database admin ui from where we can interact with database.

## Action Logs
**Create deployment config for mongodb**:</p>
**Requirements**:</p>
Check docker repo of mongo for what it needs to host inside container.</p>
This needs username & password to connect and can be default if not provided(default not recommended).</p>
This also needs TCP port to be exposed.</p>

**Create secrets config**: </p>
to store secret configurations like username & password.</p>

**Create Deployment config**:</p>
This config is used to create pods.</p>
Please check file for more field level details.</p>

**Create Service config**:</p>
This config links service component with pod. Which helps as internal LB & provides fixed vertual URL even when pod replicas restart.

```console
kubectl apply -f secret.yaml
kubectl get secret
kubectl describe secret

kubectl apply -f deployment.yaml
kubectl get deployment
kubectl get pod
kubectl describe pod / deployment

kubectl apply -f service.yaml
kubectl get service
kubectl describe service
```

This creates mongodb pod accessible within that k8s node cluster to other pods.

