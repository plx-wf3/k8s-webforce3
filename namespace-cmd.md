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
# ouvrir un second shell pour modifier l'objet deployment k8s directed
k edit deploy <nomDuDeploy>
```