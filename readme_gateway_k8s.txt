docker build -t ilyagrigoryan/gateway-jk8s-api-image .
docker push ilyagrigoryan/gateway-jk8s-api-image

kubectl apply -f gateway-jk8s-api-deployment.yaml;kubectl apply -f gateway-jk8s-api-service.yaml