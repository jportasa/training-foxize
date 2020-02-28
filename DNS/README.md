# Service discovery
Docu:

service discovery https://aws.amazon.com/blogs/opensource/unified-service-discovery-ecs-kubernetes/
https://github.com/kubernetes-sigs/external-dns/blob/master/docs/tutorials/aws.md#set-up-a-hosted-zone

## IAM permisions to Route53
```
aws iam create-group --group-name external-dns
aws iam attach-group-policy --policy-arn arn:aws:iam::aws:policy/AmazonRoute53AutoNamingFullAccess --group-name external-dns
aws iam create-user --user-name external-dns
aws iam add-user-to-group --user-name external-dns --group-name external-dns
```

## Step 2: Set Up a Namespace
```
aws servicediscovery create-private-dns-namespace --name "pepe.es" --vpc “vpc-0fd7ea4682360ddfb”
```
```
aws servicediscovery list-namespaces
```

Modificar valores en external-dns-serviceaccount.yaml
```
$ kubectl apply -f external-dns-serviceaccount.yaml
```
Modificar valores en external-dns-deployment.yaml
```
$ kubectl apply -f external-dns-deployment.yaml
```
crear service+Deployment para tetear
```
$ kubectl apply -f nginx-deployment.yaml
```
