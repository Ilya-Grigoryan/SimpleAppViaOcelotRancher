#publish to iis
dotnet publish --configuration Release --framework net7.0 --runtime win-x64 --output C:\inetpub\SimpleApp\GateWay
dotnet publish --configuration Release --framework net7.0 --runtime win-x64 --output C:\inetpub\SimpleApp\SampleApi
also need to change DownstreamHostAndPorts in ocelot.json

docker build -t apigateway-api-docker .
docker build -t sample-api-docker .

docker image ls

kubectl apply -f sample-api-deployment.yaml;kubectl apply -f sample-api-service.yaml;
#nginx
kubectl apply -f nginx-sample-deployment.yaml
kubectl create configmap nginx-sample-app-config --from-file=nginx-sample-app.conf;kubectl apply -f nginx-sample-service.yaml
#expose nginx
kubectl expose service nginx-sample-app-service --type=NodePort --name=nginx-sample-nodeport;

kubectl apply -f gateway-deployment.yaml;kubectl apply -f gateway-service.yaml;
#expose gateway
kubectl port-forward pod/apigateway-api-deployment-5f77487cf6-tqw8q 8080:80 
kubectl expose service apigateway-api-service --type=NodePort --name=apigateway-api-nodeport;
#nginx
kubectl apply -f nginx-gateway-deployment.yaml
kubectl create configmap nginx-gateway-app-config --from-file=nginx-gateway-app.conf;kubectl apply -f nginx-gateway-service.yaml
#expose nginx
kubectl expose service nginx-gateway-app-service --type=NodePort --name=nginx-gateway-nodeport

kubectl get pods
kubectl get svc sample-api-service
kubectl get svc apigateway-api-service



delete all
kubectl delete deployments --all --all-namespaces
kubectl delete services --all --all-namespaces
kubectl delete pods --all --all-namespaces
kubectl delete configmaps --all --all-namespaces
kubectl delete secrets --all --all-namespaces
kubectl delete pvc --all --all-namespaces
kubectl delete namespaces --all --exclude=kube-system

kubectl delete deployments nginx-sample-deployment
kubectl delete service nginx-sample-app-service;kubectl delete configmap nginx-sample-app-config;kubectl delete deployment sample-api-deployment;kubectl delete service sample-api-service

kubectl delete deployments nginx-apigateway-deployment
kubectl delete service nginx-gateway-app-service;kubectl delete configmap nginx-gateway-app-config;kubectl delete deployment apigateway-api-deployment;kubectl delete service apigateway-api-service




apt-get update && apt-get install htop -y
htop