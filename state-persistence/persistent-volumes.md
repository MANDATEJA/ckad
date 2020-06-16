## Persistent Volumes:
A cluster wide pool of storage volume created by k8s admin to be used by users deploying applications on the cluster. The users can now select storage from this pool using Persistent Volume Claims(PVC).

Ex:
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
 name: pv-voll
spec:
 accessModes:
  - ReadWriteOnce
 capacity:
  storage: 1Gi
 hostPath:
  path: /tmp/data
```

=> Here hostPath can be replaced by other storage types
