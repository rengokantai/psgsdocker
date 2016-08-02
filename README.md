#### psgsdocker
######16
```
docker service create --name name --replicas 5
```
######17
3 managers+3 working nodes  
IANA engine port: 2375  
secure: 2376  
swarm port: 2377
mgr1
```
docker swarm init --listen-addr ip1:2377 --secret SAF
```
mgr2:
```
docker swarm join --secret SAF --ca-hash sha256:1234 ip1:2377 --manager --listen-addr ip2:2377
```
