# Storage Objects

When none of the static PVs the administrator created match a user’s PersistentVolumeClaim, the cluster may try to dynamically provision a volume specially for the PVC. This provisioning is based on StorageClasses: the PVC must request a storage class and the administrator must have created and configured that class for dynamic provisioning to occur.

Claims that request the class "" effectively disable dynamic provisioning for themselves.

Snippet:
```yaml
spec:
  storageClassName: fast
```

```yaml
# There's not storageClass
spec:
  storageClassName: ""
```
A PV with no storageClassName has no class and can only be bound to PVCs that request no particular class.

Links:
- Object in Use Protection
https://kubernetes.io/docs/concepts/storage/persistent-volumes/#storage-object-in-use-protection

- Volumes
https://kubernetes.io/docs/concepts/storage/volumes/