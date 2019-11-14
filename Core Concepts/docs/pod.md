# POD

View a curent pod
```bash
kubectl get pod
```

View a pod using its label selector
```bash
kubectl get pod -l env=dev
```

View all pods in default namespace
```bash
kubectl get pod
```

View pods in all namespaces
```bash
kubectl get pod --all-namespaces

kubectl get pod -A
```

## Pod's probes

```bash
livenessProbe:
   httpGet:
     path: /healthz
     port: 8081
 readinessProbe:
   httpGet:
     path: /
     port: 80
```