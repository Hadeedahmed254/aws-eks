# How to setup alb add on

Download IAM policy

```
curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.11.0/docs/install/iam_policy.json
```

Create IAM Policy
<img width="973" height="393" alt="Screenshot 2025-12-16 161504" src="https://github.com/user-attachments/assets/d1f6d33a-e1b2-4cc8-a0b6-cc6a6e87e453" />

```
aws iam create-policy \
    --policy-name AWSLBCIAMPolicy-hadeed \
    --policy-document file://iam_policy.json
```

Create IAM Role
<img width="1462" height="462" alt="Screenshot 2025-12-16 161522" src="https://github.com/user-attachments/assets/a91bf0d0-6e68-46f4-9003-1823d61141e0" />

```
eksctl create iamserviceaccount \
  --cluster=hadeed-first-cluster \
  --namespace=kube-system \
  --name=aws-load-balancer-controller \
  --role-name AmazonEKSLoadBalancerControllerRole \
  --attach-policy-arn=arn:aws:iam::211125523455:policy/AWSLBCIAMPolicy-hadeed \
  --approve
```

## Deploy ALB controller

Add helm repo

```
helm repo add eks https://aws.github.io/eks-charts
```

Update the repo

```
helm repo update eks
```

Install
<img width="1467" height="366" alt="Screenshot 2025-12-16 161927" src="https://github.com/user-attachments/assets/ce0c0839-ae4e-43ac-a077-61571003d2cf" />

```
helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system \
  --set clusterName=hadeed-first-cluster \
  --set serviceAccount.create=false \
  --set serviceAccount.name=aws-load-balancer-controller \
  --set region=us-east-1 \
  --set vpcId=vpc-0b2970d3b23322151
```

Verify that the deployments are running.
<img width="1136" height="125" alt="Screenshot 2025-12-16 162044" src="https://github.com/user-attachments/assets/9196dd24-54d5-4687-aa93-f8a10c6636fb" />

```
kubectl get deployment -n kube-system aws-load-balancer-controller
```

<img width="1471" height="78" alt="Screenshot 2025-12-16 162056" src="https://github.com/user-attachments/assets/75663664-64c2-4436-8152-c0af3477343d" />

