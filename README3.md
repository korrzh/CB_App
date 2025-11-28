**Luxembourg Population API – Kubernetes Deployment**

**1. Start Minikube Cluster**

```bash 
minikube start --driver=docker
```
Check

```bash 
kubectl get nodes
kubectl version
```

**2. Configure Docker to Use Minikube**
```bash 
minikube -p minikube docker-env | Invoke-Expression
```

Check

```bash
docker images 
```

**3. Build Docker Image for the API**
```bash 
docker build -t lupopulation-api .
```

**4. Deploy the Application**
```bash
kubectl create deployment lupopulation-api --image=lupopulation-api --replicas=2
kubectl apply -f deployment.yaml
```
Check deployment and pods:
```bash
kubectl get deployments
kubectl get pods
```

**5. Access the REST API**
Use Minikube to open the service in a browser:
```bash
minikube service lupopulation-service
```
Test the API endpoint:
```bash
http://127.0.0.1:XXXXX/api/population/2024
```
