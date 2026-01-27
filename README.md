# Kubernetes

# Kubernetes Basics – Tutorial Walkthrough (Script Style)

Dieses README folgt dem offiziellen Kubernetes Basics Tutorial:
https://kubernetes.io/docs/tutorials/kubernetes-basics/

Alle Schritte sind in der Reihenfolge des Tutorials aufgebaut.
Erklärungen stehen als Kommentare, Befehle sind korrekt als bash formatiert.

---

## 1. Cluster & kubectl überprüfen

```
# Prüfen der kubectl Client- und Server-Version
kubectl version

# Anzeigen aller Nodes im Cluster
kubectl get nodes
```

## 2. Deployment erstellen
```
# Erstellen eines Deployments mit dem Beispiel-Container
kubectl create deployment kubernetes-bootcamp \
  --image=gcr.io/google-samples/kubernetes-bootcamp:v1

# Anzeigen aller Deployments
kubectl get deployments

# Anzeigen der durch das Deployment erzeugten Pods
kubectl get pods

```

## 3. Cluster & Anwendung erkunden
```
# Starten eines lokalen Proxys zur Kubernetes API
kubectl proxy

# (In einem zweiten Terminal)
# Abfrage der Kubernetes API-Version über den Proxy
curl http://localhost:8001/version
```


## 4. Anwendung über einen Service verfügbar machen
```
# Exponieren des Deployments als Service
kubectl expose deployment kubernetes-bootcamp \
  --type=LoadBalancer \
  --port=8080

# Anzeigen aller Services
kubectl get services

# (Optional)
# Anzeigen aller Ressourcen im Namespace
kubectl get all
```

### 5. Deployment skalieren
```
# Skalieren des Deployments auf 3 Replikas
kubectl scale deployment kubernetes-bootcamp --replicas=3

# Überprüfen der laufenden Pods
kubectl get pods
```

### 6. Deployment aktualisieren (Rolling Update)
```
# Aktualisieren des Container-Images auf Version v2
kubectl set image deployment/kubernetes-bootcamp \
  kubernetes-bootcamp=gcr.io/google-samples/kubernetes-bootcamp:v2

# Überprüfen der Pods nach dem Rolling Update
kubectl get pods
```

7. Aufräumen der Ressourcen
```
# Löschen des Deployments (inkl. Pods)
kubectl delete deployment kubernetes-bootcamp

# Löschen des Services
kubectl delete service kubernetes-bootcamp

```

### 8. (Optional) Namespace-übergreifende Übersicht
```
# Anzeigen aller Pods in allen Namespaces
kubectl get pods --all-namespaces

# Anzeigen aller Deployments in allen Namespaces
kubectl get deployments --all-namespaces
```