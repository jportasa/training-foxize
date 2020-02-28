EKS Cluster VPC requirements

https://docs.aws.amazon.com/eks/latest/userguide/network_reqs.html

Create cluster
```
eksctl create cluster -f step10-eks-course.yaml
```


# Create nodegroup
```
eksctl create nodegroup -f step10-eks-course.yaml --include= <nodegroup name>
```

# Delete nodegroup
```
eksctl delete nodegroup --cluster <cluster-name> --name <nodegroup name>
```

# update kubeconfig
```
aws eks --region us-east-1 update-kubeconfig --name <cluster-name>
```
