
-------------------------- Create static IP for ingress controller in azure
az aks show --resource-group OZ-RG-Owwll-QA --name Owwll-Test --query nodeResourceGroup -o tsv

az network public-ip create --resource-group resourcegroupname --location=eastus --name demo-public-ip --sku Standard --allocation-method static

172.177.46.181
-------------------------

Prerequisite

Install chocolaty on windows system
Install Helm using chocolaty

--------------------------------------------------

1. Install ingress-nginx controller

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update

helm upgrade --install ingress-nginx ingress-nginx/ingress-nginx --values values.yaml
helm uninstall ingress-nginx


2. Create Namespace in cluseter and install cert-manger using helm

kubectl create namespace cert-manager

helm repo add jetstack https://charts.jetstack.io

helm install cert-manager jetstack/cert-manager --namespace cert-manager --version v1.9.0 --set installCRDs=true
helm uninstall cert-manager

3. Create Ingress rule

kubectl apply -f .\{env}\ingress.yaml

4. Create ClusterIssuer/Issuer

5. Create Certificate

---- To get Kubeconfig  for creating service endpoint in CI/CD--------
kubectl config view --flatten > config.yml
