### EtherChannel

##### Network Topology

<img src="https://user-images.githubusercontent.com/95317911/211138785-8e621c20-1bc3-4a9e-8465-5a1172d85963.PNG" width="50%" height="50%">


##### Configuring Layer 2 Etherchannel between ASW1 and DSW1 using LACP
- Modes for LACP are: Active/Passive 
```
ASW1

ASW1>en
ASW1#config t
AWS1(config)#int g0/1
AWS1(config-if)#switchport mode trunk
AWS1(config-if)#channel-group 1 mode active
AWS1(config)#int g0/2
AWS1(config-if)#switchport mode trunk
AWS1(config-if)#channel-group 1 mode active


DSW1
DSW1>en
DSW1#config t
DWS1(config)#int range g1/0/3-4
DWS1(config-if)#switchport mode trunk
DWS1(config-if)#channel-group 1 mode active
```


##### Configuring Layer 2 Etherchannel between ASW2 and DSW2 using PAgP
- PAgP Modes: Auto/Desirable 
```
ASW2

ASW2>en
ASW2#config t
AWS2(config)#int range g0/1-2
AWS2(config-if)#switchport mode trunk
AWS2(config-if)#channel-group 1 mode auto

DSW2
DSW2>en
DSW2#config t
DWS2(config)#int range g1/0/3-4
DWS2(config-if)#switchport mode trunk
DWS2(config-if)#channel-group 1 mode auto
```

##### Configuring Layer 2 Etherchannel between DSW1 and DSW2 using Static EtherChannel
- To manually configure an EtherChannel is by using the ON mode
```
DSW1

DSW1>en
DSW1#config t
DWS1(config)#int g1/0/2
DWS1(config-if)#switchport mode trunk
DWS1(config-if)#channel-group 1 mode on

DSW2
DSW2>en
DSW2#config t
DWS2(config)#int g1/0/2
DWS2(config-if)#switchport mode trunk
DWS2(config-if)#channel-group 1 mode on
```

##### Configuring routes to allow the PCs to reach SRV1
```


```

