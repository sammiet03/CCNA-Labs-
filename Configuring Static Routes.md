### Configuring Static Routes

### Network Topology
<img src="https://user-images.githubusercontent.com/95317911/211111873-9f1da1fd-96cc-4785-9708-2c7ce39b4dd5.PNG" width="50%" height="50%">

### Configuration

##### Configuring hostnames, IP addresses, etc.
SW1
```
Switch>enable
Switch#config t
Switch(config)#hostname SW1
SW1(config)#
```

SW2
```
Switch>enable
Switch#config t
Switch(config)#hostname SW2
SW2(config)#
```


R1
```
Router>enable
Router#config t
Router(config)#hostname R1
R1(config)#int g0/1
R1(config-if)#ip add 192.168.1.254 255.255.255.0
R1(config-if)#no shut
R1(config)#int g0/0
R1(config-if)#ip add 192.168.12.1 255.255.255.0
R1(config-if)#no shut
```

R2
```
Router>enable
Router#config t
Router(config)#hostname R2
R2(config)#int g0/0
R2(config-if)#ip add 192.168.12.2 255.255.255.0
R2(config-if)#no shut
R2(config)#int g0/1
R2(config-if)#ip add 192.168.13.2 255.255.255.0
R2(config-if)#no shut
```

R3
```
Router>enable
Router#config t
Router(config)#hostname R3
R3(config)#int g0/0
R3(config-if)#ip add 192.168.13.3 255.255.255.0
R3(config-if)#no shut
R3(config)#int g0/1
R3(config-if)#ip add 192.168.3.254 255.255.255.0
R3(config-if)#no shut
```

##### Configuring static routes on the router to enable PC1 to successfully ping PC2
R1
```
R1#config t
R1(config)#ip route 192.168.13.0 255.255.255.0 192.168.12.2
R1(config)#ip route 192.168.3.0 255.255.255.0 192.168.12.2
```

R2
```
R2#config t
R2(config)#ip route 192.168.3.0 255.255.255.0 192.168.13.3
R2(config)#ip route 192.168.1.0 255.255.255.0 192.168.12.1
```

R3
```
R3#config t
R3(config)#ip route 192.168.12.0 255.255.255.0 192.168.13.2
R3(config)#ip route 192.168.1.0 255.255.255.0 192.168.13.2
```
