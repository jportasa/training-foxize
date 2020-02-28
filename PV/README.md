POD con un volumen mounted
```
kind: Pod
apiVersion: v1
metadata:
  name: custompod
  labels:
    app: nginx
spec:
  containers:
    - name: nginx
      image: nginx
      volumeMounts:
      - mountPath: "/var/www/html"
        name: external
  volumes:
    - name: external 
      persistentVolumeClaim:
        claimName: slow
```
Persistent Voulme Claim (PVC)
```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: slow
  labels:
    app: nginx
spec:
  storageClassName: generic
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```
Storage Class
```
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: generic
provisioner: kubernetes.io/aws-ebs
parameters:
  type: gp2 
  zones: eu-west-1a, eu-west-1b
  iopsPerGB: "10" 
  fsType: ext4
```