### Pod definition file
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: my-app-pod
 labels:
  tier: app
spec:
 containers:
  - name: webapp
    image: nginx
    ports:
     - containerPort: 8080
    env:
     - name: APP_COLOR
       value: blue
    resources:
     requests:
      memory: "1Gi"
      cpu: 1
     limits:
      memory: "2Gi"
      cpu: 2
```
### Note:
Limits property under pod.spec.containers[0].resources is there to make sure the container does not consume more than what is specified.
