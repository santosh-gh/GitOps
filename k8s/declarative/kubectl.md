# https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

# Deployment - Keeps pods running!

    kubectl apply -f .\k8s\declarative\deployment.yaml 
    kubectl describe rs
    kubectl describe deployments
    kubectl get pods

# Service - Makes pods accessible 
    kubectl apply -f .\k8s\declarative\service.yaml  

    kubectl get svc

    kind create cluster --config .\k8s\declarative\kind.yaml

    kubectl cluster-info --context kind-dev