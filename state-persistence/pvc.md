### One to one relationship between PC and PVC meaning only one PC for one PVC

### PVC definition.yaml
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
 name: myclaim
spec:
 accessModes:
  - ReadWriteOnce
 resources:
  requests:
   storage: 500Mi
```

### Note:
If we delete PVC, PC will still be retained based on `persistentVolumeReclaimPloicy: Retain`(Default) property .

To delete PC with PVC delete: `persistentVolumeReclaimPloicy: Retain`. We can also make it available to other PVCs by setting `persistentVolumeReclaimPloicy: Recycle` property in PC definition file.
