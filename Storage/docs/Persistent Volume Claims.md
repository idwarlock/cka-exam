# Persistent Volume Claims

Persistent Volume Claims (PVCs) are a way for an application developer to request storage for the application without having to know where the underlying storage is. PVCs consume PV resource and the claim is then bound to the Persistent Volume (PV), and it will not be released until the PVC is deleted.

Pods use claims as volumes.

Claims will remain unbound indefinitely if a matching volume does not exist. Claims will be bound as matching volumes become available. For example, a cluster provisioned with many 50Gi PVs would not match a PVC requesting 100Gi. The PVC can be bound when a 100Gi PV is added to the cluster. Notice that PVC requesting 1Gi will be bound with 50Gi PV!

So claims can request specific size and access modes.

Each PVC corresponds with a single PV.

Claims can specify a label selector to further filter the set of volumes. Only the volumes whose labels match the selector can be bound to the claim. The selector can consist of two fields:
- matchLabels - the volume must have a label with this value
- matchExpressions - a list of requirements made by specifying key, list of values, and operator that relates the key and values. Valid operators include In, NotIn, Exists, and DoesNotExist.

All of the requirements, from both matchLabels and matchExpressions, are ANDed together – they must all be satisfied in order to match.

Links:
- PersistentVolumeClaims
https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims

- Create a PersistentVolumeClaim
https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/#create-a-persistentvolumeclaim