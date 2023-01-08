# k8s-mongo
mongo express &amp; database hosted using k8s

## Prerequisites
- Hyperviser
- Local K8s setup: Using minikube.</p>
This project creates a mongodb pod which acts like mongodb database server.</p>
And mongo-express, database admin ui from where we can interact with database.

## Action Logs
**Create config for mongodb**:</p>
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
kubectl describe secret <NAME>

kubectl apply -f deployment.yaml
kubectl get deployment
kubectl get pod
kubectl describe pod / deployment <NAME>

kubectl apply -f service.yaml
kubectl get service
kubectl describe service <NAME>
```

This creates mongodb pod accessible within that k8s node cluster to other pods.

**Create config for mongo admin ui**
**Requirement**
Check docker repo for mongo-express for needs to connect.
This has many parameters but default would be DB Service name, username & password. Port we exposed is default and no need to set again.

**Create configMap**</P>
to store configuration fields like DB URL / service name.

**Create deployment**</P>
This is pod blbueprint.

**Create Service config**</P>
To expose this service outside pod, within K8s node cluster.

**Create Ingress config**</P>
To expose this service outside of k8s cluster to external world.

```console
kubectl apply -f configMap.yaml
kubectl get configMap
kubectl describe configMap <NAME>

kubectl apply -f deployment.yaml
kubectl get deployment
kubectl get pod
kubectl describe pod / deployment <NAME>

kubectl apply -f service.yaml
kubectl get service
kubectl describe service <NAME>


kubectl apply -f ingress.yaml
kubectl get ingress
kubectl describe ingress <NAME>
```

Now you can see that PORT binding is not happedned in services for mongo-express. This is how minikube works.
You need below command to start the service.

```console
minikube service list

minikube service <NAME>
```
