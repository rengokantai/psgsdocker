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
set autoaccept prop:
```
docker swarm init .. --auto-accept worker
docker swarm init .. --auto-accept manager
docker swarm init .. --auto-accept worker,manager
```
mgr1
```
docker swarm init --listen-addr ip1:2377 --secret SAF
```
mgr2:
```
docker swarm join --secret SAF --ca-hash sha256:1234 ip1:2377 --manager --listen-addr ip2:2377
```
manually accept  
mgr1
```
docker node ls
docker node accept 1234
```
promote a working to manager  
mgr3:
```
docker swarm join --secret SAF --ca-hash sha256:1234 ip1:2377 --listen-addr ip3:2377
```
(it joined as worker) by default, working node is joined by default. But not manager  
promote mgr3 to manager:  
in mgr1:
```
docker node promote 123
```
