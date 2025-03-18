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
**DO NOT FORGET TO CREATE THE VLAN**
```
config t
vlan N
```

SVI: Default Interface for VLAN
```
interface vlan *Number*
ip address *First Usable Address* *Mask*
no shutdown
```

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
```
show ip ospf(pid)
```
### Add switch to ospf network
```
router ospf 1
network *Base Ip* *Inverted Mask* area *OSPF area number*
```
Base ip == base address on interface
### Add router to ospf network
```
router ospf *ospf process id*(not address)
router-id *Address*(looks like cidr but not)
```

### Add vlan into ospf network
```
router ospf 1
passive-interface Vlan *Number*
network *Base Ip* *Inverted Mask* area *OSPF area number*
redistribute connected subnets

interface *p2p interface*
ip ospf network point-to-point
```
Need to ask if area determines which traffic allowed and 0.0.0.0 means all

## BGP

### Create BGP Process
```
router bgp *Number*
bgp router-id *Address*
```

### Add Neighbor
```
router bgp *Number*
neighbor *Neighbor Address(ip)* remote-as *Neighbor Number*
```

### Advertise Existing Route
```
router bgp *Number*
network *route address* mask *Mask*
```