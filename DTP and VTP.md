### DTP AND VTP

##### Network Topology
<img src="https://user-images.githubusercontent.com/95317911/211127243-6629e062-23a6-41d6-8c9f-111dcf9f2199.PNG" width="50%" height="50%">


##### Configure the switchports connecting switches as trunk ports
```
SW1>en
SW1#config t
SW1(config)#int g0/1
SW1(config-if)#switchport mode trunk
SW1(config-if)#switchport nonegotiate

SW2>en
SW2#config t
SW2(config)#int range g0/1-2
SW2(config-if-range)#switchport mode trunk
SW2(config-if-range)#switchport nonegotiate -- to disable DTP

SW3>en
SW3#config t
SW3(config)#int g0/1
SW3(config-if-range)#switchport mode trunk
SW3(config-if-range)#switchport nonegotiate -- to disable DTP
```

##### Configure SW1 in VPT domain CCNA
```
Create VLANs 10, 20, 30
SW1>en
SW1(config)#vlan 10
SW1(config-vlan)#vlan 20 
SW1(config-vlan)#vlan 30 

VTP Domain
SW1(config)#vtp domain CCNA
```

##### Configure SW2 in VTP transparent mode
```
SW2(config)#vtp mode transparent 

Add VLAN 40 to SW2
SW1(config)#vlan 40 
```

##### Configure SW3 in VTP client mode
```
SW3(config)#vtp mode client
```

##### Configure all switchports connected to hosts in the correct VLAN
```
SW3(config)#int f0/1
SW3(config-if)#sw mode access
SW3(config-if)#sw ac vlan 10
SW3(config)#int range f0/2-3
SW3(config-if)#sw mode access
SW3(config-if)#sw ac vlan 30
SW3(config)#int f0/4
SW3(config-if)#sw mode access
SW3(config-if)#sw ac vlan 20

SW2(config)#int range f0/1-2
SW2(config-if)#sw mode access
SW2(config-if)#sw ac vlan 40

SW1(config)#int range f0/1-2
SW1(config-if)#sw mode access
SW1(config-if)#sw ac vlan 10
SW1(config)#int f0/3
SW1(config-if)#sw mode access
SW1(config-if)#sw ac vlan 20
```
