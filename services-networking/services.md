# Services:
Enable communication between various compenents within and outside the application

Loose coupling between microservices

## Service types:
1. NodePort - For ouside cluster access by end users
2. ClusterIP - To enable communication between different services
3. LoadBalancer - Distribute load across diferrent webservers.

### NodePort:
3 ports involved:
1. targetport - port inside container
2. port - service port
3. nodeport - port on the node

### service-definition.yml
```yaml
apiVersion: v1
kind: Service
metadata:
 name: myapp-service
spec:
 type: NodePort
 ports:
  - targetPort: 80
    port: 80 # Mandatory
    nodePort: 30008 # A port is dynamically allocated if not slected already
 selector:
  app: my-app
  type: front-end
```

kubectl get services

### ClusterIP

```yaml
apiVersion: v1
kind: Service
metadata:
 name: backend
spec:
 type: ClusterIP
 ports:
  - targetPort: 80
    port: 80 # Mandatory
 selector:
  app: my-app
  type: backend
```

* Other pods can access ClusterIP service using service name or ClusterIP
