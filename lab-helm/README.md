# Installer Helm
##Installation de binaire helm
```shell script
   wget https://get.helm.sh/helm-v3.0.2-linux-amd64.tar.gz
   tar -zxvf helm-v3.0.2-linux-amd64.tar.gz
   cd linux-amd64/
   sudo mv helm /usr/local/bin/helm
   helm help
```
## Chercher un chart dans le repository hub 
``` helm search hub wordpress```  

## ajouter un repo et installer mysql  chart
```shell script
    helm repo add stable https://kubernetes-charts.storage.googleapis.com```
    helm search repo stable
    helm repo update
    (aller dans le dossier projet puis dossier (lab-)helm)
    k create -f mysqldb-hostpath.yaml
    k get pv
    (pv : persistentvolume)
    (pv : definition taille volume)
    k create -f mysqldb-pvc.yaml
    k get pvc
    (pvc : persistentvolumeclaims)
    (pvc : assignement à kubernetes)
    helm install  mysql --set mysqlRootPassword=rootpassword,mysqlUser=mysql,mysqlPassword=my-password,mysqlDatabase=mydatabase,persistence.existingClaim=mysql-pvc stable/mysql
    k get pod
    watch kubectl get pod
```
## mysql admin
```shell script
   MYSQL_ROOT_PASSWORD=$(kubectl get secret --namespace default mysql -o jsonpath="{.data.mysql-root-password}" | base64 --decode; echo)
  echo $MYSQL_ROOT_PASSWORD
```
## se connecter a Mysql en dehors du cluster 
```shell script
     sudo apt-get install -y mysql-client-core-5.7
     k port-forward svc/mysql 3306
     mysql -h 127.0.0.1 -P 3306 -u root -p
``` 

