### Two types of service accounts
1. User account - used by Humans ex: admin, developer
2. Service account - Used by application ex: monitoring application like prometheus

### To create service account:
kubectl create serivce account <account_name>

### To get service accounts:
kubectl get serviceaccount

### To see account details:
kubectl describe serviceaccount <account_name>

* Each service account will have a token associated with it. This Bearer toekn can be used for authentication when making REST calls to an API
* We can assign permissions to this account using role based access control mechanisms.

### Using service account in pod definition file:
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: mu-pod
spec:
 containers:
  - name: my-app
    image: ap-image
 serviceAccount: dashboard-sa
```
