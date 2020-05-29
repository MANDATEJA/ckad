## Pod related commands

kubectl get pods

kubectl get pods -o wide

kubectl get pods --selector app=my-app

kubectl describe pod <pod_name>

kubectl delete pod <pod_name>

kubectl edit pod <pod_name> #Lets you edit pod configuration

* To extract pod definition file from a running pod::
kubectl get pod <pod_name> -o yaml > pod-definition.yml

## Replica Set related commands

kubectl get replicasets

kubectl get replicasets -o wide

kubectl describe repliaset <replicaset_name>

kubectl delete repliaset <replicaset_name>

kubectl edit repliaset <replicaset_name> #Lets you edit repliaset configuration

kubectl scale replicaset <replicaset_name> --replicas=5

* To extract repliaset definition file from a running repliaset::
kubectl get repliaset <repliaset_name> -o yaml > repliaset-definition.yml

## Generic commands

kubectl get all # To see all created objects

## To view logs of a pod

kubectl logs -f <pod_name>

## To view logs of a particular container of a multicontainer pod

kubectl logs -f <pod_name> <image_name>

