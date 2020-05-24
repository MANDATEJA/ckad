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
