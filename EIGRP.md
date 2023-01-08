### EIGRP

##### Network Topology
<img src="https://user-images.githubusercontent.com/95317911/211174934-8275ba37-b405-4bf3-9eae-2aa29ee9e60b.PNG" width="80%" height="80%">

##### Configuring appropriate hostnames and IP addresses on each device. Enabling router interfaces
```
R1
Router>en
Router#config t
Router(config)#hostname R1
R1(config)#int g0/0
R1(config-if)#ip add 10.0.12.1 255.255.255.252
R1(config-if)#no shut
R1(config-if)#int f1/0
R1(config-if)#ip add 10.0.13.1 255.255.252
R1(config-if)#no shut

R2
Router>en
Router#config t
Router(config)#hostname R2
R2(config)#int g0/0
R2(config-if)#ip add 10.0.12.2 255.255.255.252
R2(config-if)#no shut
R2(config-if)#int f1/0
R2(config-if)#ip add 10.0.24.1 255.255.252
R2(config-if)#no shut


R3
Router>en
Router#config t
Router(config)#hostname R3
R3(config)#int f1/0
R3(config-if)#ip add 10.0.13.2 255.255.255.252
R3(config-if)#no shut
R3(config-if)#int f2/0
R3(config-if)#ip add 10.0.34.1 255.255.255.252
R3(config-if)#no shut

R4
Router>en
Router#config t
Router(config)#hostname R4
R4(config)#int f1/0
R4(config-if)#ip add 10.0.24.2 255.255.255.252
R4(config-if)#no shut
R4(config-if)#int f2/0
R4(config-if)#ip add 10.0.34.2 255.255.252
R4(config-if)#no shut
```

##### Configure a loopback interface on each router
```
R1
R1#config t
R1(config)#int loopback 0
R1(config-if)#ip add 1.1.1.1 255.255.255.255

R2
R2
R2#config t
R2(config)#int loopback 0
R2(config-if)#ip add 2.2.2.2 255.255.255.255

R3
R3
R3#config t
R3(config)#int loopback 0
R3(config-if)#ip add 3.3.3.3 255.255.255.255

R4
R4
R4#config t
R4(config)#int loopback 0
R4(config-if)#ip add 4.4.4.4 255.255.255.255
```

##### Configure EIGRP on each router
- disable auto-summary
- enable EIGRP on each interface (including loopback interfaces)
- configure passive interfaces where appropriate (including loopback interfaces)

```
R1>en
R1#config t
R1(config)#router eigrp 100 
R1(config-router)#network 10.0.12.0 0.0.0.3 
R1(config-router)#network 10.0.13.0 0.0.0.3
R1(config-router)#network 1.1.1.1 0.0.0.0
R1(config-router)#no auto-summary
R1(config-router)#passive-interface loopback 0


R2>en
R2#config t
R2(config)#router eigrp 100 
R2(config-router)#network 10.0.12.0 0.0.0.3 
R2(config-router)#network 10.0.24.0 0.0.0.3 
R2(config-router)#network 2.2.2.2 0.0.0.0 
R2(config-router)#no auto-summary
R2(config-router)#passive-interface loopback 0


R3>en
R3#config t
R3(config)#router eigrp 100 
R3(config-router)#network 10.0.13.0 0.0.0.3
R3(config-router)#network 10.0.34.0 0.0.0.3
R3(config-router)#network 3.3.3.3 0.0.0.0
R3(config-router)#no auto-summary
R3(config-router)#passive-interface loopback 0

R4>en
R4#config t
R4(config)#router eigrp 100 
R4(config-router)#network 0.0.0.0 255.255.255.255
R4(config-router)#no auto-summary
R4(config-router)#passive-interface g0/0
R4(config-router)#passive-interface loopback 0
```

##### Configuring R1 to perform unequal-cost load-balancing
```
R1>en
R1#config t
R1(config-router)#variance 2
```
