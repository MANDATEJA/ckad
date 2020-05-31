### To check rollout history

kubectl rollout status deployment/<deployment_name>

### Two types of deployment strategy
1. Recreate strategy
2. Rolling update (Default)

### To rollback to a previous revision:

kubectl rollout undo deployment/<deployment_name>

### To check rollout history

kubectl rollout history deployment/<deployment_name>
