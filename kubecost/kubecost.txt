Welcome! This guide will walk you through installing Kubecost into your Kubernetes cluster. The Kubecost helm chart includes all dependencies to get up and running and takes only a few minutes to install.

Before you begin
In order to deploy the Kubecost helm chart, ensure the following is completed:

• Helm client (version 3.0+) installed open_in_new
Step 1: Install Kubecost
Running the following commands will also install Prometheus, Grafana, and kube-state-metrics in the namespace supplied. View install configuration options here.

helm 3
kubectl create namespace kubecost
helm repo add kubecost https://kubecost.github.io/cost-analyzer/
helm install kubecost kubecost/cost-analyzer --namespace kubecost --set kubecostToken="<token>"

Step 2: Enable port-forward
kubectl port-forward --namespace kubecost deployment/kubecost-cost-analyzer 9090 file_copy
Having installation issues? View our Troubleshooting Guide or contact us directly at team@kubecost.com.

Step 3: See the data! Wahoo!
You can now view the deployed frontend by visiting the following link. Publish :9090 as a secure endpoint on your cluster to remove the need to port forward.

http://localhost:9090

With this newfound visibility, teams often start with 1) looking at cost allocation trends and 2) searching for quick cost savings or reliability improvements. View our Getting Started guide for more information on product configuration and common initial actions.

We're available any time for questions or concerns at team@kubecost.com and Slack (invite).


Updating Kubecost
Now that your Kubecost chart is installed, you can update with the following commands:

helm 2
helm repo update && helm upgrade kubecost kubecost/cost-analyzer file_copy
helm 3
helm repo update && helm upgrade kubecost kubecost/cost-analyzer -n kubecost file_copy

Deleting Kubecost
To uninstall Kubecost and its dependencies, run the following command:

helm 2
helm del --purge kubecost file_copy
helm 3
helm uninstall kubecost -n kubecost file_copy
