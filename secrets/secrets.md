### Imperative:
kubectl create secret generic <secret_name> --from-literal=<key>=<value>

#### ex: key=value
```yaml
kubectl create secret generic \
 app-secret --from-literal=DB_HOST=myhost \
            --from-literal=DB_user=root \
            --from-literal=DB_PASS=passwd
```
#### ex: from-file
```yaml
kubectl create secret generic app-secret --from-file=/path/to/file
```

### Declarative:
```yaml
apiVersion: v1
kind: Secret
metadata:
 name: app-secret
data:
 DB_Host: mysql
 DB_User: root
 DB_password: passwd
 ```
 There secrets will be available in environment variable form inside container
 It is better to base64 encode and cretae secret and then decode that inside container
 
 kubectl create -f secret-definition.yml
