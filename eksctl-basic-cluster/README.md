EKS Cluster VPC requirements

https://docs.aws.amazon.com/eks/latest/userguide/network_reqs.html


If you plan to have ALB+ingress create the policy
```
./ALBIngressControllerIAMPolicy.sh
```

Create cluster
```
eksctl create cluster -f step20-eks-course.yaml
```


# Create nodegroup
```
eksctl create nodegroup -f step20-eks-course.yaml --include=mix
```

# Delete nodegroup
```
eksctl delete nodegroup --cluster <cluster-name> --name <nodegroup name>
```

# update kubeconfig
```
aws eks --region us-east-1 update-kubeconfig --name <cluster-name>
```
