* Security cotext to a container can be added at the pod level or at the container level. Container level configuraiton overrides pod level configuration

```yaml
apiVersion: v1
kind: Pod
metadata:
 name: my-pod
spec:
 securityContext:
  runAsUser: 1000
  capabilities:
   add: ["MAC_ADMIN"]
 containers:
  - name: ubuntu
    image: ubuntu
    command: ["sleep","3600"]
