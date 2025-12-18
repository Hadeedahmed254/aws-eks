# 2048 App

## Create Fargate profile

```
eksctl create fargateprofile \
    --cluster hadeed-first-cluster \
    --region us-east-1 \
    --name first-fargate-profile \
    --namespace game-2048
```

## Deploy the deployment, service and Ingress

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/examples/2048/2048_full.yaml
OR
kubectl apply -f all-resources.yaml
```
<img width="1051" height="118" alt="Screenshot 2025-12-16 154319" src="https://github.com/user-attachments/assets/725a1e06-109c-42a7-bce3-42a7161928c2" />

### all the things created inn no time 
<img width="1140" height="442" alt="Screenshot 2025-12-16 161000" src="https://github.com/user-attachments/assets/864affdd-a19a-4e84-a060-8b978d73280e" />

done
![Screenshot 2023-08-03 at 7 57 15 PM](https://github.com/iam-veeramalla/aws-devops-zero-to-hero/assets/43399466/93b06a9f-67f9-404f-b0ad-18e3095b7353)
<img width="1919" height="1010" alt="Screenshot 2025-12-16 162509" src="https://github.com/user-attachments/assets/8379a6e6-b354-4bca-a8e0-d51bd7575dbc" />
