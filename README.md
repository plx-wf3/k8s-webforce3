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
# Recuperation info svc
k get svc <svcname> --export -o yaml > <filename>.yml


## CPU and Limits
k create deployment hog --image vish/stress
k describe deployment hog

k get deployment hog --export -o yaml > hog.yml


# "Monitoring"
(connect to node)
"htop"
# Note !!!!
!!!!! connect to https for master !!!!!

# Crontab
# crd = custom resource definition
k get crd
k describe crd <nomducrd>
# ct = crontab
k get ct
k describe ct

# Autoriser creation de pods sur le master
# PAS CONSEILLER EN PRODUCTION:  INTERDIT
# a des fins informative et pour tester chez soi (machines basse ressource)
k get node(s)
k describe node <nodename(master)>
# find "Taints" info (-i to ignore upper/lowercase)
k describe node <nodename(master)> | grep -i taints
k describe node | grep -i taints
# remove taint from nodes
# to remove add "-" at the end
k taint nodes --all node-role.kubernetes.io/master-
# remove "not-ready" taint from nodes
k taint nodes --all node.kubernetes.io/not-ready-
# create deployment normalement et P-E que ca le fera sur le master
# PAS CONSEILLER EN PRODUCTION:  INTERDIT

```
