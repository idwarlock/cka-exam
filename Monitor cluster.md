# Monitir Cluster

Before you get ability for monitoring Kubernetes Cluster you need to install a Metric-server.

Metric server collects metrics from the Summary API, exposed by Kubelet on each node.

View CPU and memory for the nodes
```bash
kubectl top node
```

View CPU and memory for the pods
```bash
kubectl top pod
```

View the CPU and memory for a pod's containers
```bash
kubectl top pods <pod_name> --containers
```