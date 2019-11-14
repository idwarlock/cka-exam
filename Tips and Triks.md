# Tips and Triks

Create alias for kubectl
```bash
echo "alias k=kubectl" > ~/.bashrc
. !$
```

Set configuration context:
```bash
kubectl config use-context k8s
```

Nodes comprising each cluster can be reached via ssh, using a command such as the following:
```bash
ssh k8s-node-0
```

Elevated privileges can be assumed on any node with the following command:
```bash
sudo -i
```