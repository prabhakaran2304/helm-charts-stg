# redis-pv.yaml

important, in script you must edit name of persistent volume because name are refer persistent volume claim (pvc) like this.
```
name: redis-data-[name of helm service]-master-0
```

example: 
```
name: redis-data-redis-master-0
```
