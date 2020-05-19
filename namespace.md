## Namespaces

### Connecting to a Service within same namespace::
* mysql.connect("db-service")

### Connecting to a Service in different namespace::
* mysql.connect("db-service.dev.svc.clutser.local") # where dev=namespace,svc=service,domain=cluster.local

## Namespace commands:
kubectl create namespace <namespace_name>

To set a namespace as default namespace:
kubectl confgi ser-context $(kubectl config current-context) --namespace=dev

To get pods in a namespace:
kubectl get pods --namespace=<namespace_name>

To get pods in all namespaces:
kubectl get pods --all-namespaces
