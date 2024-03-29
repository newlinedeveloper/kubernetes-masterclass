#### Fullstack Golang application - k8s deployment

```
cd k8s

kubectl apply -f deployments.yml

kubectl get pods

kubectl apply -f services.yml

kubectl get svc


kubectl port-forward service/frontend-service 3000:3000

kubectl port-forward service/backend-service 8000:8000

```
