## Env value types

### Plain Key Value
env:
 - name: APP_COLOR
   value: blue
   
### ConfigMap
env:
 - name: APP_COLOR
   valueFrom:
    configMapKey
   
### Secrets:
env:
 - name: APP_COLOR
   valueFrom:
    secretKeyFile
