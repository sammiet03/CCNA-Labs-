### VLANs and Inter-VLAN Routing

##### Network Topology
<img src="https://user-images.githubusercontent.com/95317911/211118821-587a8921-46a1-4b3d-a9b7-c59d2db2a40b.PNG" width="50%" height="50%">

##### Configuring IP Addresses/Subnet Mask on each PC

| Device | IPv4 Address | Subnet Mask | Default Gateway |
| ------ | ------------ | ----------- | --------------- |
| PC1 | 10.0.0.1 | 255.255.255.192 | - |
| PC2 | 10.0.0.2 | 255.255.255.192 | - |
| PC3 | 10.0.0.65 | 255.255.255.192 | - |
| PC4 | 10.0.0.66 | 255.255.255.192 | - |
| PC5 | 10.0.0.129 | 255.255.255.192 | - |
| PC6 | 10.0.0.130 | 255.255.255.192 | - |

##### Configuring Interfaces between R1 and SW1,  Configure one Interface on R1 for each VLAN
R1
```
R1>en
R1#config t
R1(config)# int g0/0
R1(config)#ip add

R1(config)# int g0/1
R1(config)#ip add


R1(config)# int g0/2
R1(config)#ip add
```

##### Configuring SW1's Interfaces in the proper VLANs
SW1
```
First create the VLANs 10, 20, 30
SW1>en
SW1#config t
SW1(config)#vlan 10
SW1(config-vlan)#name Engineering
SW1(config-vlan)#vlan 20 
SW1(config-vlan)#name HR
SW1(config-vlan)#vlan 30
SW1(config-vlan)#name Sales

Next, configure each of the interfaces into the right VLAN
SW1(config)#int f3/1
SW1(config-if)#switchport mode access
SW1(config-if)#switchport access vlan 10 
SW1(config)#int f4/1
SW1(config-if)#switchport mode access
SW1(config-if)#switchport access vlan 10 

SW1(config)#int f5/1
SW1(config-if)#switchport mode access
SW1(config-if)#switchport access vlan 20
SW1(config)#int f6/1
SW1(config-if)#switchport mode access
SW1(config-if)#switchport access vlan 20 

SW1(config)#int f8/1
SW1(config-if)#switchport mode access
SW1(config-if)#switchport access vlan 30 
SW1(config)#int f7/1
SW1(config-if)#switchport mode access
SW1(config-if)#switchport access vlan 30 
```

