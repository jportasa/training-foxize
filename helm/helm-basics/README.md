# Helm3 basics

https://www.youtube.com/watch?v=-uZ25iO1Z1k

```
(python37) $ helm repo ls
NAME    URL                                             
stable  https://kubernetes-charts.storage.googleapis.com
```

```helm search repo stable/kubernetes-dashboard```

```
helm install k8s-dashboard stable/kubernetes-dashboard
```

```
helm ls
```

```
helm ls --namespace dev 
```
```
helm install k8s-dashboard stable/kubernetes-dashboard --namespace dev
```

