choco install kubernetes-helm
helm version

helm create web-app
helm install web-app .  
helm upgrade  web-app .

http://172.18.0.2:31863/weatherforecast

helm lint web-app