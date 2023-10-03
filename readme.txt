docker build -t apigateway-jk8s-api-docker .
docker build -t sample-jk8s-api-docker .

kubectl apply -f sample-api-deployment.yaml;kubectl apply -f sample-api-service.yaml
kubectl apply -f gateway-deployment.yaml;kubectl apply -f gateway-service.yaml

docker image ls
kubectl get pods
kubectl get svc sample-api-service





delete all
kubectl delete deployments --all --all-namespaces
kubectl delete services --all --all-namespaces
kubectl delete pods --all --all-namespaces
kubectl delete configmaps --all --all-namespaces
kubectl delete secrets --all --all-namespaces
kubectl delete pvc --all --all-namespaces
kubectl delete namespaces --all --exclude=kube-system
