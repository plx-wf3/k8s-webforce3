# k8s-webforce3
# titre indicatif

## Namespace
```shell script
k create namespace <nameDuNamespace>
k get namespaces <nameDuNamespace>

# Create low-ressource-range.yml

k --namespace=low-usage-limit create -f low-ressource-range.yml

k get limitrange -A
#NAMESPACE          NAME                  CREATED AT
#low-usage-limit    low-ressource-range   2020-.............

k -n <nameDuNamespace> create deployment <nomDuPodVoulu> --image vish/stress
k -n <nameDuNamespace> get pod
k -n <nameDuNamespace> get pod <nomDuPoD(UUID)> -o yaml

#Voir qu'il est lancé
k get rs -A
# Delete le deploy lier au namespace
k -n <nomDuNamespace> delete deployments.apps <nomDuDeploy>

k create -f <json/yml file>
k describe rs = k describe replicasets.apps
k describe rs <nomDuReplicaset>
k get rs
k delete rs rs-one --cascade=false
 --> --cascade=false : conserve les pods créer

k edit po <nomDuPod>
k edit pod <nomDuPod>
# isoler le pod pour l'étudier ou travailler dessus sans affecter le reste
# k delete rs <rs-one> : ne delete pas les pod isolé
(change labels: system: IsolatedPod)
k get po -L system

k describe po rs-one-xpcvw | grep Image

# delete all IsolatedPod
k delete po -l system=IsolatedPod

rs-one metadata dans le fichier yaml
ds-one metadata dans le fichier yaml

# lance curl.yml dans le namespace kube-public
k create -f curl.yaml -n kube-public
k create -f frontend.yaml
k create -f webapp-service.yaml
chmod +x curl-test.sh
./curl-test.sh
# ouvrir un second shell pour modifier l'objet deployment k8s directed (pour voir le changement durant curl  -> v2)
k edit deploy <nomDuDeploy>

k rollout status deployment/frontend
k rollout history deployment/frontend
k rollout undo deployment/frontend


# Exercice configmap (??)
ubuntu@k8s-carmine-master:~/projet$ cd ..
ubuntu@k8s-carmine-master:~$ mkdir configmap
ubuntu@k8s-carmine-master:~$ cd configmap/
ubuntu@k8s-carmine-master:~/configmap$ mkdir primary
ubuntu@k8s-carmine-master:~/configmap$ echo c > primary/cyan
ubuntu@k8s-carmine-master:~/configmap$ echo m > primary/magenta
ubuntu@k8s-carmine-master:~/configmap$ echo y > primary/yellow
ubuntu@k8s-carmine-master:~/configmap$ echo k > primary/black
ubuntu@k8s-carmine-master:~/configmap$ echo "is k" >> primary/black
ubuntu@k8s-carmine-master:~/configmap$ echo blue > favorite

# en etant dans le dossier "configmap"
k create configmap colors --from-literal=text=black --from-file=./favorite --from-file=./primary/
(affiche: configmap/colors created)
k get configmaps
k get configmaps -o yaml

# apres upload du fichier simpleshell.yml
k create -f shell-demo
k exec -it shell-demo -- /bin/bash -c 'echo $ilike'
k exec -it shell-demo -- /bin/bash -c 'env'

```