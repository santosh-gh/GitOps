# kubectl commands for k8s
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

    # Forward a local port to a port on the Pod
    kubectl port-forward  myapp-ff99498bf-q57cb 15684:8080 -n dev