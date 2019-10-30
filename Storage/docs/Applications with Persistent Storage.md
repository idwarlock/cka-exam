# Applications with Persistent Storage

Create objects:
```bash
kubectl apply -f .
```

Verify:
```bash
kubectl get sc

kubectl get pv

kubectl get pvc

kebectl get deploy

kubectl rollout status deployments kubeserve

kubectl get po

kubectl exec -it [pod-name] -- touch /data/file1

kubectl exec -it [pod-name] -- ls /data
```

Snippet:

```yaml
---
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: fast
provisioner: kubernetes.io/gce-pd
parameters:
  type: pd-ssd

---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv-gce
spec:
  storageClassName: gce
  capacity: 
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  gcePersistentDisk:
    pdName: gce-volume
    fsType: ext4

---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: kubeserve-pvc 
spec:
  storageClassName: fast
  resources:
    requests:
      storage: 100Mi
  accessModes:
    - ReadWriteOnce

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: kubeserve
spec:
  replicas: 1
  selector:
    matchLabels:
      app: kubeserve
  template:
    metadata:
      name: kubeserve
      labels:
        app: kubeserve
    spec:
      containers:
      - env:
        - name: app
          value: "1"
        image: linuxacademycontent/kubeserve:v1
        name: app
        volumeMounts:
        - mountPath: /data
          name: volume-data
      volumes:
      - name: volume-data
        persistentVolumeClaim:
          claimName: kubeserve-pvc
```