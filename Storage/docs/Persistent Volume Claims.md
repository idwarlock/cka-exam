# Persistent Volume Claims

Persistent Volume Claims (PVCs) are a way for an application developer to request storage for the application without having to know where the underlying storage is. The claim is then bound to the Persistent Volume (PV), and it will not be released until the PVC is deleted.

Each PVC corresponds with a single PV. 

Links:
- PersistentVolumeClaims
https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims

- Create a PersistentVolumeClaim
https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/#create-a-persistentvolumeclaim