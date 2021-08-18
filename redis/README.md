# redis-pv.yaml

important, in script you must edit name of persistent volume because name are refer persistent volume claim (pvc) like this.
```
name: redis-data-[name of helm service]-master-0
```

example: 
```
name: redis-data-redis-master-0
```
```
kubectl create -f redis-pv.yaml
```
# value.yaml
```
helm install redis bitnami/redis --namespace redis -f values.yaml
```
```
helm uninstall redis bitnami/redis --namespace redis
```
