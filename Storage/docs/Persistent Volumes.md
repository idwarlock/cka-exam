# Persistent Volumes

A PersistentVolume (PV) is a piece of storage in the cluster that has been provisioned by an administrator or dynamically. It's a layer of abstraction.

PVs are volume plugins like Volumes, but have a lifecycle independent of any individual Pod that uses the PV. This API object captures the details of the implementation of the storage, be that NFS, iSCSI, or a cloud-provider-specific storage system.

Pods in Kubernetes are ephemeral, which makes the local container filesytem unusable, as you can never ensure the pod will remain. To decouple your storage from your pods, you will be creating a persistent volume to mount for use by your pods.

Having persistent storage means that we can use that same volume with different pods in our Kubernetes cluster and access the same data.

PVs are cluster level objects so they havn't a namespace.

Reclaiming Policy:
- Retain – manual reclamation
- Delete – delete an underline storage, associated storage asset such as AWS EBS, GCE PD, Azure Disk, or OpenStack Cinder volume is deleted
- Recycle – basic scrub (rm -rf /thevolume/*) (Depricated)

Currently, only NFS and HostPath support recycling. AWS EBS, GCE PD, Azure Disk, and Cinder volumes support deletion.

You need to  set Node Afinity for local volumes. Pods that use a PV will only be scheduled to nodes that are selected by the node affinity.

A volume will be in one of the following phases:
- Available – a free resource that is not yet bound to a claim
- Bound – the volume is bound to a claim
- Released – the claim has been deleted, but the resource is not yet reclaimed by the cluster
- Failed – the volume has failed its automatic reclamation

Snippet:
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  storageClassName: ""
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
```

Links:
- Persistent Volumes
https://kubernetes.io/docs/concepts/storage/persistent-volumes/

- Configure Persistent Volume Storage
https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/