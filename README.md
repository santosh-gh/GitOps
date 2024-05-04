# GitOps
DevOps Workshop

https://www.baeldung.com/ops/kubernetes-kind
https://iamunnip.medium.com/kind-local-kubernetes-cluster-part-6-775397fa060d
https://iamunnip.medium.com/kind-local-kubernetes-cluster-part-5-25844d448926



https://www.digitalocean.com/community/developer-center/implementing-gitops-using-flux-cd

https://blog.zelarsoft.com/using-gitops-with-flux-5723b7724f2f

https://medium.com/@selvamraju007/fluxcd-introduction-and-installation-demo-fb9fe0cb7555

https://medium.com/@david.franko1998/kubernetes-gitops-with-flux-cd-on-github-c867b1decf9f

https://www.techtarget.com/searchitoperations/tutorial/Try-out-this-GitOps-tutorial-with-Flux-and-Kubernetes

Automating Image Updates with FluxCD on AKS
-------------------------------------------
https://paulyu.dev/article/automating-image-updates-with-fluxcd-on-aks/

Git going with GitOps on AKS: A Step-by-Step Guide using FluxCD AKS Extension
-----------------------------------------------------------------------------
https://dev.to/azure/git-going-with-gitops-on-aks-a-step-by-step-guide-using-fluxcd-aks-extension-499m


https://neo4j.com/developer-blog/set-up-gitops-full-stack-app-with-flux-helm-kubernetes/?utm_source=Google&utm_medium=PaidSearch&utm_campaign=Evergreen&utm_content=EMEA-Search-SEMCE-DSA-None-SEM-SEM-NonABM&utm_term=&utm_adgroup=DSA&gad_source=1&gclid=CjwKCAjw5v2wBhBrEiwAXDDoJR6LGVzsjxbe1TbsW2qYYiI3JAaIoJXVEk8qil_4uHhmh2x7_uUaNRoCFqYQAvD_BwE

https://fluxcd.io/flux/concepts/

https://yodamad.hashnode.dev/build-and-publish-an-helm-chart-deploy-it-with-flux

https://medium.com/swlh/deploying-applications-in-kubernetes-using-flux-a9d171b11917

https://geek-cookbook.funkypenguin.co.nz/kubernetes/deployment/flux/operate/
https://alicegg.tech/2020/11/09/helm


The FASTEST way to deploy apps to Kubernetes - GitOps with FLUX
--------------------------------------------------------------
https://technotim.live/posts/flux-devops-gitops/

Using Flux in Kubernetes
---------------------------
https://siebjee.nl/posts/using-flux-in-kubernetes/

Kubernetes GitOps with Flux
----------------------------
https://cloudtechnologyexperts.com/blog/kubernetes/kubernetes-gitOps-with-flux



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

    kubectl port-forward svc/web-app-service --address 0.0.0.0 8080:8080

    
    kind delete clusters --all

    kubectl cluster-info --context kind-dev
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

    kubectl -n ingress-nginx get pods --selector=app.kubernetes.io/component=controller


04. Deploy app using helm chart
    https://wkrzywiec.medium.com/how-to-deploy-application-on-kubernetes-with-helm-39f545ad33b8
    # Installation

    - MacOS
    brew install helm

    - Windows
    choco install kubernetes-helm


    helm upgrade --install web-app . 

    helm install phoenix-chart phoenixnap/ --values phoenixnap/values.yaml

    kubectl run nginx --image=e880613/web-api:v1 --port=8080 --dry-run=client -o yaml > webapp.yml

05. Kustomization
    https://www.densify.com/kubernetes-tools/kustomize/