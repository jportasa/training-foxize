# ALB+Ingress

Docu ALB: 
https://github.com/helm/charts/tree/master/incubator/aws-alb-ingress-controller

Docu AWS Ingress: 
https://github.com/kubernetes-sigs/aws-alb-ingress-controller

Ingress controller in kube-system
```
helm install alb-ingress incubator/aws-alb-ingress-controller \
--set clusterName=EKS-cluster-joan-porta \
--set autoDiscoverAwsRegion=true \
--set autoDiscoverAwsVpcID=true \
--namespace kube-system
```
Ingress in a namespace, for example use this one:
```
kubectl apply -f ingress.yaml
```
Create app example deployment/service in namespace that will use ALB ingress:
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/aws-alb-ingress-controller/v1.0.0/docs/examples/2048/2048-namespace.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/aws-alb-ingress-controller/v1.0.0/docs/examples/2048/2048-deployment.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/aws-alb-ingress-controller/v1.0.0/docs/examples/2048/2048-service.yaml
```
