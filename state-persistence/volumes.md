### pod definition with volume mounts:
ex:
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: random-num-gen
spec:
 containers:
  - image: alpine
    name: alpine
    command: ["/bin/bash","-c"]
    args: ["shuf -i 0-100 -n 1 >> /opt/number.out;"]
    volumeMounts:
     - mountPath: /opt
       name: data-volume
 volumes:
  - name: data-volume
    hostPath:
     path: /data
     type: Directory
```

=> using hostPath in volume mounts is not preferable in a keberetes cluster as all nodes may not contain same directory and same data

### For ex: to configure AWS EBS on a pod:
```yaml
volumes:
 - name: data-volume
   awsElasticBlockStore:
    volumeID: <volume-id>
    fsType: ext4
```
