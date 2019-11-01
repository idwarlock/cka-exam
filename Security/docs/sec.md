# Creating a ClusterRole to Access a PV in Kubernetes

We have been given access to a three-node cluster. Within that cluster, a PV has already been provisioned. We will need to make sure we can access the PV directly from a pod in our cluster. By default, pods cannot access PVs directly, so we will need to create a ClusterRole and test the access after it's been created. Every ClusterRole requires a ClusterRoleBinding to bind the role to a user, service account, or group. After we have created the ClusterRole and ClusterRoleBinding, we will try to access the PV directly from a pod.

Log in to the Kube Master server using the credentials on the lab page (either in your local terminal, using the Instant Terminal feature, or using the public IP), and work through the objectives listed.

View the Persistent Volume.
Use the following command to view the Persistent Volume within the cluster:

 kubectl get pv
Create a ClusterRole.
Use the following command to create the ClusterRole:

 kubectl create clusterrole pv-reader --verb=get,list --resource=persistentvolumes
Create a ClusterRoleBinding.
Use the following command to create the ClusterRoleBinding:

 kubectl create clusterrolebinding pv-test --clusterrole=pv-reader --serviceaccount=web:default
Create a pod to access the PV.
Use the following YAML to create a pod that will proxy the connection and allow you to curl the address:

 apiVersion: v1
 kind: Pod
 metadata:
   name: curlpod
   namespace: web
 spec:
   containers:
   - image: tutum/curl
     command: ["sleep", "9999999"]
     name: main
   - image: linuxacademycontent/kubectl-proxy
     name: proxy
   restartPolicy: Always
Use the following command to create the pod:

 kubectl apply -f curlpod.yaml
Request access to the PV from the pod.
Use the following command (from within the pod) to access a shell from the pod:

 kubectl exec -it curlpod -n web -- sh
Use the following command to curl the PV resource:

 curl localhost:8001/api/v1/persistentvolumes
Conclusion
Congratulations on completing this lab!



kubectl create clusterrolebinding auditor --clusterrole=kubernetes-dashboard-readonly --serviceaccount=auditor:dashboard

