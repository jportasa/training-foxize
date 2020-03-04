# Logs k8s to Cloudwatch

Docu: https://github.com/helm/charts/tree/master/incubator/fluentd-cloudwatch

```
kubectl create namespace logging
```
```
helm install logs-to-cloudwatch \
  --set awsRegion=us-east-1 \
  --set rbac.create=true \
  --namespace logging
    incubator/fluentd-cloudwatch
```

```
cat << EOF > pod-hello-world.yaml
apiVersion: v1
kind: Pod
metadata:
  name: hello-world
spec: 
  restartPolicy: Never
  containers:
  - name: hello
    image: alpine
    command: ["/bin/echo", "hello", "world"]
EOF

kubectl apply -f pod-hello-world.yaml
```
