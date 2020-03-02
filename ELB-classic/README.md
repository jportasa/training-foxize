# ELB Classic
```
apiVersion: v1
kind: Service
metadata:
  name: web
  annotations:
    external-dns.alpha.kubernetes.io/hostname: nginx.test.net, webserver.helloworld.es.
    service.beta.kubernetes.io/aws-load-balancer-backend-protocol: http
    service.beta.kubernetes.io/aws-load-balancer-ssl-ports: "443,8443"
    service.beta.kubernetes.io/aws-load-balancer-ssl-cert: arn:aws:acm:eu-central...
    service.beta.kubernetes.io/aws-load-balancer-access-log-enabled: true
    # Specifies whether access logs are enabled for the load balancer
    service.beta.kubernetes.io/aws-load-balancer-access-log-emit-interval: "60"
    # The interval for publishing the access logs. You can specify an interval of either 5 or 60 (minutes).
    service.beta.kubernetes.io/aws-load-balancer-access-log-s3-bucket-name: "my-bucket"
    # The name of the Amazon S3 bucket where the access logs are stored
    service.beta.kubernetes.io/aws-load-balancer-access-log-s3-bucket-prefix: "my-bucket-prefix/prod"
    # The logical hierarchy you created for your Amazon S3 bucket, for example `my-bucket-prefix/prod`
    service.beta.kubernetes.io/aws-load-balancer-cross-zone-load-balancing-enabled: "true"
    # Specifies whether cross-zone load balancing is enabled for the load balancer
    service.beta.kubernetes.io/aws-load-balancer-extra-security-groups: "sg-53fae93f,sg-42efd82e"
    # A list of additional security groups to be added to the ELB
spec:
  selector:
    app: web
  type: LoadBalancer
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

# ALB + Ingress
Docu: https://medium.com/tensult/alb-ingress-controller-on-aws-eks-45bf8e36020d

Public subnets in your VPC should be tagged accordingly so that Kubernetes knows to use only those subnets for external load balancers.

Key:  kubernetes.io/role/elb

Value: 1

```
helm repo add incubator http://storage.googleapis.com/kubernetes-charts-incubator
```
```
helm install incubator/aws-alb-ingress-controller --set clusterName=EKS-cluster-joan-porta --set autoDiscoverAwsRegion=true --set autoDiscoverAwsVpcID=true --name alb-name --namespace kube-system
```