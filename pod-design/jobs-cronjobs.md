# Job:
Pod managet that ensures pods are created to complete assigned jobs and existed cleanly

### definition file:
```yaml
apiVersion: batch/v1
kind: Job
metadata:
 name:math-add-job
spec:
 completions: 3 #replicas
 template:
  spec:
   containers:
    - name: math-add
      image: ubuntu
      command: ['expr', '3', '+', '2']
   restartPolicy: Never
```

kubectl create -f job-definition.yml

kubectl get jobs

kubectl delet job math-add-job

