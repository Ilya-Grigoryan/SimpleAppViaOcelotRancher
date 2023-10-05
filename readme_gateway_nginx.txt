docker build -t ilyagrigoryan/gateway-nginx-api-image .
docker push ilyagrigoryan/gateway-nginx-api-image

kubectl apply -f gateway-nginx-api-deployment.yaml;kubectl apply -f gateway-nginx-api-service.yaml
kubectl create configmap gateway-nginx-app-config --from-file=gateway-nginx-app.conf;kubectl apply -f gateway-nginx-service.yaml

kubectl expose service gateway-nginx-service --type=NodePort --name=gateway-nginx-nodeport





kubectl exec -it gateway-nginx-api-deployment-768998cf59-ct8h9 -c gateway-nginx-api-container -- /bin/bash
kubectl logs -f gateway-nginx-api-deployment-768998cf59-ct8h9 -c gateway-nginx-api-container
kubectl port-forward gateway-nginx-api-deployment-768998cf59-ct8h9 8082:80