## Taints and Tolerations
Taints and tolerations are used to set restrictions on what pods can be scheduled on a node.

Taint: node - To repel pod that cannot tolerate the taint on the node
Toleration: pod - Pods that can tolerate the taint can land on node

### To set a taint on a node:
kubectl taint node <node_name> kay=value:taint-effect
### To remove a taint on a node
kubectl taint node <node_name> kay=value:taint-effect

Ex: kubectl taint nodes master node-role.kubernetes.io/master:NoSchedule-

#### Taint-effect:
1. NoSchedule - pods will not be scheduled on the node
2. PreferNoSchedule - The system will try to avoid placing a pod on the node, but not guarenteed.
3. NoExecute - New pods will not be scheduled and existing pods will be evicted.

ex: kubectl taint node node1 app=blue:NoSchedule

### To set tolerations on pod:
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
 tolerations:
  - key: "app"
    operator: "Equal"
    value: "blue"
    effect: "NoSchedule"
```
