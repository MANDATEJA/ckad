# Ingress

### Difference between Ingress and Service:
Ingressis used to mask nodeport and nodeIP that service exposes.

* Kubenetes cluster needs to be configured to have ingress controller and ingress resources configured before we can configure an ingress for our applications.

### Ingress controller:
* nginx
* Contour
* HAPROXY

To install controller:
* Create nginx eployment with right image and configuration
* Create a service to expose the deployment to the cluster

### Ingress resources
Ingress to expose applications
```yaml
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
 name: ingress-wear
spec:
 backend:
  serviceName: wear-service
  servicePort: 80
```

kubectl get ingress


Ingress creates a layer 7 Load balancer server and routes the traffic to specified service
