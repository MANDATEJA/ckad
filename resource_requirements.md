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

### Note on default resource requirements and limits
In the previous lecture, I said - "When a pod is created the containers are assigned a default CPU request of .5 and memory of 256Mi". For the POD to pick up those defaults you must have first set those as default values for request and limit by creating a LimitRange in that namespace.


```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: mem-limit-range
spec:
  limits:
  - default:
      memory: 512Mi
    defaultRequest:
      memory: 256Mi
    type: Container
```
https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/memory-default-namespace/


```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: cpu-limit-range
spec:
  limits:
  - default:
      cpu: 1
    defaultRequest:
      cpu: 0.5
    type: Container
```
https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/cpu-default-namespace/
