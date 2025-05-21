### 1. Топология сети:
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab08/VxLAN.JPG)

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

### Фабрика 2

|Device|Ip-address
|---|---|
|Spine401| 10.255.4.1/32|
|Spine402| 10.255.4.2/32|
|Leaf411| 10.255.4.11/32|
|Leaf412| 10.255.4.12/32|
|Leaf413| 10.255.4.13/32|
|Leaf414| 10.255.4.14/32|
|Leaf415| 10.255.4.15/32|
|Leaf416| 10.255.4.16/32|
|Leaf417| 10.255.4.17/32|
|Leaf418| 10.255.4.18/32|


### Адреса для интерфейсов UnderLay:
|Device|Port|Ip-address|---|Device|Port|Ip-address
|---|---|---|---|---|---|---|
|Spine401| Eth1| 10.254.13.1/30| < ---> |Leaf411| Eth49| 10.254.13.2/30|
|Spine402| Eth1| 10.254.14.1/30| < ---> |Leaf411| Eth50|1 0.254.16.2/30|
|Spine401| Eth2| 10.254.13.5/30| < ---> |Leaf412| Eth49| 10.254.13.6/30|
|Spine402| Eth2| 10.254.14.5/30| < ---> |Leaf412| Eth50| 10.254.14.6/30|
|Spine401| Eth3| 10.254.13.9/30| < ---> |Leaf413| Eth49| 10.254.13.10/30|
|Spine402| Eth3| 10.254.14.9/30| < ---> |Leaf413| Eth50| 10.254.14.10/30|
|Spine401| Eth4| 10.254.13.13/30| < ---> |Leaf414| Eth49| 10.254.13.14/30|
|Spine402| Eth4| 10.254.14.13/30| < ---> |Leaf414| Eth50| 10.254.14.14/30|
|Spine401| Eth5| 10.254.13.17/30| < ---> |Leaf415| Eth49| 10.254.13.18/30|
|Spine402| Eth5| 10.254.14.17/30| < ---> |Leaf415| Eth50| 10.254.14.18/30|
|Spine401| Eth6| 10.254.13.21/30| < ---> |Leaf416| Eth49| 10.254.13.22/30|
|Spine402| Eth6| 10.254.14.21/30| < ---> |Leaf416| Eth50| 10.254.14.22/30|
|Spine401| Eth7| 10.254.13.25/30| < ---> |Leaf417| Eth49| 10.254.13.26/30|
|Spine402| Eth7| 10.254.14.25/30| < ---> |Leaf417| Eth50| 10.254.14.26/30|
|Spine401| Eth8| 10.254.13.29/30| < ---> |Leaf418| Eth49| 10.254.13.30/30|
|Spine402| Eth8| 10.254.14.29/30| < ---> |Leaf418| Eth50| 10.254.14.30/30|

### 3. План работ:
   В двух дата-центрах используется трехуровневая модель сети. Необходимо разработать план перехода на сеть CLOS и в дальнейшем соединить две фабрики между собой технологией multisite. План работ:
         
   Для overlay двух фабрик: 
   - соединить по схеме интерфейсы
   - ip адреса должны соответствовать схеме
   - используем ip адреса интерфейсов подключенных к Spine добавляем их в eBGP
   - настроить настроить L3VNI Anycast gateway
   - настроить multihoming
   - создать разные vrf для разделения продуктов
   - добавить внешнее устрово маршрутизации
   - добавить к фабрике GW
   - настроить пиринг eBGP GW c Spine 
   - проверить работу ecmp, проверить маршруты которые приходят от Spine
   - настроить eBGP между GW разных фабрик
   - проверяем маршрутизацию между фабриками.
   
   

Конфигурации устройств:
```
   Spine501:
   
   hostname spine501
   aaa authorization exec default local
   
interface Ethernet1
   description ->leaf511
   no switchport
   ip address 10.254.15.1/30
   
interface Ethernet2
   description ->leaf512
   no switchport
   ip address 10.254.15.5/30
   
interface Ethernet3
   description ->leaf513
   no switchport
   ip address 10.254.15.9/30
   
interface Ethernet4
   description ->leaf1414
   no switchport
   ip address 10.254.15.13/30
   

interface Ethernet5
   description ->leaf515
   no switchport
   ip address 10.254.15.17/30
   

interface Ethernet6
   description ->leaf516
   no switchport
   ip address 10.254.15.21/30
   

interface Ethernet7
   description ->leaf518
   no switchport
   ip address 10.254.15.25/30
   

interface Ethernet8
   description ->leaf519
   no switchport
   ip address 10.254.15.29/30
   

interface Ethernet9
   description ->leaf519
   no switchport
   ip address 10.254.15.33/30
   

interface Ethernet10
   description ->leaf520
   no switchport
   ip address 10.254.15.37/30
   

interface Ethernet11
   description ->leaf521
   no switchport
   ip address 10.254.15.41/30
   

interface Ethernet12
   description ->leaf522
   no switchport
   ip address 10.254.15.45/30

interface Ethernet13
   description ->GW1
   no switchport
   ip address 10.254.15.49/30
   

interface Loopback0
   ip address 10.255.5.1/32
   
router bgp 65500
   router-id 10.255.5.1
   update wait-install
   no bgp default ipv4-unicast
   bgp listen range 10.255.5.0/24 peer-group OVERLAY peer-filter leaf-as-range
   bgp listen range 10.254.15.0/24 peer-group UNDERLAY peer-filter leaf-as-range
   neighbor OVERLAY peer group
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 5
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor OVERLAY maximum-routes 1000
   neighbor UNDERLAY peer group
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor UNDERLAY maximum-routes 100
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.1/32

ip routing
end
```
Spine502
```
hostname spine502

aaa authorization exec default local

interface Ethernet1
   description ->leaf511
   no switchport
   ip address 10.254.16.1/30

interface Ethernet2
   description ->leaf512
   no switchport
   ip address 10.254.16.5/30
 
interface Ethernet3
   description ->leaf513
   no switchport
   ip address 10.254.16.9/30
  
interface Ethernet4
   description ->leaf514
   no switchport
   ip address 10.254.16.13/30
   
interface Ethernet5
   description ->leaf515
   no switchport
   ip address 10.254.16.17/30
  
interface Ethernet6
   description ->leaf516
   no switchport
   ip address 10.254.16.21/30

interface Ethernet7
   description ->leaf517
   no switchport
   ip address 10.254.16.25/30

interface Ethernet8
   description ->leaf518
   no switchport
   ip address 10.254.16.29/30

interface Ethernet9
   description ->leaf519
   no switchport
   ip address 10.254.16.33/30

interface Ethernet10
   description ->leaf520
   no switchport
   ip address 10.254.16.37/30


interface Ethernet11
   description ->leaf521
   no switchport
   ip address 10.254.16.41/30

interface Ethernet12
   description ->leaf522
   no switchport
   ip address 10.254.16.45/30
 
interface Loopback0
   ip address 10.255.5.2/32

ip routing

router bgp 65500
   router-id 10.255.5.2
   update wait-install
   no bgp default ipv4-unicast
   bgp listen range 10.255.5.0/24 peer-group OVERLAY peer-filter leaf-as-range
   bgp listen range 10.254.16.0/24 peer-group UNDERLAY peer-filter leaf-as-range
   neighbor OVERLAY peer group
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 5
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor OVERLAY maximum-routes 1000
   neighbor UNDERLAY peer group
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor UNDERLAY maximum-routes 100
   !
   address-family evpn
      neighbor OVERLAY activate
   !
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.2/32

end
```
Leaf511
```
hostname leaf511

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Ethernet12
   switchport access vlan 2

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.2/30
   
interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.2/30
   
interface Loopback0
   ip address 10.255.5.11/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan virtual-router encapsulation mac-address 00:00:00:00:00:01
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002

ip virtual-router mac-address 00:00:00:00:00:01
   
ip routing
ip routing vrf anycast

router bgp 65511
   router-id 10.255.5.11
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor default send-community
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor 10.254.15.1 peer group UNDERLAY
   neighbor 10.254.15.1 description spine501
   neighbor 10.254.16.1 peer group UNDERLAY
   neighbor 10.254.16.1 description spine502
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine501
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine502
   
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   !
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.11/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```
Leaf512
```
hostname leaf512

interface Port-Channel3
   switchport trunk native vlan tag
   switchport trunk allowed vlan 2-3
   switchport mode trunk
   !
   evpn ethernet-segment
      identifier 0000:0000:0000:0000:1413
      route-target import 00:00:00:00:14:13
   lacp system-id 0000.0000.1413

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Ethernet12
   channel-group 3 mode active

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.6/30


interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.6/30


interface Loopback0
   ip address 10.255.5.12/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast

router bgp 65512
   router-id 10.255.5.12
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.5 peer group UNDERLAY
   neighbor 10.254.15.5 description spine501
   neighbor 10.254.16.5 peer group UNDERLAY
   neighbor 10.254.16.5 description spine502
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine501
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine502
  
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.12/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```
Leaf513
```
hostname leaf513

interface Port-Channel3
   switchport trunk native vlan tag
   switchport trunk allowed vlan 2-3
   switchport mode trunk
   !
   evpn ethernet-segment
      identifier 0000:0000:0000:0000:1413
      route-target import 00:00:00:00:14:13
   lacp system-id 0000.0000.1413

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Ethernet12
   channel-group 3 mode active

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.10/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.10/30

interface Loopback0
   ip address 10.255.5.13/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002
   
ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast

router bgp 65513
   router-id 10.255.5.13
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.9 peer group UNDERLAY
   neighbor 10.254.15.9 description spine501
   neighbor 10.254.16.9 peer group UNDERLAY
   neighbor 10.254.16.9 description spine502
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine501
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine502
 
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.13/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```
Leaf514
```
hostname leaf514

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.14/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.14/30
 
interface Loopback0
   ip address 10.255.5.14/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002
   
ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast

router bgp 65514
   router-id 10.255.5.14
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.13 peer group UNDERLAY
   neighbor 10.254.15.13 description spine501
   neighbor 10.254.16.13 peer group UNDERLAY
   neighbor 10.254.16.13 description spine502
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine501
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine502
   
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.14/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```
Leaf515
```
hostname leaf515

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Ethernet12
   switchport access vlan 2

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.18/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.18/30

interface Loopback0
   ip address 10.255.5.15/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002
   
ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast

router bgp 65515
   router-id 10.255.5.15
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.17 peer group UNDERLAY
   neighbor 10.254.15.17 description spine501
   neighbor 10.254.16.17 peer group UNDERLAY
   neighbor 10.254.16.17 description spine502
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine501
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine502
  
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.15/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```
Leaf516
```
hostname leaf516

vlan 2
   name externel

vlan 3
   name internal   

vlan 4

vrf instance anycast

vrf instance servers

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.22/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.22/30

interface Loopback0
   ip address 10.255.5.16/32

interface Loopback1
   vrf servers
   ip address 10.255.5.16/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vlan4
   vrf servers
   ip address virtual 10.0.0.1/30

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vlan 4 vni 2550004
   vxlan vrf anycast vni 2550002
   vxlan vrf servers vni 2550001
   
ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast
ip routing vrf servers

router bgp 65516
   router-id 10.255.5.16
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.21 peer group UNDERLAY
   neighbor 10.254.15.21 description spine501
   neighbor 10.254.16.21 peer group UNDERLAY
   neighbor 10.254.16.21 description spine502
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine501
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine502

   vlan 4
      rd 10.255.5.16:25504
      route-target both 65500:25504
      redistribute learned
 
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

    address-family evpn
      neighbor OVERLAY activate
   !
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.16/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

   vrf servers
      rd 10.255.5.16:25501
      route-target import evpn 65500:25501
      route-target export evpn 65500:25501
      network 10.5.0.0/24
      network 10.255.5.16/32

end
```
Leaf517
```
hostname leaf517

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Ethernet13
   switchport access vlan 3

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.26/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.26/30

interface Loopback0
   ip address 10.255.5.17/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast

router bgp 65517
   router-id 10.255.5.17
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.25 peer group UNDERLAY
   neighbor 10.254.15.25 description spine501
   neighbor 10.254.16.25 peer group UNDERLAY
   neighbor 10.254.16.25 description spine502
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine501
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine502
  
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.17/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```
Leaf518
```
hostname leaf518

vlan 2
   name externel

vlan 3
   name internel
   
vlan 200

vlan 300

vrf instance anycast

vrf instance servers

interface Ethernet11
   no switchport

interface Ethernet11.200
   encapsulation dot1q vlan 200
   vrf servers
   ip address 10.250.50.2/29

interface Ethernet11.300
   encapsulation dot1q vlan 300
   vrf anycast
   ip address 10.250.60.2/29

interface Ethernet49
   description -> spine401
   no switchport
   ip address 10.254.15.30/30

interface Ethernet50
   description spine402
   no switchport
   ip address 10.254.16.30/30

interface Loopback0
   ip address 10.255.5.18/32

interface Loopback1
   vrf servers
   ip address 10.255.5.18/32

interface Management1

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24

interface Vlan3
   description internal
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vlan4
   vrf servers
   ip address virtual 10.5.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vlan 4 vni 2550004
   vxlan vrf anycast vni 2550002
   vxlan vrf servers vni 2550001

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast
ip routing vrf servers

router bgp 65518
   router-id 10.255.5.18
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.29 peer group UNDERLAY
   neighbor 10.254.15.29 description spine401
   neighbor 10.254.16.29 peer group UNDERLAY
   neighbor 10.254.16.29 description spine402
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine401
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine402

   vlan 4
      rd 10.255.5.18:25504
      route-target both 65500:25504
      redistribute learned

   vlan-aware-bundle lan
      rd 10.255.5.18:101
      route-target both 65500:101
      redistribute learned
      redistribute igmp
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate

   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.18/32

   vrf anycast
      rd 10.255.5.18:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      neighbor 10.250.60.1 remote-as 65530
      neighbor 10.250.60.1 allowas-in 10
      !
      address-family ipv4
         neighbor 10.250.60.1 activate
         network 192.168.0.0/24
         network 192.168.1.0/24

   vrf servers
      rd 10.255.5.18:25501
      route-target import evpn 65500:25501
      route-target export evpn 65500:25501
      no bgp default ipv4-unicast
      neighbor 10.250.50.1 remote-as 65530
      neighbor 10.250.50.1 allowas-in 10
      neighbor 10.250.50.1 send-community
      !
      address-family ipv4
         neighbor 10.250.50.1 activate
         network 10.255.5.18/32

end
```
Leaf519
```
hostname leaf519

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.34/30


interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.34/30

interface Loopback0
   ip address 10.255.5.19/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast

router bgp 65519
   router-id 10.255.5.19
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.33 peer group UNDERLAY
   neighbor 10.254.15.33 description spine401
   neighbor 10.254.16.33 peer group UNDERLAY
   neighbor 10.254.16.33 description spine402
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine401
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine402
   
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.19/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```
Leaf520
```
hostname leaf520

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Port-Channel1
   switchport trunk native vlan tag
   switchport trunk allowed vlan 2-3
   switchport mode trunk
   !
   evpn ethernet-segment
      identifier 0000:0000:0000:0000:1412
      route-target import 00:00:00:00:14:12
   lacp system-id 0000.0000.1412

interface Ethernet12
   channel-group 1 mode active

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.38/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.38/30

interface Loopback0
   ip address 10.255.5.20/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast

router bgp 65520
   router-id 10.255.5.20
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.37 peer group UNDERLAY
   neighbor 10.254.15.37 description spine401
   neighbor 10.254.16.37 peer group UNDERLAY
   neighbor 10.254.16.37 description spine402
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine401
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine402

   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.20/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```
Leaf521
```
hostname leaf521

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Port-Channel1
   switchport trunk native vlan tag
   switchport trunk allowed vlan 2-3
   switchport mode trunk
   !
   evpn ethernet-segment
      identifier 0000:0000:0000:0000:1412
      route-target import 00:00:00:00:14:12
   lacp system-id 0000.0000.1412

interface Ethernet12
   channel-group 1 mode active

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.42/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.42/30
 
interface Loopback0
   ip address 10.255.5.21/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast

router bgp 65521
   router-id 10.255.5.21
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.41 peer group UNDERLAY
   neighbor 10.254.15.41 description spine401
   neighbor 10.254.16.41 peer group UNDERLAY
   neighbor 10.254.16.41 description spine402
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine401
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine402
  
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.21/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```
Leaf522
```
hostname leaf522

vlan 2
   name externel

vlan 3
   name internal   

vrf instance anycast

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.46/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.46/30

interface Loopback0
   ip address 10.255.5.22/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast

router bgp 65522
   router-id 10.255.5.22
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65500
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 yOrMEmhcEvH/dZMG/Vsi153kXS5Fe31k
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY password 7 3TMOe34NFW4PqoE/aAGaL2L3G5H/UReF
   neighbor UNDERLAY send-community
   neighbor 10.254.15.45 peer group UNDERLAY
   neighbor 10.254.15.45 description spine501
   neighbor 10.254.16.45 peer group UNDERLAY
   neighbor 10.254.16.45 description spine502
   neighbor 10.255.5.1 peer group OVERLAY
   neighbor 10.255.5.1 description spine501
   neighbor 10.255.5.2 peer group OVERLAY
   neighbor 10.255.5.2 description spine502
   
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.22/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

end
```   
R1
```
hostname R1

spanning-tree mode mstp
no spanning-tree vlan-id 1-4094

vlan 200,300

interface Ethernet1
   switchport trunk allowed vlan 200,300
   switchport mode trunk

interface Ethernet2
   switchport trunk allowed vlan 200,300
   switchport mode trunk

interface Loopback1
   ip address 1.1.1.1/32

interface Management1

interface Vlan200
   ip address 10.250.50.1/29

interface Vlan300
   ip address 10.250.60.1/29

ip routing

ip as-path regex-mode string
ip as-path access-list allow-any permit .* any

route-map allow-loop permit 10
   match as-path allow-any

router bgp 65530
   router-id 10.250.50.1
   neighbor 10.250.50.2 remote-as 65518
   neighbor 10.250.50.2 remove-private-as all replace-as
   neighbor 10.250.50.2 route-map allow-loop out
   neighbor 10.250.50.3 remote-as 65519
   neighbor 10.250.50.3 shutdown
   neighbor 10.250.50.3 remove-private-as all replace-as
   neighbor 10.250.50.3 route-map allow-loop out
   neighbor 10.250.60.2 remote-as 65518
   neighbor 10.250.60.2 remove-private-as all replace-as
   neighbor 10.250.60.2 route-map allow-loop out
   neighbor 10.250.60.3 remote-as 65519
   neighbor 10.250.60.3 shutdown
   neighbor 10.250.60.3 remove-private-as all replace-as
   neighbor 10.250.60.3 route-map allow-loop out
   network 1.1.1.1/32

end


username admin role network-admin secret 5 $1$jl2KUbXm$FdJbZdjeMNbzZpVnO4MTU/

terminal width 200
service configuration session max completed 20
service configuration session max pending 1
service configuration terminal disabled
service configuration session commit merge
service configuration session commit save startup-config

hostname GW1

vlan 2
   name externel

vlan 3
   name anycast

vrf instance anycast

vrf instance servers

interface Ethernet1
   no switchport
   ip address 10.250.20.1/30

interface Ethernet2
   no switchport
   ip address 10.250.21.1/30

interface Ethernet7
   description -> spine501
   no switchport
   ip address 10.254.15.50/30

interface Ethernet8
   description spine502
   no switchport
   ip address 10.254.16.50/30

interface Loopback0
   ip address 10.255.5.23/32


interface Management1

interface Vlan3
   description local
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 3 vni 1010003
   vxlan vrf anycast vni 2550002
   vxlan vrf servers vni 2550001

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast
ip routing vrf servers

ip prefix-list UNDERLAY-IP
   seq 10 permit 10.255.5.23/32

route-map UNDERLAY-EXPORT permit 10
   match ip address prefix-list UNDERLAY-IP

router bgp 65523
   router-id 10.255.5.23
   no bgp default ipv4-unicast
   maximum-paths 10
   neighbor DCI-OVERLAY peer group
   neighbor DCI-OVERLAY remote-as 65419
   neighbor DCI-OVERLAY update-source Loopback0
   neighbor DCI-OVERLAY ebgp-multihop 2
   neighbor DCI-OVERLAY send-community
   neighbor DCI-UNDERLAY peer group
   neighbor DCI-UNDERLAY remote-as 65419
   neighbor DCI-UNDERLAY route-map UNDERLAY-EXPORT out
   neighbor SPINE-OVERLAY peer group
   neighbor SPINE-OVERLAY remote-as 65500
   neighbor SPINE-OVERLAY update-source Loopback0
   neighbor SPINE-OVERLAY ebgp-multihop 2
   neighbor SPINE-OVERLAY password 7 /kuyiofcYniP98hEK1YHR1g0WVe1S/1x
   neighbor SPINE-OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65500
   neighbor UNDERLAY route-map UNDERLAY-EXPORT out
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor 10.250.20.2 peer group DCI-UNDERLAY
   neighbor 10.254.15.49 peer group UNDERLAY
   neighbor 10.254.16.49 peer group UNDERLAY
   neighbor 10.255.4.19 peer group DCI-OVERLAY
   neighbor 10.255.5.1 peer group SPINE-OVERLAY
   neighbor 10.255.5.2 peer group SPINE-OVERLAY
   redistribute connected route-map UNDERLAY-EXPORT
   
   vlan-aware-bundle lan
      rd 10.255.5.23:101
      route-target both 65500:101
      redistribute learned
      vlan 3
   
   address-family evpn
      neighbor DCI-OVERLAY activate
      neighbor DCI-OVERLAY domain remote
      neighbor SPINE-OVERLAY activate
      neighbor default next-hop-self received-evpn-routes route-type ip-prefix inter-domain
   
   address-family ipv4
      neighbor DCI-UNDERLAY activate
      neighbor UNDERLAY activate
      network 10.255.5.23/32
   
   vrf anycast
      rd 10.255.5.23:25502
      route-target import evpn 65400:25504
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      redistribute connected
   
   vrf servers
      rd 10.255.5.23:25501
      route-target import evpn 65500:25501
      route-target export evpn 65500:25501
      redistribute connected

end

Фабрика NYC:

hostname spine401

interface Ethernet1
   description ->leaf411
   no switchport
   ip address 10.254.13.1/30
   pim ipv4 sparse-mode

interface Ethernet2
   description ->leaf412
   no switchport
   ip address 10.254.13.5/30
   pim ipv4 sparse-mode

interface Ethernet3
   description ->leaf413
   no switchport
   ip address 10.254.13.9/30
   pim ipv4 sparse-mode

interface Ethernet4
   description ->leaf1414
   no switchport
   ip address 10.254.13.13/30
   pim ipv4 sparse-mode

interface Ethernet5
   description ->leaf415
   no switchport
   ip address 10.254.13.17/30
   pim ipv4 sparse-mode

interface Ethernet6
   description ->leaf416
   no switchport
   ip address 10.254.13.21/30
   pim ipv4 sparse-mode

interface Ethernet7
   description ->leaf418
   no switchport
   ip address 10.254.13.25/30
   pim ipv4 sparse-mode

interface Ethernet8
   description ->leaf418
   no switchport
   ip address 10.254.13.29/30
   pim ipv4 sparse-mode

interface Ethernet9
   description ->leaf419
   no switchport
   ip address 10.254.13.33/30
   pim ipv4 sparse-mode

interface Loopback0
   ip address 10.255.4.1/32

interface Management1

ip routing

router bgp 65400
   router-id 10.255.4.1
   update wait-install
   no bgp default ipv4-unicast
   bgp listen range 10.255.4.0/24 peer-group OVERLAY peer-filter leaf-as-range
   bgp listen range 10.254.13.0/24 peer-group UNDERLAY peer-filter leaf-as-range
   neighbor OVERLAY peer group
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 5
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor OVERLAY maximum-routes 1000
   neighbor UNDERLAY peer group
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor UNDERLAY maximum-routes 100
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.1/32


end

hostname spine402

interface defaults
   mtu 9192


interface Ethernet1
   description ->leaf411
   no switchport
   ip address 10.254.14.1/30
   pim ipv4 sparse-mode

interface Ethernet2
   description ->leaf412
   no switchport
   ip address 10.254.14.5/30
   pim ipv4 sparse-mode

interface Ethernet3
   description ->leaf413
   no switchport
   ip address 10.254.14.9/30
   pim ipv4 sparse-mode

interface Ethernet4
   description ->leaf414
   no switchport
   ip address 10.254.14.13/30
   pim ipv4 sparse-mode

interface Ethernet5
   description ->leaf415
   no switchport
   ip address 10.254.14.17/30
   pim ipv4 sparse-mode

interface Ethernet6
   description ->leaf416
   no switchport
   ip address 10.254.14.21/30
   pim ipv4 sparse-mode

interface Ethernet7
   description ->leaf417
   no switchport
   ip address 10.254.14.25/30
   pim ipv4 sparse-mode

interface Ethernet8
   description ->leaf418
   no switchport
   ip address 10.254.14.29/30
   pim ipv4 sparse-mode

interface Ethernet9
   description ->leaf419
   no switchport
   ip address 10.254.14.33/30
   pim ipv4 sparse-mode

interface Management1

ip routing

peer-filter leaf-as-range
   10 match as-range 65400-65499 result accept

router bgp 65400
   router-id 10.255.4.2
   update wait-install
   no bgp default ipv4-unicast
   bgp listen range 10.255.4.0/24 peer-group OVERLAY peer-filter leaf-as-range
   bgp listen range 10.254.14.0/24 peer-group UNDERLAY peer-filter leaf-as-range
   neighbor OVERLAY peer group
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 5
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor OVERLAY maximum-routes 1000
   neighbor UNDERLAY peer group
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor UNDERLAY maximum-routes 100
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.2/32


end

hostname leaf411

username admin privilege 15 role network-admin secret sha512 $6$CpTmDOk4L.g6zHCh$oQgAqx5asBynwz78ADZhCn2jWuGFmFE8bNU4Io4RyResDO07abLyfR56DHCDEFCzM/k24RbmxO4xeGmx9rq7T.

interface defaults
   mtu 9192

vlan 2
   name externel

vlan 3,255

vrf instance anycast

vrf instance anycast-right

vrf instance mgmt

aaa authorization exec default local

interface Port-Channel1
   switchport trunk native vlan tag
   switchport trunk allowed vlan 2-3,255
   switchport mode trunk
   
   evpn ethernet-segment
      identifier 0000:0000:0000:0000:1412
      route-target import 00:00:00:00:14:12
   lacp system-id 0000.0000.1412


interface Ethernet48
   channel-group 1 mode active

interface Ethernet49
   description -> spine401
   no switchport
   ip address 10.254.13.2/30

interface Ethernet50
   description spine402
   no switchport
   ip address 10.254.14.2/30

interface Loopback0
   ip address 10.255.4.11/32

interface Loopback255
   vrf mgmt
   ip address 10.255.4.11/32


interface Vlan2
   vrf anycast
   ip address virtual 192.168.11.1/24

interface Vlan3
   description local
   vrf anycast
   ip address virtual 192.168.10.1/24

interface Vlan33
   vrf anycast-right
   ip address virtual 192.168.10.1/24

interface Vlan255
   vrf mgmt
   ip address virtual 10.0.0.1/30

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vlan 33 vni 1010033
   vxlan vlan 255 vni 2550002
   vxlan vrf anycast vni 2550004
   vxlan vrf anycast-right vni 2560002
   vxlan vrf mgmt vni 2550001
   vxlan vlan 3 multicast group 225.10.10.3

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast
ip routing vrf anycast-right
ip routing vrf mgmt


router bgp 65411
   router-id 10.255.4.11
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65400
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65400
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor 10.254.13.1 peer group UNDERLAY
   neighbor 10.254.13.1 description spine401
   neighbor 10.254.14.1 peer group UNDERLAY
   neighbor 10.254.14.1 description spine402
   neighbor 10.255.4.1 peer group OVERLAY
   neighbor 10.255.4.1 description spine401
   neighbor 10.255.4.2 peer group OVERLAY
   neighbor 10.255.4.2 description spine402
   
   vlan 255
      rd 10.255.4.11:25502
      route-target both 65500:25502
      redistribute learned
   
   vlan-aware-bundle lan
      rd 10.255.4.11:101
      route-target both 65400:101
      redistribute learned
      redistribute igmp
      vlan 2-3,33
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.11/32
   
   vrf anycast
      rd 10.255.4.11:25504
      route-target import evpn 65400:25504
      route-target export evpn 65400:25504
      network 192.168.10.0/24
      network 192.168.11.0/24
   
   vrf anycast-right
      rd 10.255.4.11:25604
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65400:25604
   
   vrf mgmt
      rd 10.255.4.11:25501
      route-target import evpn 65400:25501
      route-target export evpn 65400:25501
      network 10.0.0.0/30
      network 10.255.4.11/32

end

hostname leaf412

username admin privilege 15 role network-admin secret sha512 $6$cd9uiQk11pvtXEIm$BCNrwgzIv6d2aOOOS/dOdyGtcmM4Tr6uUlVJQktlok.CZ.MmtUdeClaPN2mMtr9td.PXRYKykn7KCtnX2FDjP/

interface defaults
   mtu 9192

vlan 2
   name externel

vlan 3

vlan 255
   name mgmt

vrf instance anycast

vrf instance anycast-right

vrf instance mgmt

aaa authorization exec default local

interface Port-Channel1
   switchport trunk native vlan tag
   switchport trunk allowed vlan 2-3,255
   switchport mode trunk
   !
   evpn ethernet-segment
      identifier 0000:0000:0000:0000:1412
      route-target import 00:00:00:00:14:12
   lacp system-id 0000.0000.1412

interface Ethernet48
   channel-group 1 mode active

interface Ethernet49
   description -> spine401
   no switchport
   ip address 10.254.13.6/30

interface Ethernet50
   description spine402
   no switchport
   ip address 10.254.14.6/30

interface Loopback0
   ip address 10.255.4.12/32

interface Loopback255
   vrf mgmt
   ip address 10.255.4.12/32

interface Management1

interface Vlan2
   vrf anycast
   ip address virtual 192.168.11.1/24

interface Vlan3
   description local
   vrf anycast
   ip address virtual 192.168.10.1/24

interface Vlan33
   vrf anycast-right
   ip address virtual 192.168.10.1/24

interface Vlan255
   vrf mgmt
   ip address virtual 10.0.0.1/30

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vlan 33 vni 1010033
   vxlan vlan 255 vni 2550002
   vxlan vrf anycast vni 2550004
   vxlan vrf anycast-right vni 2560002
   vxlan vrf mgmt vni 2550001
   vxlan vlan 3 multicast group 225.10.10.3

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast
ip routing vrf anycast-right
ip routing vrf mgmt

router bgp 65412
   router-id 10.255.4.12
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65400
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65400
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor 10.254.13.5 peer group UNDERLAY
   neighbor 10.254.13.5 description spine401
   neighbor 10.254.14.5 peer group UNDERLAY
   neighbor 10.254.14.5 description spine402
   neighbor 10.255.4.1 peer group OVERLAY
   neighbor 10.255.4.1 description spine401
   neighbor 10.255.4.2 peer group OVERLAY
   neighbor 10.255.4.2 description spine402
   
   vlan 255
      rd 10.255.4.12:25502
      route-target both 65500:25502
      redistribute learned
   
   vlan-aware-bundle lan
      rd 10.255.4.12:101
      route-target both 65400:101
      redistribute learned
      redistribute igmp
      vlan 2-3,33
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.12/32
   
   vrf anycast-right
      rd 10.255.4.12:25604
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65400:25604
   
   vrf mgmt
      rd 10.255.4.12:25501
      route-target import evpn 65400:25501
      route-target export evpn 65400:25501
      network 10.0.0.0/30
      network 10.255.4.12/32

end

hostname leaf413

username admin role network-admin secret sha512 $6$dXV7XVCR/Vlag/Zo$VKgQJHGJmV2PNnQ0PGf0IOsGHPfKPTTXoWDvXZP.D6A6QXcrgxAoDA/VF6kM8dadxV8uZRyS15k/.SajT2ob4.

interface defaults
   mtu 9192

vlan 2
   name externel

vlan 3,33

vrf instance anycast-right

vrf instance mgmt

interface Ethernet17
   switchport access vlan 33

interface Ethernet48
   switchport access vlan 3

interface Ethernet49
   description -> spine401
   no switchport
   ip address 10.254.13.10/30

interface Ethernet50
   description spine402
   no switchport
   ip address 10.254.14.10/30

interface Loopback0
   ip address 10.255.4.13/32
!
interface Loopback255
   vrf mgmt
   ip address 10.255.4.13/32

interface Management1

interface Vlan2
   vrf anycast
   ip address virtual 192.168.11.1/24

interface Vlan33
   vrf anycast-right
   ip address virtual 192.168.10.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vlan 33 vni 1010033
   vxlan vrf anycast vni 2550004
   vxlan vrf anycast-right vni 2560002
   vxlan vrf mgmt vni 2550001
   vxlan vlan 3 multicast group 225.10.10.3

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast-right
ip routing vrf mgmt

router bgp 65413
   router-id 10.255.4.13
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65400
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65400
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor 10.254.13.9 peer group UNDERLAY
   neighbor 10.254.13.9 description spine401
   neighbor 10.254.14.9 peer group UNDERLAY
   neighbor 10.254.14.9 description spine402
   neighbor 10.255.4.1 peer group OVERLAY
   neighbor 10.255.4.1 description spine401
   neighbor 10.255.4.2 peer group OVERLAY
   neighbor 10.255.4.2 description spine402
   
   vlan-aware-bundle lan
      rd 10.255.4.13:101
      route-target both 65400:101
      redistribute learned
      redistribute igmp
      vlan 2-3,33
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.13/32
   
   vrf anycast-right
      rd 10.255.4.13:25604
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65400:25604
   
   vrf mgmt
      rd 10.255.4.13:25501
      route-target import evpn 65400:25501
      route-target export evpn 65400:25501
      network 10.255.4.13/32

end

hostname leaf414

username admin role network-admin secret 5 $1$jl2KUbXm$FdJbZdjeMNbzZpVnO4MTU/

interface defaults
   mtu 9192

vlan 2
   name externel

vlan 3
   name internel

vlan 33

vrf instance anycast-right

vrf instance mgmt

interface Ethernet49
   description -> spine401
   no switchport
   ip address 10.254.13.14/30

interface Ethernet50
   description spine402
   no switchport
   ip address 10.254.14.14/30

interface Loopback0
   ip address 10.255.4.14/32

interface Loopback255
   vrf mgmt
   ip address 10.255.4.14/32

interface Management1

interface Vlan2
   vrf anycast
   ip address virtual 192.168.11.1/24

interface Vlan33
   description local
   vrf anycast-right
   ip address virtual 192.168.10.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 33 vni 1010033
   vxlan vrf anycast-right vni 2560002
   vxlan vrf mgmt vni 2550001
   
ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast-right
ip routing vrf mgmt

ntp server ntp401.adcluster.targetix.net prefer

router bgp 65414
   router-id 10.255.4.14
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65400
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65400
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor 10.254.13.13 peer group UNDERLAY
   neighbor 10.254.13.13 description spine401
   neighbor 10.254.14.13 peer group UNDERLAY
   neighbor 10.254.14.13 description spine402
   neighbor 10.255.4.1 peer group OVERLAY
   neighbor 10.255.4.1 description spine401
   neighbor 10.255.4.2 peer group OVERLAY
   neighbor 10.255.4.2 description spine402
   
   vlan-aware-bundle lan
      rd 10.255.4.14:101
      route-target both 65400:101
      redistribute learned
      redistribute igmp
      vlan 2-3,33
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.14/32
   
   vrf anycast-right
      rd 10.255.4.14:25604
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65400:25604
   
   vrf mgmt
      rd 10.255.4.14:25501
      route-target import evpn 65400:25501
      route-target export evpn 65400:25501
      network 10.255.4.14/32

end

hostname leaf415

username admin role network-admin secret 5 $1$jl2KUbXm$FdJbZdjeMNbzZpVnO4MTU/

interface defaults
   mtu 9192

vlan 2
   name externel

vlan 33

vrf instance anycast-right

vrf instance mgmt

aaa authorization exec default local

interface Ethernet13
   switchport access vlan 33

interface Ethernet49
   description -> spine401
   no switchport
   ip address 10.254.13.18/30

interface Ethernet50
   description spine402
   no switchport
   ip address 10.254.14.18/30

interface Loopback0
   ip address 10.255.4.15/32
!
interface Loopback255
   vrf mgmt
   ip address 10.255.4.15/32

interface Management1

interface Vlan2
   vrf anycast
   ip address virtual 192.168.11.1/24

interface Vlan33
   vrf anycast-right
   ip address virtual 192.168.10.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 33 vni 1010033
   vxlan vrf anycast-right vni 2560002
   vxlan vrf mgmt vni 2550001
 
ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast-right
ip routing vrf mgmt

router bgp 65415
   router-id 10.255.4.15
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65400
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65400
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor 10.254.13.17 peer group UNDERLAY
   neighbor 10.254.13.17 description spine401
   neighbor 10.254.14.17 peer group UNDERLAY
   neighbor 10.254.14.17 description spine402
   neighbor 10.255.4.1 peer group OVERLAY
   neighbor 10.255.4.1 description spine401
   neighbor 10.255.4.2 peer group OVERLAY
   neighbor 10.255.4.2 description spine402
   
   vlan-aware-bundle lan
      rd 10.255.4.15:101
      route-target both 65400:101
      redistribute learned
      redistribute igmp
      vlan 2-3,33
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.15/32
   
   vrf anycast-right
      rd 10.255.4.15:25604
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65400:25604
   
   vrf mgmt
      rd 10.255.4.15:25501
      route-target import evpn 65400:25501
      route-target export evpn 65400:25501
      network 10.255.4.15/32

end

hostname leaf416

username admin role network-admin secret 5 $1$jl2KUbXm$FdJbZdjeMNbzZpVnO4MTU/

interface defaults
   mtu 9192

vlan 2
   name externel
vlan 13,33,103

vrf instance anycast-right

vrf instance mgmt

interface Ethernet49
   description -> spine401
   no switchport
   ip address 10.254.13.22/30

interface Ethernet50
   description spine402
   no switchport
   ip address 10.254.14.22/30

interface Loopback0
   ip address 10.255.4.16/32

interface Loopback255
   vrf mgmt
   ip address 10.255.4.16/32

interface Management1

interface Vlan2
   vrf anycast
   ip address virtual 192.168.11.1/24

interface Vlan33
   vrf anycast-right
   ip address virtual 192.168.10.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 33 vni 1010033
   vxlan vlan 103 vni 1010103
   vxlan vrf anycast-right vni 2560002
   vxlan vrf mgmt vni 2550001

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast
ip routing vrf anycast-right
ip routing vrf mgmt

router bgp 65416
   router-id 10.255.4.16
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65400
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY bfd
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65400
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor 10.254.13.21 peer group UNDERLAY
   neighbor 10.254.13.21 description spine401
   neighbor 10.254.14.21 peer group UNDERLAY
   neighbor 10.254.14.21 description spine402
   neighbor 10.255.4.1 peer group OVERLAY
   neighbor 10.255.4.1 description spine401
   neighbor 10.255.4.2 peer group OVERLAY
   neighbor 10.255.4.2 description spine402

    vlan-aware-bundle lan
      route-target both 65400:101
      vlan 2,33
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.16/32
   
   vrf anycast-right
      rd 10.255.4.16:25604
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65400:25604
   
   vrf mgmt
      rd 10.255.4.16:25501
      route-target import evpn 65400:25501
      route-target export evpn 65400:25501
      network 10.255.4.16/32

end

hostname leaf417

username admin role network-admin secret 5 $1$jl2KUbXm$FdJbZdjeMNbzZpVnO4MTU/

interface defaults
   mtu 9192

spanning-tree mode none
no spanning-tree vlan-id 1-4094

vlan 2
   name externel

vlan 33

vrf instance anycast-right

vrf instance mgmt

interface Ethernet49
   description -> spine401
   no switchport
   ip address 10.254.13.26/30

interface Ethernet50
   description spine402
   no switchport
   ip address 10.254.14.26/30

interface Loopback0
   ip address 10.255.4.17/32

interface Loopback255
   vrf mgmt
   ip address 10.255.4.17/32

interface Management1

interface Vlan2
   vrf anycast
   ip address virtual 192.168.11.1/24

interface Vlan33
   vrf anycast-right
   ip address virtual 192.168.10.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 33 vni 1010033
   vxlan vrf anycast-right vni 2560002
   vxlan vrf mgmt vni 2550001
   vxlan vlan 3 multicast group 225.10.10.3

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast-right
ip routing vrf mgmt

ntp server ntp401.adcluster.targetix.net prefer

router bgp 65417
   router-id 10.255.4.17
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65400
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65400
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor 10.254.13.25 peer group UNDERLAY
   neighbor 10.254.13.25 description spine401
   neighbor 10.254.14.25 peer group UNDERLAY
   neighbor 10.254.14.25 description spine402
   neighbor 10.255.4.1 peer group OVERLAY
   neighbor 10.255.4.1 description spine401
   neighbor 10.255.4.2 peer group OVERLAY
   neighbor 10.255.4.2 description spine402
   
   vlan-aware-bundle lan
      route-target both 65400:101
      redistribute learned
      redistribute igmp
      vlan 2-33
   
   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.17/32
   
   vrf anycast-right
      rd 10.255.4.17:25604
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65400:25604
   
   vrf mgmt
      rd 10.255.4.17:25501
      route-target import evpn 65400:25501
      route-target export evpn 65400:25501
      network 10.255.4.17/32

end

hostname leaf418

username admin role network-admin secret 5 $1$jl2KUbXm$FdJbZdjeMNbzZpVnO4MTU/

interface defaults
   mtu 9192

spanning-tree mode none
no spanning-tree vlan-id 1-4094

vlan 2
   name externel

vlan 33

vrf instance anycast-right

vrf instance mgmt

interface Ethernet49
   description -> spine401
   no switchport
   ip address 10.254.13.30/30

interface Ethernet50
   description spine402
   no switchport
   ip address 10.254.14.30/30

interface Loopback255
   vrf mgmt
   ip address 10.255.4.18/32

interface Management1

interface Vlan2
   vrf anycast
   ip address virtual 192.168.11.1/24

interface Vlan33
   vrf anycast-right
   ip address virtual 192.168.10.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 33 vni 1010033
   vxlan vrf anycast-right vni 2560002
   vxlan vrf mgmt vni 2550001
   vxlan vlan 3 multicast group 225.10.10.3

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast-right
ip routing vrf mgmt

router bgp 65418
   router-id 10.255.4.18
   no bgp default ipv4-unicast
   maximum-paths 2
   neighbor OVERLAY peer group
   neighbor OVERLAY remote-as 65400
   neighbor OVERLAY next-hop-unchanged
   neighbor OVERLAY update-source Loopback0
   neighbor OVERLAY ebgp-multihop 3
   neighbor OVERLAY password 7 CrtfwFdT/uN/cvuGMXN9WIXEyNe6Chm3
   neighbor OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65400
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor UNDERLAY send-community
   neighbor 10.254.13.29 peer group UNDERLAY
   neighbor 10.254.13.29 description spine401
   neighbor 10.254.14.29 peer group UNDERLAY
   neighbor 10.254.14.29 description spine402
   neighbor 10.255.4.1 peer group OVERLAY
   neighbor 10.255.4.1 description spine401
   neighbor 10.255.4.2 peer group OVERLAY
   neighbor 10.255.4.2 description spine402

   vlan-aware-bundle lan
      route-target both 65400:101
      redistribute learned
      redistribute igmp
      vlan 2,33

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.4.18/32
   
   vrf anycast-right
      rd 10.255.4.18:25604
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65400:25604
   
   vrf mgmt
      rd 10.255.4.18:25501
      route-target import evpn 65400:25501
      route-target export evpn 65400:25501
      network 10.255.4.18/32

end

hostname GW2

username admin role network-admin secret 5 $1$jl2KUbXm$FdJbZdjeMNbzZpVnO4MTU/

terminal width 200

spanning-tree mode mstp

vlan 2
   name externel

vlan 33

vrf instance anycast-right

vrf instance servers

interface Ethernet1
   no switchport
   ip address 10.250.20.2/30

interface Ethernet2
   no switchport
   ip address 10.250.21.2/30

interface Ethernet7
   description -> spine401
   no switchport
   ip address 10.254.13.34/30

interface Ethernet8
   description spine402
   no switchport
   ip address 10.254.14.34/30

interface Loopback0
   ip address 10.255.4.19/32

interface Management1

interface Vlan33
   vrf anycast-right
   ip address virtual 192.168.10.1/24

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 3 vni 1010003
   vxlan vlan 33 vni 1010033
   vxlan vrf anycast-right vni 2560002
   vxlan vrf servers vni 2550003

ip virtual-router mac-address 00:00:00:00:00:01

ip routing
ip routing vrf anycast-right
ip routing vrf servers

ip prefix-list UNDERLAY-IP
   seq 10 permit 10.255.4.19/32

route-map UNDERLAY-EXPORT permit 10
   match ip address prefix-list UNDERLAY-IP

router bgp 65419
   router-id 10.255.4.19
   no bgp default ipv4-unicast
   maximum-paths 10
   neighbor DCI-OVERLAY peer group
   neighbor DCI-OVERLAY remote-as 65523
   neighbor DCI-OVERLAY update-source Loopback0
   neighbor DCI-OVERLAY ebgp-multihop 2
   neighbor DCI-OVERLAY send-community
   neighbor DCI-UNDERLAY peer group
   neighbor DCI-UNDERLAY remote-as 65523
   neighbor DCI-UNDERLAY route-map UNDERLAY-EXPORT out
   neighbor SPINE-OVERLAY peer group
   neighbor SPINE-OVERLAY remote-as 65400
   neighbor SPINE-OVERLAY update-source Loopback0
   neighbor SPINE-OVERLAY ebgp-multihop 2
   neighbor SPINE-OVERLAY password 7 /kuyiofcYniP98hEK1YHR1g0WVe1S/1x
   neighbor SPINE-OVERLAY send-community
   neighbor UNDERLAY peer group
   neighbor UNDERLAY remote-as 65400
   neighbor UNDERLAY route-map UNDERLAY-EXPORT out
   neighbor UNDERLAY password 7 gTUCnU9RCsjTMbB+E8I1xgmqA48iX9su
   neighbor 10.250.20.1 peer group DCI-UNDERLAY
   neighbor 10.254.13.33 peer group UNDERLAY
   neighbor 10.254.14.33 peer group UNDERLAY
   neighbor 10.255.4.1 peer group SPINE-OVERLAY
   neighbor 10.255.4.2 peer group SPINE-OVERLAY
   neighbor 10.255.5.23 peer group DCI-OVERLAY
   redistribute connected route-map UNDERLAY-EXPORT
   
   vlan-aware-bundle lan
      rd 10.255.4.19:101
      route-target both 65400:101
      redistribute learned
      vlan 33
   
   address-family evpn
      neighbor DCI-OVERLAY activate
      neighbor DCI-OVERLAY domain remote
      neighbor SPINE-OVERLAY activate
      neighbor default next-hop-self received-evpn-routes route-type ip-prefix inter-domain
   
   address-family ipv4
      neighbor DCI-UNDERLAY activate
      neighbor UNDERLAY activate
      network 10.255.4.19/32
   
   vrf anycast-right
      rd 10.255.4.19:25604
      route-target import evpn 65400:25604
      route-target import evpn 65500:25502
      route-target export evpn 65400:25604
      redistribute connected
   
   vrf servers
      rd 10.255.4.19:25501
      route-target import evpn 65400:25501
      route-target export evpn 65400:25501
      redistribute connected

end

```   

### 3. Разбор основных решений и их работу:

``` 

``` 
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab08/PC1_anycast.JPG)

![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab08/PC2.JPG)

![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab08/PC1_anycast2.JPG)
