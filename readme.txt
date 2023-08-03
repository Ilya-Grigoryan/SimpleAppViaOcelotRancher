docker build -t apigateway-api-docker .
docker build -t sample-api-docker .

docker image ls

kubectl apply -f .\SampleApi\sample-api-deployment.yaml

kubectl get pods

kubectl apply -f .\SampleApi\sample-api-service.yaml

kubectl get svc sample-api-service





delete all
kubectl delete deployments --all --all-namespaces
kubectl delete services --all --all-namespaces
kubectl delete pods --all --all-namespaces
kubectl delete configmaps --all --all-namespaces
kubectl delete secrets --all --all-namespaces
kubectl delete pvc --all --all-namespaces
kubectl delete namespaces --all --exclude=kube-system
