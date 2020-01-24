# k8s-webforce3

## Check
```shell script
  kubectl get nodes
  kubectl get node
  kubectl get node -o wide

## Deployment example
  kubectl create deployment nginx --image=nginx
  kubectl get deployments
  kubectl describe deployment nginx
  kubectl get events
  kubectl get deployment nginx -o yaml 
  kubectl get deployment nginx -o yaml > first.yaml

# "Travaux pratiques"
# replace yaml by json

# dry-run: comme son nom l'indique
k create deployment two --image=nginx --dry-run -o yaml
k get deployment nginx --export -o yaml
k replace -f first.yml
# create from .yml
k create -f first.yml 
k get svc nginx
k get deploy,pod,svc
k get pod
k delete pod <name (or id?)>
k delete svc <name (or id?)>
k expose deployment/<name(?)>
(curl <cluster-ip>) voir du html
k get ep <name>

k describe pod nginx-xxxx | grep Node:
# get pod node info
k get pod -o wide

k scale deployment  nginx --replicas=<number of replicas>
# set 1 to restart after "0" (example


k exec nginx-xxxx printenv |grep KUBERNETES
k expose deployment nginx --type=LoadBalancer

# Port Kubernetes dashboard (https)
k get svc -A
# Commande recuperation token
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}' )


## CPU and Limits
k create deployment hog --image vish/stress
k describe deployment hog

k get deployment hog --export -o yaml > hog.yml

# "Monitoring"
(connect to node)
"htop"
# Note !!!!
!!!!! connect to https for master !!!!!
```