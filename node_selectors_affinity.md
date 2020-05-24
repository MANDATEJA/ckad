## Node Selectors:

* Assigning labels created with node in Pod definition file so that the pod will deploy on that particular node.

ex:
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: myapp-pod
spec:
 containers:
  - image: data-processor
    name: data-processor
 nodeSelector:
  size: Large
```

### To label a node:
kubectl label nodes <node_name> <label-key>=<label_value>
  
Ex: kubectl label node node-1 size=Large

## Node Affinity:

Ex: Pod defnition file:
ex:
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: myapp-pod
spec:
 containers:
  - image: data-processor
    name: data-processor
 affinity:
  nodeAffinity:
   requiredDuringSchedulingIgnoreDuringExecution:
    nodeSelectorTerms:
     - matchExpressions:
        - key: size:
          operator: In
          values:
           - Large
           - Medium
```
Affinity section in above pod definition file describes scduling a pod on a node that is of size(label set on node) medium or large

Ex:
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: myapp-pod
spec:
 containers:
  - image: data-processor
    name: data-processor
 affinity:
  nodeAffinity:
   requiredDuringSchedulingIgnoredDuringExecution:
    nodeSelectorTerms:
     - matchExpressions:
        - key: size:
          operator: NotIn
          values:
           - Small
```
Affinity section in above pod definition file describes scduling a pod on a node that is not of size(label set on node) small

### Node Affinity types:
1. requiredDuringSchedulingIgnoredDuringExecution
2. preferredDuringSchedulingIgnoredDuringExecution
3. requiredDuringSchedulingRequiredDuringExecution
