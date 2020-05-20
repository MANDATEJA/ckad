## Env value types

### Plain Key Value
```yaml
env:
 - name: APP_COLOR
   value: blue
```   
   
### ConfigMap
```yaml
env:
 - name: APP_COLOR
   valueFrom:
    configMapKey
```    
   
### Secrets:
```yaml
env:
 - name: APP_COLOR
   valueFrom:
    secretKeyFile
```
