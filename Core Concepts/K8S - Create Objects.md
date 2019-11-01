# K8S - Create Objects

Create an object from yaml file:

```bash
kubectl apply -f <object.yaml>
```

Create an object from yaml file in specific namespace:

```bash
kubectl apply -f <object.yaml> -n <namespace_name>
```

Create objects from all yaml files in current directory:

```bash
kubectl apply -f .
```

Create object from STDIN:

```bash
cat << EOF | kubectl -f -n <namespace_name> -
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.7.9
        ports:
        - containerPort: 80
EOF
```