### STP

##### Network Topology

<img width="360" alt="25-2 STP Configuration" src="https://user-images.githubusercontent.com/95317911/211137402-a59cc41e-1e58-435c-b80a-cc549740d1ba.PNG">

##### Goal
- Configure the network so traffic between the PCs and the Internet travels along the shortest available path. If a switch fails, traffic should failover to the next shortest available path.

##### Configuration
```
CD1(config)#spanning-tree vlan 10 root primary 
CD2(config)#spanning-tree vlan 10 root secondary 

Acc3(config)#int f0/1
Acc3(config-if)#spanning-tree portfast
Acc3(config-if)#spanning-tree bpduguard enable

Acc4(config)#int f0/1
Acc4(config-if)#spanning-tree portfast
Acc4(config-if)#spanning-tree bpduguard enable

CD1(config)#int g0/1
CD1(config-if)#spanning-tree portfast
CD1(config-if)#spanning-tree bpduguard enable

CD2(config)#int f0/1
CD2(config-if)#spanning-tree portfast
CD2(config-if)#spanning-tree bpduguard enable
```
