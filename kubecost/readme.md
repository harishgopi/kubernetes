# kubecost

Welcome! This guide will walk you through installing Kubecost into your Kubernetes cluster. The Kubecost helm chart includes all dependencies to get up and running and takes only a few minutes to install.

Before you begin
In order to deploy the Kubecost helm chart, ensure the following is completed:

• Helm client (version 3.0+) installed open_in_new
Step 1: Install Kubecost Running the following commands will also install Prometheus, Grafana, and kube-state-metrics in the namespace supplied. View install configuration options [here](https://github.com/kubecost/cost-analyzer-helm-chart/blob/master/README.md#config-options).

## Installation using helm3

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install foobar.

### step 1 : Installing kubecost
```bash
kubectl create namespace kubecost

helm repo add kubecost https://kubecost.github.io/cost-analyzer/

helm install kubecost kubecost/cost-analyzer --namespace kubecost --set kubecostToken="<token>"
```

### step 2 : port forwarding the deployment
```bash
kubectl port-forward --namespace kubecost deployment/kubecost-cost-analyzer 9090
```

### step 3 : See the data! Wahoo!
```bash
http://localhost:9090
```


With this newfound visibility, teams often start with 
1) looking at cost allocation trends and 
2) searching for quick cost savings or reliability improvements.

## Updating Kubecost
Now that your Kubecost chart is installed, you can update with the following commands:

### helm 2
```bash
helm repo update && helm upgrade kubecost kubecost/cost-analyzer file_copy
```
### helm 3
```bash
helm repo update && helm upgrade kubecost kubecost/cost-analyzer -n kubecost file_copy
```


## Deleting Kubecost
To uninstall Kubecost and its dependencies, run the following command:

### helm 2
```bash
helm del --purge kubecost file_copy
```
### helm 3
```bash
helm uninstall kubecost -n kubecost file_copy
```
