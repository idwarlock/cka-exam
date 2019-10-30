# Volume Access Modes

Volume access modes are how you specify the access of a node to your Persistent Volume.

There are three types of access modes:
- ReadWriteOnce (RWO) – the volume can be mounted as read-write by a single node
- ReadOnlyMany  (ROX) – the volume can be mounted read-only by many nodes
- ReadWriteMany (RWX) – the volume can be mounted as read-write by many nodes

The volume can only be mounted using one access mode at a time, even if it supports many. So Google Cloud disk, for example, can be mounted as read write once by a single node or at a different point in time, read only many by many nodes, but not at the same time, not simultaneously. So you couldn't have this node writing to this volume and then read by a completely different node at the same time.

Snippet:
```yaml
spec:
  capacity:
    storage: 1Gi
  accessModes:
  - ReadWriteOnce
  - ReadOnleMany
```

Links:
- Access Modes
https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes