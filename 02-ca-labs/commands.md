# kubectl api-resources - list the available commands
# kubectl describe -n deployments hpa # HorizontalPodAutoscaler

# Rolling updates and rollbacks
kubectl delete -n deployments hpa app-tier
kubectl edit -n deployments deployment app-tier
watch -n 1 kubectl get -n deployments deployments app-tier
kubectl edit -n deployments deployment app-tier
kubectl rollout -n deployments status deployment app-tier
tmux
kubectl edit -n deployments deployments app-tier (left terminal)
kubectl rollout -n deployments status deployment app-tier (right terminal)
kubectl rollout -n deployments pause deployment app-tier (left terminal)
kubectl get deployments -n deployments app-tier (left terminal)
kubectl rollout -n deployments resume deployment app-tier (left terminal)
kubectl rollout -n deployments undo deployment app-tier
kubectl scale -n deployments deployment app-tier --replicas=1


# kubectl exec -n deployments data-tier-... -it -- /bin/bash  --- log in to container and start bash command 

# aws ec2 describe-volumes --region=us-west-2 --filters="Name=tag:Type,Values=PV" --query="Volumes[0].VolumeId" --output=text --- create volumes

# kubectl describe -n volumes pvc --- describe persistence volume

# This 2 commands give same result but one exec in container the other from outside the container
## run outside the container kubectl exec -n config data-tier-... -- redis-cli CONFIG GET tcp-keepalive
## bin/bash inside container then exec 
### kubectl exec -n config data-tier-... -it -- /bin/bash 
### cat /etc/redis/redis.conf
### redis-cli CONFIG GET tcp-keepalive






