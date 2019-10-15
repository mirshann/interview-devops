# Kubernetes deployment

For deployment configure your kubernetes cluster, then go to deployment process

```
kubectl apply -f src/kubernetes/backend_production.yaml
kubectl apply -f src/kubernetes/backend_service.yaml
```

then wait wile backend service achive public IP.
```
kubectl get svc
```

Use public IP of backend service to fix env in "src/kubernetes/frontend.yaml", and then proceed with frontend deployment

```
kubectl apply -f src/kubernetes/frontend.yaml
```

Then you can access your deployment

## Upgrade

Just apply "backend_canary.yaml" and it will deploy pod with backend.v2 and than destroy backend.v1 without down the service
```
kubectl apply -f src/kubernetes/backend_canary.yaml
```