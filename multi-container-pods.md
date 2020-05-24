### Different patterns of multi-container pods:
1. Ambassador
2. Adaptor
3. Sidecar

Ex:
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: myapp-pod
spec:
 containers:
  - name: webapp
    image: nginx
  - name: log-agent
    image: log-agent
```
### Note:
Containers within same pod shares same life-cycle, networking(Both pods can refer each other as localhost), and storage

Examples of multi-container pods:
1. sidecar: logging agent: collect app logs and forward them tp central log server
2. Adaptor: Adapter container: Collect app logs, process them and send them to central logging server
3. Ambassador: Container with logic to connect to different DB instance

