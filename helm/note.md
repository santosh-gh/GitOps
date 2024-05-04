
https://wkrzywiec.medium.com/how-to-deploy-application-on-kubernetes-with-helm-39f545ad33b8

choco install kubernetes-helm
helm version

helm create web-app
helm install web-app .  
helm upgrade  web-app .

http://172.18.0.2:31863/weatherforecast

helm lint web-app

helm upgrade newrelease apache-airflow/airflow --namespace dev --set images.airflow.repository=my-dags --set images.airflow.tag=0.0.1

helm install hello-app-chart ./hello-app-0.1.0.tgz
