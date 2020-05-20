### Imperative:
kubectl create configmap <configmap_name> --from-literal=<key>=<value>

#### ex:
```yaml
kubectl create configmap \
 app-config --from-literal=APP_COLOR=blue \
            --from-literal=APP_MOD=prod
```

### Declarative:
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
 name: app-config
data:
 APP_COLOR: blue
 APP_MODE: prod
 ```
 
 kubectl create -f configmap-definition.yml
