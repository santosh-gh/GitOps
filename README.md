# GitOps
DevOps Workshop

https://www.baeldung.com/ops/kubernetes-kind
https://iamunnip.medium.com/kind-local-kubernetes-cluster-part-6-775397fa060d

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

    #Windows 
    Install Chocolatey first: https://chocolatey.org/install 
    choco install kind
    choco install kubernetes-cli
    kubectl version --client

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

04. Deploy app using helm chart
    https://wkrzywiec.medium.com/how-to-deploy-application-on-kubernetes-with-helm-39f545ad33b8
    # Installation

    - MacOS
    brew install helm

    - Windows
    choco install kubernetes-helm


    helm upgrade --install web-app . 

    helm install phoenix-chart phoenixnap/ --values phoenixnap/values.yaml