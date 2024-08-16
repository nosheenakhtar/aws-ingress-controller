
1.	Edit the file and change the VPC CIDR in use for the Kubernetes cluster:
          proxy-real-ip-cidr: XXX.XXX.XXX/XX

2.	Change the AWS Certificate Manager (ACM) ID as well:

            arn:aws:acm:us-west-2:XXXXXXXX:certificate/XXXXXX-XXXXXXX-XXXXXXX-XXXXXXXX

3.	Deploy the manifest:
kubectl apply -f deploy.yaml


finally installed by this command 

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.8.2/deploy/static/provider/cloud/deploy.yaml
