## Pre-requisites:

### Pod status:
pending -> container creating -> running
### Pod conditions:
1. pod scheduled - true/false
2. initialized - true/false
3. containers ready - true/false
4. ready - true/false

## Readiness probe:
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: simle-webapp
spec:
 containers:
  - name: simple-webapp
    image: simple-webapp
    ports:
     - containerPort: 8080
    readinessProbe:
     httpGet:
      path: /api/ready
      port: 8080
     initialDelaySeconds: 10 # Time to wait befoew probing
     periodSeconds: 5 # time intervals to probe
     failureThreshould: 8 # No of probes before reporting failure
```
### TCP connection:
```yaml
readinessProbe:
 tcpSocket:
  port: 3306
 initialDelaySeconds: 10 # Time to wait befoew probing
 periodSeconds: 5 # time intervals to probe
 failureThreshould: 8 # No of probes before reporting failure
```
### Execute a command:
```yaml
readinessProbe:
 exec:
  command:
   - cat
   - /app/is_ready
 initialDelaySeconds: 10 # Time to wait befoew probing
 periodSeconds: 5 # time intervals to probe
 failureThreshould: 8 # No of probes before reporting failure
```

