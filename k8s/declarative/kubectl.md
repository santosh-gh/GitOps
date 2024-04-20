# https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

# Deployment - Keeps pods running!

    kubectl apply -f .\k8s\declarative\deployment.yaml 
    kubectl describe rs
    kubectl describe deployments
    kubectl get pods

# Service - Makes pods accessible 
    kubectl apply -f .\k8s\declarative\service.yaml  

    kubectl get svc



    apiVersion: v1
kind: Service
metadata:
   name: bb-entrypoint
   namespace: default
spec:
   type: NodePort
   selector:
      bb: web
   ports:
      - port: 3000
        targetPort: 3000
        nodePort: 30001

