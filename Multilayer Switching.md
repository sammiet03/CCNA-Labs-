### Multilayer Switching

##### Network Topology
<img src="https://user-images.githubusercontent.com/95317911/211126418-fa981906-eddc-459b-85b5-b0951195ce3c.PNG" width="50%" height="50%">


##### Configure a Point-to-Point Layer 3 connection between R1 to SW2 
```
R1(config)#int g0/0
R1(config-if)#ip add 10.0.0.194 255.255.255.252

SW2(config)#default int g1/0/2
SW2(config)#int g1/0/2
SW2(config-if)#no switchport -- disabling layer 2 
SW2(config-if)#ip add 10.0.0.193 255.255.255.252
SW2(config)#ip route 0.0.0.0 0.0.0.0 10.0.0.194 -- adding a default route
SW2(config)# int vlan 10 
SW2(config-if)#ip add 10.0.0.62 255.255.255.192
SW2(config)# int vlan 20 
SW2(config-if)#ip add 10.0.0.126 255.255.255.192
SW2(config)# int vlan 30 
SW2(config-if)#ip add 10.0.0.190 255.255.255.192
SW2(config-if)#exit
```
