docker build -t ilyagrigoryan/sample-jk8s-api-image .
docker push ilyagrigoryan/sample-jk8s-api-image

kubectl apply -f sample-jk8s-api-deployment.yaml;kubectl apply -f sample-jk8s-api-service.yaml