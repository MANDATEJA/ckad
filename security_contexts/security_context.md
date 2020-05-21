* Security cotext to a container can be added at the pod level or at the container level. Container level configuraiton overrides pod level configuration

Pod Level:
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: my-pod
spec:
 securityContext:
  runAsUser: 1000
 containers:
  - name: ubuntu
    image: ubuntu
    command: ["sleep","3600"]
```
Container Level:
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: my-pod
spec:
 containers:
  - name: ubuntu
    image: ubuntu
    command: ["sleep","3600"]
    securityContext:
     runAsUser: 1000
     capabilities:
      add: ["MAC_ADMIN"]
```

### Note: 
Capabilities are only supported at container level and not at pod level.
