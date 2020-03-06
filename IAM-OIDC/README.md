# IAM OIDC
Docu:
https://eksctl.io/usage/iamserviceaccounts/

Amazon EKS supports IAM Roles for Service Accounts (IRSA) that allows cluster operators to map AWS IAM Roles to Kubernetes Service Accounts.

# Test if my POD have permissions to S3

```
cat <<EOF > /tmp/pod-with-iam.yaml
apiVersion: v1
kind: Pod
metadata:
  name: aws-cli
  namespace: dev
spec:
  serviceAccountName: s3-reader
  restartPolicy: Never
  containers:
  - name: aws-cli
    command: ["sleep", "10000"]
    image: mikesir87/aws-cli
EOF
```
```
kubectl apply -f /tmp/pod-with-iam.yaml
```