# Cisco Router Basic Operations
Great for INFSCI 1660 at Pitt. Also good for general packet tracer use.
No routers were harmed in the making of this document.

## Vlans
```
show vlan id *Number*
show interfaces trunk
```


### Add Interface to Vlan
```
interface *Name*
switchport access vlan *Number*
```

### Trunk Interface
```
interface *Name* 
switchport trunk encapsulation dot1q 
switchport mode trunk

switchport trunk native vlan *Number* switchport trunk allowed vlan *Number* 
switchport trunk allowed vlan add *Extras* 
no shutdown
```

### Make SVI

### Spanning Tree
```
spanning-tree vlan *Number* priority *Number*
``` 

## Static Routing
```
show interface *Name* switchport
show ip interface brief
show ip route
show run | in ip.route

#to reset interface
default *Interface Name*

#to remove route
no ip route *request address* *mask* *direct to address*
```

### Add Static Route
```
interface *Name*

#disable switchport(routers do not have switchport)
no switchport

#set ip address
ip address *address* *mask*
no shutdown

#set route
ip route *request address* *mask* *direct to address*
```
To set default route set address and mask = 0.0.0.0
## OSPF