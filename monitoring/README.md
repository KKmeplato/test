# Kubernetes Cluster Monitoring with Prometheus-Grafana

kubectl create ns monitoring 

![Alt text](image.png)

## Pre-requisites

Link to refer to install https://k21academy.com/docker-kubernetes/prometheus-grafana-monitoring/
### Step 1: Install Helm charts on cluster

curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh



### Step 2: Isntall Prometheus/grafana charts 
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add stable https://charts.helm.sh/stable  
helm repo update

#### Step3: install Prometheus Kubernetes 
helm install prometheus prometheus-community/kube-prometheus-stack

### Step 3: Kubernetes Prometheus Port Forward, Login to grafana
kubectl port-forward deployment/prometheus-grafana 3000
username: admin
password: prom-operator


you need to add Prometheus as a data source. Go to "Configuration" > "Data Sources" > "Add data source". Select Prometheus and provide the URL of your Prometheus instance (e.g., http://prometheus-server:9090)

![Alt text](image-1.png)