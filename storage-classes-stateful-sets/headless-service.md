> Create DNS for each pod using pod name and subdomain.

### EX DNS:
pod-name.headless-service.namespace.service.cluster.local

### headless-service-definition.yml
```yaml
apiVersion: v1
kind: Service
metadata:
 name: mysql-h
spec:
 ports:
  - port: 3306
 selector:
  app:mysql
 clusterIP: none # setting it to none creates a headless service
```

### to create a DNS record for a POD two properties need to be added to pod
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: my-pod
spec:
 containers:
  - name: my-sql
    image: my-sql
 sibdomain: mysql-h # should be same as headless service name
 hostname: my-pod
```
### stateful-set-definition.yml
```yaml
apiVersion: apps/v1
kind: statefulSet
metadata:
 name: mysql-statefulset
 labels:
  app: mysql
spec:
 serviceName: mysql-h #headless servicename to create DNS records
 replicas: 3
 matchLabels:
  app: mysql
 template:
  metadata:
   name: mysql-pod
   labels:
    app: mysql
  spec:
   containers:
    - name: mysql
      image: mysql
```
