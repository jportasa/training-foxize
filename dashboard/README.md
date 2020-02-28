# Dashboard

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml
```
```
kubectl proxy --port=8080 --address='0.0.0.0' --disable-filter=true &

```
```
http://localhost:8080/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
```

```
aws eks get-token --cluster-name <CLUSTER_NAME> | jq -r '.status.token'

```
