### 1. Топология сети:
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab01/%D0%A1%D1%85%D0%B5%D0%BC%D0%B0.JPG)

### 2.Распределение адресного пространства:
### Адреса для интерфейсов Lo overlay:
|Device|Ip-address
|---|---|
|Spine501| 10.255.5.1/32|
|Spine502| 10.255.5.2/32|
|Leaf511| 10.255.5.11/32|
|Leaf512| 10.255.5.12/32|
|Leaf513| 10.255.5.13/32|
|Leaf514| 10.255.5.14/32|
|Leaf515| 10.255.5.15/32|
|Leaf516| 10.255.5.16/32|
|Leaf517| 10.255.5.17/32|
|Leaf518| 10.255.5.18/32|
|Leaf519| 10.255.5.19/32|
|Leaf520| 10.255.5.20/32|
|Leaf521| 10.255.5.21/32|
|Leaf522| 10.255.5.22/32|

### Адреса для интерфейсов UnderLay:
|Device|Port|Ip-address|---|Device|Port|Ip-address
|---|---|---|---|---|---|---|
|Spine501| Eth1| 10.254.15.1/30| < ---> |Leaf511| Eth49| 10.254.15.2/30|
|Spine502| Eth1| 10.254.16.1/30| < ---> |Leaf511| Eth50|1 0.254.16.2/30|
|Spine501| Eth2| 10.254.15.5/30| < ---> |Leaf512| Eth49| 10.254.15.6/30|
|Spine502| Eth2| 10.254.16.5/30| < ---> |Leaf512| Eth50| 10.254.16.6/30|
|Spine501| Eth3| 10.254.15.9/30| < ---> |Leaf513| Eth49| 10.254.15.10/30|
|Spine502| Eth3| 10.254.16.9/30| < ---> |Leaf513| Eth50| 10.254.16.10/30|
|Spine501| Eth4| 10.254.15.13/30| < ---> |Leaf514| Eth49| 10.254.15.14/30|
|Spine502| Eth4| 10.254.16.13/30| < ---> |Leaf514| Eth50| 10.254.16.14/30|
|Spine501| Eth5| 10.254.15.17/30| < ---> |Leaf515| Eth49| 10.254.15.18/30|
|Spine502| Eth5| 10.254.16.17/30| < ---> |Leaf515| Eth50| 10.254.16.18/30|
|Spine501| Eth6| 10.254.15.21/30| < ---> |Leaf516| Eth49| 10.254.15.22/30|
|Spine502| Eth6| 10.254.16.21/30| < ---> |Leaf516| Eth50| 10.254.16.22/30|
|Spine501| Eth7| 10.254.15.25/30| < ---> |Leaf517| Eth49| 10.254.15.26/30|
|Spine502| Eth7| 10.254.16.25/30| < ---> |Leaf517| Eth50| 10.254.16.26/30|
|Spine501| Eth8| 10.254.15.29/30| < ---> |Leaf518| Eth49| 10.254.15.30/30|
|Spine502| Eth8| 10.254.16.29/30| < ---> |Leaf518| Eth50| 10.254.16.30/30|
|Spine501| Eth9| 10.254.15.33/30| < ---> |Leaf519| Eth49| 10.254.15.34/30|
|Spine502| Eth9| 10.254.16.33/30| < ---> |Leaf519| Eth50| 10.254.16.34/30|
|Spine501| Eth10| 10.254.15.37/30| < ---> |Leaf520| Eth49| 10.254.15.38/30|
|Spine502| Eth10| 10.254.16.37/30| < ---> |Leaf520| Eth50| 10.254.16.38/30|
|Spine501| Eth11| 10.254.15.41/30| < ---> |Leaf521| Eth49| 10.254.15.42/30|
|Spine502| Eth11| 10.254.16.41/30| < ---> |Leaf521| Eth50| 10.254.16.42/30|
|Spine501| Eth12| 10.254.15.45/30| < ---> |Leaf522| Eth49| 10.254.15.46/30|
|Spine502| Eth12| 10.254.16.45/30| < ---> |Leaf522| Eth50| 10.254.16.46/30|

### 3. План работ:
   Необходимо соединить интерфейсы Leaf и Spine коммутаторов с помощью технологии ISIS. Для полносты  тестов созданной сети, необходимо настроить ISIS на underlay уровне VxLAN. Так как у нас не большая сеть будем использовать level-1. 
   
   
   Для underlay: 
   - соединить по схеме интерфейсы
   - ip адреса должны соответствовать схеме
   - используем интерфейсы Lo 0 и интерфейсы подключенные к Spine добавляем их в isis
   - мы будем ананонсировать не ip адреса, а интерфейсы
   - для настроики используем level-1

Конфигурации устройств:
```
   Spine501:
   
   hostname spine501
   aaa authorization exec default local
   router isis 500
   net 49.0001.0001.0000.0001.00
   router-id ipv4 10.255.5.1
   is-type level-1
   address-family ipv4 unicast

interface Ethernet1
   description ->leaf511
   no switchport
   ip address 10.254.15.1/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet2
   description ->leaf512
   no switchport
   ip address 10.254.15.5/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet3
   description ->leaf513
   no switchport
   ip address 10.254.15.9/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet4
   description ->leaf1414
   no switchport
   ip address 10.254.15.13/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet5
   description ->leaf515
   no switchport
   ip address 10.254.15.17/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet6
   description ->leaf516
   no switchport
   ip address 10.254.15.21/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet7
   description ->leaf518
   no switchport
   ip address 10.254.15.25/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet8
   description ->leaf519
   no switchport
   ip address 10.254.15.29/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet9
   description ->leaf519
   no switchport
   ip address 10.254.15.33/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet10
   description ->leaf520
   no switchport
   ip address 10.254.15.37/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet11
   description ->leaf521
   no switchport
   ip address 10.254.15.41/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet12
   description ->leaf522
   no switchport
   ip address 10.254.15.45/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.1/32
   isis enable 500
   isis bfd
   isis network point-to-point

ip routing
end
```
Spine502
```
hostname spine502

aaa authorization exec default local
router isis 500
   net 49.0001.0001.0000.0002.00
   router-id ipv4 10.255.5.2
   is-type level-1
   address-family ipv4 unicast

interface Ethernet1
   description ->leaf511
   no switchport
   ip address 10.254.16.1/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet2
   description ->leaf512
   no switchport
   ip address 10.254.16.5/30
   isis enable 500
   isis bfd
   isis network point-to-point


interface Ethernet3
   description ->leaf513
   no switchport
   ip address 10.254.16.9/30
   isis enable 500
   isis bfd
   isis network point-to-point


interface Ethernet4
   description ->leaf514
   no switchport
   ip address 10.254.16.13/30
   isis enable 500
   isis bfd
   isis network point-to-point


interface Ethernet5
   description ->leaf515
   no switchport
   ip address 10.254.16.17/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet6
   description ->leaf516
   no switchport
   ip address 10.254.16.21/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet7
   description ->leaf517
   no switchport
   ip address 10.254.16.25/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet8
   description ->leaf518
   no switchport
   ip address 10.254.16.29/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet9
   description ->leaf519
   no switchport
   ip address 10.254.16.33/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet10
   description ->leaf520
   no switchport
   ip address 10.254.16.37/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet11
   description ->leaf521
   no switchport
   ip address 10.254.16.41/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet12
   description ->leaf522
   no switchport
   ip address 10.254.16.45/30
   isis enable 500
   isis bfd
   isis network point-to-point

   
interface Loopback0
   ip address 10.255.5.2/32
   isis enable 500
   isis bfd
   isis network point-to-point

ip routing
end
```
Leaf511
```
hostname leaf511

router isis 500
   net 49.0001.0001.0000.1001.00
   router-id ipv4 10.255.5.11
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.2/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.2/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.11/32
    isis enable 500
   isis bfd
   isis network point-to-point
ip routing

end
```
Leaf512
```
hostname leaf512

router isis 500
   net 49.0001.0001.0000.1002.00
   router-id ipv4 10.255.5.12
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.6/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.6/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.12/32
   isis enable 500
   isis bfd
   isis network point-to-point
ip routing
end
```
Leaf513
```
hostname leaf513

router isis 500
   net 49.0001.0001.0000.1003.00
   router-id ipv4 10.255.5.13
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.10/30
     isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.10/30
    isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.13/32
    isis enable 500
   isis bfd
   isis network point-to-point
ip routing
end
```
Leaf514
```
hostname leaf514

router isis 500
   net 49.0001.0001.0000.1004.00
   router-id ipv4 10.255.5.14
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.14/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.14/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.14/32
   isis enable 500
   isis bfd
   isis network point-to-point

ip routing

end
```
Leaf515
```
hostname leaf515

router isis 500
   net 49.0001.0001.0000.1005.00
   router-id ipv4 10.255.5.15
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.18/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.18/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.15/32
   isis enable 500
   isis bfd
   isis network point-to-point

ip routing

end
```
Leaf516
```
hostname leaf516

router isis 500
   net 49.0001.0001.0000.1006.00
   router-id ipv4 10.255.5.16
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.22/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.22/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.16/32
   isis enable 500
   isis bfd
   isis network point-to-point
ip routing
end
```
Leaf517
```
hostname leaf517

router isis 500
   net 49.0001.0001.0000.1007.00
   router-id ipv4 10.255.5.17
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.26/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.26/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.17/32
   isis enable 500
   isis bfd
   isis network point-to-point
ip routing

end
```
Leaf518
```
hostname leaf518

router isis 500
   net 49.0001.0001.0000.1008.00
   router-id ipv4 10.255.5.18
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.30/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.30/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.18/32
   isis enable 500
   isis bfd
   isis network point-to-point
ip routing
end
```
Leaf519
```
hostname leaf519

router isis 500
   net 49.0001.0001.0000.1009.00
   router-id ipv4 10.255.5.19
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.34/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.34/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.19/32
    isis enable 500
   isis bfd
   isis network point-to-point
ip routing
end
```
Leaf520
```
hostname leaf520

router isis 500
   net 49.0001.0001.0000.1010.00
   router-id ipv4 10.255.5.20
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.38/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.38/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.20/32
   isis enable 500
   isis bfd
   isis network point-to-point
ip routing

end
```
Leaf521
```
hostname leaf521

router isis 500
   net 49.0001.0001.0000.1011.00
   router-id ipv4 10.255.5.21
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.42/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.42/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.21/32
    isis enable 500
   isis bfd
   isis network point-to-point

ip routing
end
```
Leaf522
```
hostname leaf522

router isis 500
   net 49.0001.0001.0000.1012.00
   router-id ipv4 10.255.5.22
   is-type level-1
   address-family ipv4 unicast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.46/30
   isis enable 500
   isis bfd
   isis network point-to-point

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.46/30
    isis enable 500
   isis bfd
   isis network point-to-point

interface Loopback0
   ip address 10.255.5.22/32
   isis enable 500
   isis bfd
   isis network point-to-point

ip routing

end
```   
### 3. Доступность коммутаторов в underlay и overlay:

``` 
spine501#show isis neighbors 
 
Instance  VRF      System Id        Type Interface          SNPA              State Hold time   Circuit Id          
500       default  leaf511          L1   Ethernet1          P2P               UP    27          50                  
500       default  leaf512          L1   Ethernet2          P2P               UP    28          56                  
500       default  leaf513          L1   Ethernet3          P2P               UP    24          5E                  
500       default  leaf514          L1   Ethernet4          P2P               UP    24          6F                  
500       default  leaf515          L1   Ethernet5          P2P               UP    23          5B                  
500       default  leaf516          L1   Ethernet6          P2P               UP    27          56                  
500       default  leaf517          L1   Ethernet7          P2P               UP    25          53                  
500       default  leaf518          L1   Ethernet8          P2P               UP    23          48                  
500       default  leaf519          L1   Ethernet9          P2P               UP    21          55                  
500       default  leaf520          L1   Ethernet10         P2P               UP    27          57                  
500       default  leaf521          L1   Ethernet11         P2P               UP    29          60                  
500       default  Leaf522          L1   Ethernet12         P2P               UP    29          43              

spine501#show isis database 
Legend:
H - hostname conflict
U - node unreachable

IS-IS Instance: 500 VRF: default
  IS-IS Level 1 Link State Database
    LSPID                   Seq Num  Cksum  Life Length IS  Received LSPID        Flags
    spine501.00-00              259  40138  1086    364 L1  0001.0000.0001.00-00  <>
    spine502.00-00              250  54143  1086    364 L1  0001.0000.0002.00-00  <>
    leaf511.00-00                94  47031  1085    123 L1  0001.0000.1001.00-00  <>
    leaf512.00-00                88  12081  1086    123 L1  0001.0000.1002.00-00  <>
    leaf513.00-00               145   7158  1193    123 L1  0001.0000.1003.00-00  <>
    leaf514.00-00                88  64059  1085    123 L1  0001.0000.1004.00-00  <>
    leaf515.00-00                77  34724  1086    123 L1  0001.0000.1005.00-00  <>
    leaf516.00-00                77  58673  1085    123 L1  0001.0000.1006.00-00  <>
    leaf517.00-00                76  21423  1122    123 L1  0001.0000.1007.00-00  <>
    leaf518.00-00                80  46643  1085    123 L1  0001.0000.1008.00-00  <>
    leaf519.00-00                74  12458  1085    123 L1  0001.0000.1009.00-00  <>
    leaf520.00-00                75  32329  1086    123 L1  0001.0000.1010.00-00  <>
    leaf521.00-00                79  58314  1085    123 L1  0001.0000.1011.00-00  <>
    Leaf522.00-00                72  21867  1179    123 L1  0001.0000.1012.00-00  <>

spine501#show ip route isis 

VRF: default
Source Codes:
       C - connected, S - static, K - kernel,
       O - OSPF, IA - OSPF inter area, E1 - OSPF external type 1,
       E2 - OSPF external type 2, N1 - OSPF NSSA external type 1,
       N2 - OSPF NSSA external type2, B - Other BGP Routes,
       B I - iBGP, B E - eBGP, R - RIP, I L1 - IS-IS level 1,
       I L2 - IS-IS level 2, O3 - OSPFv3, A B - BGP Aggregate,
       A O - OSPF Summary, NG - Nexthop Group Static Route,
       V - VXLAN Control Service, M - Martian,
       DH - DHCP client installed default route,
       DP - Dynamic Policy Route, L - VRF Leaked,
       G  - gRIBI, RC - Route Cache Route,
       CL - CBF Leaked Route

 I L1     10.254.16.0/30 [115/20]
           via 10.254.15.2, Ethernet1
 I L1     10.254.16.4/30 [115/20]
           via 10.254.15.6, Ethernet2
 I L1     10.254.16.8/30 [115/20]
           via 10.254.15.10, Ethernet3
 I L1     10.254.16.12/30 [115/20]
           via 10.254.15.14, Ethernet4
 I L1     10.254.16.16/30 [115/20]
           via 10.254.15.18, Ethernet5
 I L1     10.254.16.20/30 [115/20]
           via 10.254.15.22, Ethernet6
 I L1     10.254.16.24/30 [115/20]
           via 10.254.15.26, Ethernet7
 I L1     10.254.16.28/30 [115/20]
           via 10.254.15.30, Ethernet8
 I L1     10.254.16.32/30 [115/20]
           via 10.254.15.34, Ethernet9
 I L1     10.254.16.36/30 [115/20]
           via 10.254.15.38, Ethernet10
 I L1     10.254.16.40/30 [115/20]
           via 10.254.15.42, Ethernet11
 I L1     10.254.16.44/30 [115/20]
           via 10.254.15.46, Ethernet12
 I L1     10.255.5.2/32 [115/30]
           via 10.254.15.2, Ethernet1
           via 10.254.15.6, Ethernet2
           via 10.254.15.10, Ethernet3
           via 10.254.15.14, Ethernet4
           via 10.254.15.18, Ethernet5
           via 10.254.15.22, Ethernet6
           via 10.254.15.26, Ethernet7
           via 10.254.15.30, Ethernet8
           via 10.254.15.34, Ethernet9
           via 10.254.15.38, Ethernet10
           via 10.254.15.42, Ethernet11
           via 10.254.15.46, Ethernet12
 I L1     10.255.5.11/32 [115/20]
           via 10.254.15.2, Ethernet1
 I L1     10.255.5.12/32 [115/20]
           via 10.254.15.6, Ethernet2
 I L1     10.255.5.13/32 [115/20]
           via 10.254.15.10, Ethernet3
 I L1     10.255.5.14/32 [115/20]
           via 10.254.15.14, Ethernet4
 I L1     10.255.5.15/32 [115/20]
           via 10.254.15.18, Ethernet5
 I L1     10.255.5.16/32 [115/20]
           via 10.254.15.22, Ethernet6
 I L1     10.255.5.17/32 [115/20]
           via 10.254.15.26, Ethernet7
 I L1     10.255.5.18/32 [115/20]
           via 10.254.15.30, Ethernet8
 I L1     10.255.5.19/32 [115/20]
           via 10.254.15.34, Ethernet9
 I L1     10.255.5.20/32 [115/20]
           via 10.254.15.38, Ethernet10
 I L1     10.255.5.21/32 [115/20]
           via 10.254.15.42, Ethernet11
 I L1     10.255.5.22/32 [115/20]
           via 10.254.15.46, Ethernet12

spine501#show isis network topology level-1

IS-IS Instance: 500 VRF: default
  IS-IS paths to level-1 routers
    System Id        Metric   IA Metric Next-Hop         Interface                SNPA             
    spine502         20       0         leaf511          Ethernet1                P2P              
                                        leaf512          Ethernet2                P2P              
                                        leaf513          Ethernet3                P2P              
                                        leaf514          Ethernet4                P2P              
                                        leaf515          Ethernet5                P2P              
                                        leaf516          Ethernet6                P2P              
                                        leaf517          Ethernet7                P2P              
                                        leaf518          Ethernet8                P2P              
                                        leaf519          Ethernet9                P2P              
                                        leaf520          Ethernet10               P2P              
                                        leaf521          Ethernet11               P2P              
                                        Leaf522          Ethernet12               P2P              
    leaf511          10       0         leaf511          Ethernet1                P2P              
    leaf512          10       0         leaf512          Ethernet2                P2P              
    leaf513          10       0         leaf513          Ethernet3                P2P              
    leaf514          10       0         leaf514          Ethernet4                P2P              
    leaf515          10       0         leaf515          Ethernet5                P2P              
    leaf516          10       0         leaf516          Ethernet6                P2P              
    leaf517          10       0         leaf517          Ethernet7                P2P              
    leaf518          10       0         leaf518          Ethernet8                P2P              
    leaf519          10       0         leaf519          Ethernet9                P2P              
    leaf520          10       0         leaf520          Ethernet10               P2P              
    leaf521          10       0         leaf521          Ethernet11               P2P              
    Leaf522          10       0         Leaf522          Ethernet12               P2P              
spine501#show isis network topology ldp-tunneling 

IS-IS Instance: 500 VRF: default
  IS-IS paths to level-1 routers
    System Id        Metric   IA Metric Next-Hop         Interface                SNPA             
``` 
