# Creo namespaces
```
kubectl create namespace dev
kubectl create namespace pro
```
# Instalo helm para actuar sobre entorno dev
Setup tiller per namespace using RBAC on kubernetes

This will create tiller and run it as that service account (given that service account exists and has permission for that namespsace)

```
kubectl apply -f rbac-config.yaml
```

```
namespace="dev"
helm init --service-account "tiller-$namespace" --tiller-namespace $namespace
```
```
(python37) $ k get deploy -A
NAMESPACE     NAME            READY   UP-TO-DATE   AVAILABLE   AGE
dev           tiller-deploy   1/1     1            1           21s
kube-system   coredns         2/2     2            2           47m

```
