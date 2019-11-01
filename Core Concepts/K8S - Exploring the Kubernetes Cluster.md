**K8S - Exploring the Kubernetes Cluster**

List all the nodes in the cluster

```bash
kubectl get nodes
```

List all the pods within all the namespaces

```bash
kubectl get pods --all-namespaces
```

List all the namespaces

See if there are any pods running in the default namespace

```bash
kubectl get pods
```

See if there are any pods running in the kube-system namespace

```bash
kubectl get pods -n kube-system
```

```bash
kubectl get pods --all-namespaces
```

Find the IP address of the API server running on the master node

```bash
kubectl get pods --all-namespaces -o wide
```

Find the label applied to the etcd pod on the master node

```bash
kubectl get pods --all-namespaces --show-labels -o wide
```

See if there are any deployments

```bash
kubectl get deployments
```