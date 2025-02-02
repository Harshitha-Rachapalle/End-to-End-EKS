**Install using Fargate**
eksctl create cluster --name demo-cluster --region us-east-1 --fargate

**Delete the cluster**
eksctl delete cluster --name demo-cluster --region us-east-1

**Download kubecongig i.e update**
aws eks update-kubeconfig --name demo-cluster --region us-east-1

**Deploymentof 2048 app**

**create Fargate profile**
eksctl create fargateprofile \
    --cluster demo-cluster \
    --region us-east-1 \
    --name alb-sample-app \
    --namespace game-2048

**Deploy the deployment, service and Ingress**
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/examples/2048/2048_full.yaml

**watch the status of pods pending or running**
kubectl get pods -n game-2048 -w

 Tocheck service
 kubectl get svc -n game-2048
 
Tocheck ingress 
kubectl get ingress -n game-2048

here address will be empty. because there is no ingress controller
now we create ingress controller which will read ingress resource that m=name is ingress-2048 which will entirely configure the load balancer

In our case create iam oidc provider using this command 
eksctl utils associate-iam-oidc-provider --cluster demo-cluster --approve


**commands to configure IAM OIDC provider**

export cluster_name=demo-cluster

oidc_id=$(aws eks describe-cluster --name $cluster_name --query "cluster.identity.oidc.issuer" --output text | cut -d '/' -f 5) 

**Check if there is an IAM OIDC provider configured already** 

aws iam list-open-id-connect-providers | grep $oidc_id | cut -d "/" -f4\n

If not, run the below command

eksctl utils associate-iam-oidc-provider --cluster $cluster_name --approve
