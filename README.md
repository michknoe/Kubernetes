
# Kubernetes

## Kubernetes Basics – Tutorial Walkthrough

This README follows the official Kubernetes Basics Tutorial:
https://kubernetes.io/docs/tutorials/kubernetes-basics/

All steps are structured in the order of the tutorial.

---


## 1. Check Cluster & kubectl

```
# Check the kubectl client and server version
kubectl version

# Show all nodes in the cluster
kubectl get nodes
```


## 2. Create a Deployment
```
# Create a deployment with the sample container
kubectl create deployment kubernetes-bootcamp \
  --image=gcr.io/google-samples/kubernetes-bootcamp:v1

# Show all deployments
kubectl get deployments

# Show the pods created by the deployment
kubectl get pods
```


## 3. Explore Cluster & Application
```
# Start a local proxy to the Kubernetes API
kubectl proxy

# (In a second terminal)
# Query the Kubernetes API version via the proxy
curl http://localhost:8001/version
```



## 4. Expose Application via a Service
```
# Expose the deployment as a service
kubectl expose deployment kubernetes-bootcamp \
  --type=LoadBalancer \
  --port=8080

# Show all services
kubectl get services

# (Optional)
# Show all resources in the namespace
kubectl get all
```


### 5. Scale the Deployment
```
# Scale the deployment to 3 replicas
kubectl scale deployment kubernetes-bootcamp --replicas=3

# Check the running pods
kubectl get pods
```


### 6. Update the Deployment (Rolling Update)
```
# Update the container image to version v2
kubectl set image deployment/kubernetes-bootcamp \
  kubernetes-bootcamp=gcr.io/google-samples/kubernetes-bootcamp:v2

# Check the pods after the rolling update
kubectl get pods
```


7. Clean Up Resources
```
# Delete the deployment (including pods)
kubectl delete deployment kubernetes-bootcamp

# Delete the service
kubectl delete service kubernetes-bootcamp
```


### 8. (Optional) Cross-Namespace Overview
```
# Show all pods in all namespaces
kubectl get pods --all-namespaces

# Show all deployments in all namespaces
kubectl get deployments --all-namespaces
```