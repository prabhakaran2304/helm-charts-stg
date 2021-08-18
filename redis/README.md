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

# Redis test 
```
kubectl exec -it -n redis redis-master-0 bash
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
Defaulted container "redis" out of: redis, volume-permissions (init)
1001@redis-master-0:/$ redis-cli -h redis-master-0 -a redis321
Warning: Using a password with '-a' or '-u' option on the command line interface may not be safe.
redis-master-0:6379> set hi "hello prabha"
OK
redis-master-0:6379> get hi
"hello prabha"
redis-master-0:6379> exit
1001@redis-master-0:/$ exit
exit
```
```
kubectl exec -it -n redis redis-replicas-0 bash
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
Defaulted container "redis" out of: redis, volume-permissions (init)
1001@redis-replicas-0:/$ redis-cli -h redis-replicas-0 -a redis321
Warning: Using a password with '-a' or '-u' option on the command line interface may not be safe.
redis-replicas-0:6379> get hi
"hello prabha"
redis-replicas-0:6379> exit
1001@redis-replicas-0:/$ exit
exit
```
```
kubectl exec -it -n redis redis-replicas-2 bash
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
Defaulted container "redis" out of: redis, volume-permissions (init)
1001@redis-replicas-2:/$ redis-cli -h redis-replicas-2 -a redis321
Warning: Using a password with '-a' or '-u' option on the command line interface may not be safe.
redis-replicas-2:6379> get hi
"hello prabha"
redis-replicas-2:6379> exit
1001@redis-replicas-2:/$ exit
exit
```
