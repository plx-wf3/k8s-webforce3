# k8s-webforce3

## Namespace
```shell script
k create namespace <nameDuNamespace>
k get namespaces <nameDuNamespace>

# Create low-ressource-range.yml

k --namespace=low-usage-limit create -f low-ressource-range.yml

k get LimitRange -A
#NAMESPACE          NAME                  CREATED AT
#low-usage-limit    low-ressource-range   2020-.............

k -n <nameDuNamespace> create deployment limited-hog --image vish/stress
k -n <nameDuNamespace> get pod
k -n <nameDuNamespace> get pod limited-<nomDuPoD(UUID)> -o yaml

#Voir qu'il est lancé
k get rs -A

```