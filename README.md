# GitOps
DevOps Workshop

https://www.baeldung.com/ops/kubernetes-kind

# Tasks:

01. Containerize Application 

    docker build -t web-api .
    docker images
    docker run -d -p 15684:8080 web-api
    docker ps

    http://localhost:15684/weatherforecast

    docker stop 79c669e62ff4
    docker rm 79c669e62ff4

02. Push Docker image to DockerHub
    docker login
    docker tag web-api  e880613/web-api:v1
    docker images
    docker push e880613/web-api:v1

03. Setup Cluster Infrastructure
    kind version
    kind get clusters
    kind create cluster --name my-cluster
    kubectl cluster-info --context kind-my-cluster 
    kubectl get ns
    kubectl get nodes
    kubectl describe nodes
    kubectl get deployments -n kube-systems

    kubectl get pods -n kube-system
    kubectl get deployments -n default

    kubectl create ns dev

    kubectl create deployment myapp --image=e880613/web-api:v1 --replicas=2

    kubectl get deployments -n default

    kubectl get replicaset

    kubectl delete deployments myapp

    kubectl get deployments -n dev 

    kubectl get pods -n dev


    kind create cluster --config mycluster.yaml
    kind create cluster --config mycluster-config.yaml


    # Forward a local port to a port on the Pod
    kubectl port-forward  myapp-ff99498bf-q57cb 15684:8080 -n dev
    
    kind delete clusters --all