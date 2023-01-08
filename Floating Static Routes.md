### Floating Static Routes
- A floating static route is used as a backup route. It has a manually configured Administrative distance at the end of the command ip route.

##### Network Topology
<img src="https://user-images.githubusercontent.com/95317911/211174749-3689c4c0-41d5-4437-ace3-9329689dfdcc.PNG" width="80%" height="80%">

##### Configuring Floating Static Routes on R1 and R2 that allow PC1 to reach SRV1 if the link between R1 and R2 fails

```
R1#conf t
R1(config)#ip route 10.0.2.0 255.255.255.0 203.0.113.1 111

R2#config t
R2(config)#ip route 10.0.1.0 255.255.255.0 203.0.113.5 111
```




