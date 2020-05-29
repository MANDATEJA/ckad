### Replicaset definition file

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
 name: simple-webapp
 labels:
  app: my-app
  function: front-end
spec:
 replicas: 3
 selector:
  matchLabels:
   app: my-app-pod
 template:
  metadata:
   labels:
    app: my-app-pod
    function: front-end
  spec:
   containers:
    - name: simple-webapp
      image: simple-webapp
```

## Annotations:
Annotations are used to record metadata of application
```yaml
metadata:
 name: my-app
 lebels:
  app: my-app
 annotations:
  buildversion: 1.1
  owner: madmint
```

