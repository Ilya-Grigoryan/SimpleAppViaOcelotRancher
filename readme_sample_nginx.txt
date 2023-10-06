docker build -t ilyagrigoryan/sample-nginx-api-image .
docker push ilyagrigoryan/sample-nginx-api-image

kubectl apply -f sample-nginx-api-deployment.yaml;kubectl apply -f sample-nginx-api-service.yaml
kubectl create configmap sample-nginx-app-config --from-file=sample-nginx-app.conf;kubectl apply -f sample-nginx-deployment.yaml;kubectl apply -f sample-nginx-service.yaml



kubectl delete configmap sample-nginx-app-config