# kubectl create app

```bash
 kubectl run webapp --image=nginx:latest --port=80 --replicas=3 -n web

 kubectl run busybox --image=busybox --rm -it --restart=Never -- sh

kubectl expose deployment/webapp --port=80 --target-port=80 --type=NodePort -n web --dry-run -o yaml > web-service.yaml

 kubectl apply -f web-service.yaml
```