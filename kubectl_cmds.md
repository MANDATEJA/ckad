## Pod related commands

kubectl get pods

kubectl get pods -o wide

kubectl describe pod <pod_name>

kubectl delete pod <pod_name>

kubectl edit pod <pod_name> #Lets you edit pod configuration

* To extract pod definition file from a running pod::
kubectl get pod <pod_name> -o yaml > pod-definition.yml
