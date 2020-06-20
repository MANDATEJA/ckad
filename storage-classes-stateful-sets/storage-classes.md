Usually(without storage classes), if we are using google cloud storage, we need to create disk(gce-pd) storage for the PV before creating PV in k8s cluster. With storage classes, this can be eliminated and this process is called dynamic provisioning

### sc-definition.yml
```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
 name: google-storage
provisioner: kubernetes.io/gce-pd
parameters:
 type: pd-standard
 replication-type: none
```

>>> There are other provisioners such as, aws-ebc, azure-file, azure-disk, safe-fs, port -work, scale-io etc.,

### Note:
storage class takes care of creating PV. No need to create Pv explicitly. But we need to configure PVC to use storage class

Ex: pvc-definition.yml
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
 name: myclaim
spec:
 accessModes:
  - ReadWriteOnce
 storageClassName: google-storage
 resources:
  requests:
   storage: 500Mi
```

