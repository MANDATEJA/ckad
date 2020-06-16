=> Network policies are configured for pod to define what other pods are allowed to communicate with it

Ex:
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
 name: db-policy
spec:
 podSelector:
  matchLabels:
   role: db
 policyTypes:
  - Ingress
 ingress:
  - from:
     - podSelector:
        matchLabels:
         name: api-pod
     ports:
      - protocol: TCP
        port: 3306
```
