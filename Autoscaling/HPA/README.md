# HPA Horitzontal Pod Autoscaler

Docu: https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/

```
kubectl create namespace metrics
```
Install metrics service
```
helm install --name metrics-server \
    stable/metrics-server \
    --version 2.9.0 \
    --namespace metrics
```
Confirm that the metrics API is available
```
kubectl get apiservice v1beta1.metrics.k8s.io -o yaml
```
```
cat << EOF > hpa.yaml
apiVersion: autoscaling/v2beta2
kind: HorizontalPodAutoscaler
metadata:
  name: 2048-deployment      # Change
  namespace: 2048-game    # Change
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: 2048-deployment    # Change
  minReplicas: 1        # Change
  maxReplicas: 10       # Change
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 50 # Change
EOF
```
Apply changes
```
kubectl apply -f hpa.yaml
```
Check HPA is working
```
kubectl get hpa -A
```
