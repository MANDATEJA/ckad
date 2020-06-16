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
