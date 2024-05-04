docker build -t hello-app:1.0 .

kind create cluster --name my-cluster

 kind create cluster --config cluster-config.yaml

 kind load docker-image hello-app:1.0 --name my-cluster

 kubectl apply -f deployment.yml

 kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/kind/deploy.yaml

kubectl apply -f namespace.yaml

kubectl delete deployment --all --namespace=default

kubectl delete service hello-app-svc -n default


kind create cluster --config cluster.yaml 

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

kubectl get pods -n ingress-nginx

kubectl get services -n ingress-nginx

kubectl get ingressclass -A

kind load docker-image hello-app:1.0 --name my-cluster

kubectl apply -f namespace.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml

kubectl get ingress -n dev