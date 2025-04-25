### 1. Топология сети:
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab07/VxLAN.JPG)

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
   Необходимо разместить двух "клиентов" в разных VRF в рамках одной фабрики. Настроите маршрутизацию между клиентами через внешнее устройство (граничный роутер\фаерволл\etc). 
      
   Для overlay: 
   - соединить по схеме интерфейсы
   - ip адреса должны соответствовать схеме
   - используем ip адреса интерфейсов подключенных к Spine добавляем их в eBGP
   - настроить на двух пк разные подсети и привязать их в разные vlan
   - настроить новую vrf
   - создать новый vlan
   - настроить дополнительный lo
   - добавить новые интерфейсы в vxlan
   
   

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
      network 10.0.0.0/30
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
   name internal   

vlan 4

vrf instance anycast
vrf instance servers

interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.30/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.30/30

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 2 vni 1010002
   vxlan vlan 3 vni 1010003
   vxlan vlan 4 vni 2550004
   vxlan vrf anycast vni 2550002
   vxlan vrf servers vni 2550001

interface Loopback0
   ip address 10.255.5.18/32

interface Loopback1
   vrf servers
   ip address 10.255.5.18/32

interface Vlan2
   vrf anycast
   ip address virtual 192.168.1.1/24
   
interface Vlan3
   vrf anycast
   ip address virtual 192.168.0.1/24

interface Vlan4
   vrf servers
   ip address virtual 10.0.0.1/30

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
      rd 10.255.5.11:101
      route-target both 65500:101
      redistribute learned
      vlan 2-3

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.18/32

   vrf anycast
      rd 10.255.5.11:25502
      route-target import evpn 65500:25502
      route-target export evpn 65500:25502
      network 192.168.0.0/24
      network 192.168.1.0/24

   vrf servers
      rd 10.255.5.18:25501
      route-target import evpn 65500:25501
      route-target export evpn 65500:25501
      network 10.0.0.0/30
      network 10.5.0.0/24
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
### 3. Доступность пк в разных vrf:

``` 
leaf516#show arp vrf servers 
Address         Age (sec)  Hardware Addr   Interface
10.0.0.2                -  5000.0052.0000  Vlan4, Vxlan1
leaf516#show arp vrf anycast 
Address         Age (sec)  Hardware Addr   Interface
192.168.1.68      3:23:55  5000.005a.0001  Vlan2, not learned
192.168.1.69            -  5000.0033.0001  Vlan2, Vxlan1
192.168.0.68            -  5000.0058.0000  Vlan3, Vxlan1
192.168.0.69      3:18:21  5000.005f.0000  Vlan3, Vxlan1
192.168.0.100           -  5000.0052.0000  Vlan3, Vxlan1
leaf516#show mac address-table vlan 4
          Mac Address Table
------------------------------------------------------------------

Vlan    Mac Address       Type        Ports      Moves   Last Move
----    -----------       ----        -----      -----   ---------
   4    0000.0000.0001    STATIC      Cpu
   4    5000.0001.0001    DYNAMIC     Vx1        1       0:01:17 ago
   4    5000.002b.0000    DYNAMIC     Et13       1       0:04:20 ago
   4    5000.0052.0000    DYNAMIC     Vx1        1       1 day, 0:52:41 ago
Total Mac Addresses for this criterion: 4

          Multicast Mac Address Table
------------------------------------------------------------------

Vlan    Mac Address       Type        Ports
----    -----------       ----        -----
Total Mac Addresses for this criterion: 0

leaf516#show mac address-table dynamic 
          Mac Address Table
------------------------------------------------------------------

Vlan    Mac Address       Type        Ports      Moves   Last Move
----    -----------       ----        -----      -----   ---------
   2    5000.0033.0001    DYNAMIC     Vx1        1       0:01:33 ago
   2    5000.0052.0000    DYNAMIC     Vx1        1       1 day, 0:53:08 ago
   3    5000.0052.0000    DYNAMIC     Vx1        1       1 day, 0:53:06 ago
   3    5000.0058.0000    DYNAMIC     Vx1        1       0:02:21 ago
   3    5000.005f.0000    DYNAMIC     Vx1        1       0:05:13 ago
   4    5000.0001.0001    DYNAMIC     Vx1        1       0:01:39 ago
   4    5000.002b.0000    DYNAMIC     Et13       1       0:04:43 ago
   4    5000.0052.0000    DYNAMIC     Vx1        1       1 day, 0:53:04 ago
Total Mac Addresses for this criterion: 8

          Multicast Mac Address Table
------------------------------------------------------------------

Vlan    Mac Address       Type        Ports
----    -----------       ----        -----
Total Mac Addresses for this criterion: 0
leaf516#show bgp evpn route-type mac-ip 
BGP routing table information for VRF default
Router identifier 10.255.5.16, local AS number 65516
Route status codes: * - valid, > - active, S - Stale, E - ECMP head, e - ECMP
                    c - Contributing to ECMP, % - Pending best path selection
Origin codes: i - IGP, e - EGP, ? - incomplete
AS Path Attributes: Or-ID - Originator ID, C-LST - Cluster List, LL Nexthop - Link Local Nexthop

          Network                Next Hop              Metric  LocPref Weight  Path
 * >Ec    RD: 10.255.5.18:25504 mac-ip 5000.0001.0001
                                 10.255.5.18           -       100     0       65500 65518 i
 *  ec    RD: 10.255.5.18:25504 mac-ip 5000.0001.0001
                                 10.255.5.18           -       100     0       65500 65518 i
 * >      RD: 10.255.5.16:25504 mac-ip 5000.002b.0000
                                 -                     -       -       0       i
 * >Ec    RD: 10.255.5.18:25504 mac-ip 5000.0052.0000
                                 10.255.5.18           -       100     0       65500 65518 i
 *  ec    RD: 10.255.5.18:25504 mac-ip 5000.0052.0000
                                 10.255.5.18           -       100     0       65500 65518 i
 * >Ec    RD: 10.255.5.18:25504 mac-ip 5000.0052.0000 10.0.0.2
                                 10.255.5.18           -       100     0       65500 65518 i
 *  ec    RD: 10.255.5.18:25504 mac-ip 5000.0052.0000 10.0.0.2
                                 10.255.5.18           -       100     0       65500 65518 i
 * >Ec    RD: 10.255.5.13:101 mac-ip 1010002 5000.0033.0001
                                 10.255.5.13           -       100     0       65500 65513 i
 *  ec    RD: 10.255.5.13:101 mac-ip 1010002 5000.0033.0001
                                 10.255.5.13           -       100     0       65500 65513 i
 * >Ec    RD: 10.255.5.12:101 mac-ip 1010002 5000.0033.0001 192.168.1.69
                                 10.255.5.12           -       100     0       65500 65512 i
 *  ec    RD: 10.255.5.12:101 mac-ip 1010002 5000.0033.0001 192.168.1.69
                                 10.255.5.12           -       100     0       65500 65512 i
 * >Ec    RD: 10.255.5.13:101 mac-ip 1010002 5000.0033.0001 192.168.1.69
                                 10.255.5.13           -       100     0       65500 65513 i
 *  ec    RD: 10.255.5.13:101 mac-ip 1010002 5000.0033.0001 192.168.1.69
                                 10.255.5.13           -       100     0       65500 65513 i
 * >Ec    RD: 10.255.5.18:101 mac-ip 1010002 5000.0052.0000
                                 10.255.5.18           -       100     0       65500 65518 i
 *  ec    RD: 10.255.5.18:101 mac-ip 1010002 5000.0052.0000
                                 10.255.5.18           -       100     0       65500 65518 i
 * >Ec    RD: 10.255.5.18:101 mac-ip 1010003 5000.0052.0000
                                 10.255.5.18           -       100     0       65500 65518 i
 *  ec    RD: 10.255.5.18:101 mac-ip 1010003 5000.0052.0000
                                 10.255.5.18           -       100     0       65500 65518 i
 * >Ec    RD: 10.255.5.18:101 mac-ip 1010003 5000.0052.0000 192.168.0.100
                                 10.255.5.18           -       100     0       65500 65518 i
 *  ec    RD: 10.255.5.18:101 mac-ip 1010003 5000.0052.0000 192.168.0.100
                                 10.255.5.18           -       100     0       65500 65518 i
 * >Ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000
                                 10.255.5.11           -       100     0       65500 65511 i
 *  ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000
                                 10.255.5.11           -       100     0       65500 65511 i
 * >Ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000 192.168.0.68
                                 10.255.5.11           -       100     0       65500 65511 i
 *  ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000 192.168.0.68
                                 10.255.5.11           -       100     0       65500 65511 i
 * >Ec    RD: 10.255.5.15:101 mac-ip 1010003 5000.005f.0000
                                 10.255.5.15           -       100     0       65500 65515 i
 *  ec    RD: 10.255.5.15:101 mac-ip 1010003 5000.005f.0000
                                 10.255.5.15           -       100     0       65500 65515 i



leaf518#show arp vrf servers
Address         Age (sec)  Hardware Addr   Interface
10.0.0.2          0:01:27  5000.0052.0000  Vlan4, Ethernet15
leaf518#show arp vrf anycast 
Address         Age (sec)  Hardware Addr   Interface
192.168.1.68      3:28:39  5000.005a.0001  Vlan2, Vxlan1
192.168.1.69            -  5000.0033.0001  Vlan2, Vxlan1
192.168.0.68            -  5000.0058.0000  Vlan3, Vxlan1
192.168.0.69      0:03:09  5000.005f.0000  Vlan3, Vxlan1
192.168.0.100     2:51:12  5000.0052.0000  Vlan3, Ethernet15
leaf518#show mac address-table dynamic
          Mac Address Table
------------------------------------------------------------------

Vlan    Mac Address       Type        Ports      Moves   Last Move
----    -----------       ----        -----      -----   ---------
   2    5000.0033.0001    DYNAMIC     Vx1        1       0:04:57 ago
   2    5000.0052.0000    DYNAMIC     Et15       1       1 day, 0:56:32 ago
   2    5000.005a.0001    DYNAMIC     Vx1        1       0:01:34 ago
   3    5000.0052.0000    DYNAMIC     Et15       1       1 day, 0:56:30 ago
   3    5000.0058.0000    DYNAMIC     Vx1        1       0:05:45 ago
   3    5000.005f.0000    DYNAMIC     Vx1        1       0:08:37 ago
   4    5000.0001.0001    DYNAMIC     Et15       1       0:05:03 ago
   4    5000.002b.0000    DYNAMIC     Vx1        1       0:08:06 ago
   4    5000.0052.0000    DYNAMIC     Et15       1       1 day, 0:56:28 ago
4094    5000.0029.5cf6    DYNAMIC     Vx1        1       1 day, 3:30:59 ago
4094    5000.00bf.7e4d    DYNAMIC     Vx1        1       1 day, 3:14:58 ago
Total Mac Addresses for this criterion: 11

          Multicast Mac Address Table
------------------------------------------------------------------

Vlan    Mac Address       Type        Ports
----    -----------       ----        -----
Total Mac Addresses for this criterion: 0

leaf518#show bgp evpn route-type mac-ip
BGP routing table information for VRF default
Router identifier 10.255.5.18, local AS number 65518
Route status codes: * - valid, > - active, S - Stale, E - ECMP head, e - ECMP
                    c - Contributing to ECMP, % - Pending best path selection
Origin codes: i - IGP, e - EGP, ? - incomplete
AS Path Attributes: Or-ID - Originator ID, C-LST - Cluster List, LL Nexthop - Link Local Nexthop

          Network                Next Hop              Metric  LocPref Weight  Path
 * >      RD: 10.255.5.18:25504 mac-ip 5000.0001.0001
                                 -                     -       -       0       i
 * >Ec    RD: 10.255.5.16:25504 mac-ip 5000.002b.0000
                                 10.255.5.16           -       100     0       65500 65516 i
 *  ec    RD: 10.255.5.16:25504 mac-ip 5000.002b.0000
                                 10.255.5.16           -       100     0       65500 65516 i
 * >      RD: 10.255.5.18:25504 mac-ip 5000.0052.0000
                                 -                     -       -       0       i
 * >      RD: 10.255.5.18:25504 mac-ip 5000.0052.0000 10.0.0.2
                                 -                     -       -       0       i
 * >Ec    RD: 10.255.5.12:101 mac-ip 1010002 5000.0033.0001
                                 10.255.5.12           -       100     0       65500 65512 i
 *  ec    RD: 10.255.5.12:101 mac-ip 1010002 5000.0033.0001
                                 10.255.5.12           -       100     0       65500 65512 i
 * >Ec    RD: 10.255.5.13:101 mac-ip 1010002 5000.0033.0001
                                 10.255.5.13           -       100     0       65500 65513 i
 *  ec    RD: 10.255.5.13:101 mac-ip 1010002 5000.0033.0001
                                 10.255.5.13           -       100     0       65500 65513 i
 * >Ec    RD: 10.255.5.12:101 mac-ip 1010002 5000.0033.0001 192.168.1.69
                                 10.255.5.12           -       100     0       65500 65512 i
 *  ec    RD: 10.255.5.12:101 mac-ip 1010002 5000.0033.0001 192.168.1.69
                                 10.255.5.12           -       100     0       65500 65512 i
 * >Ec    RD: 10.255.5.13:101 mac-ip 1010002 5000.0033.0001 192.168.1.69
                                 10.255.5.13           -       100     0       65500 65513 i
 *  ec    RD: 10.255.5.13:101 mac-ip 1010002 5000.0033.0001 192.168.1.69
                                 10.255.5.13           -       100     0       65500 65513 i
 * >      RD: 10.255.5.18:101 mac-ip 1010002 5000.0052.0000
                                 -                     -       -       0       i
 * >Ec    RD: 10.255.5.21:101 mac-ip 1010002 5000.005a.0001
                                 10.255.5.21           -       100     0       65500 65521 i
 *  ec    RD: 10.255.5.21:101 mac-ip 1010002 5000.005a.0001
                                 10.255.5.21           -       100     0       65500 65521 i
 * >      RD: 10.255.5.18:101 mac-ip 1010003 5000.0052.0000
                                 -                     -       -       0       i
 * >      RD: 10.255.5.18:101 mac-ip 1010003 5000.0052.0000 192.168.0.100
                                 -                     -       -       0       i
 * >Ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000
                                 10.255.5.11           -       100     0       65500 65511 i
 *  ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000
                                 10.255.5.11           -       100     0       65500 65511 i
 * >Ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000 192.168.0.68
                                 10.255.5.11           -       100     0       65500 65511 i
 *  ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000 192.168.0.68
                                 10.255.5.11           -       100     0       65500 65511 i
 * >Ec    RD: 10.255.5.15:101 mac-ip 1010003 5000.005f.0000
                                 10.255.5.15           -       100     0       65500 65515 i
 *  ec    RD: 10.255.5.15:101 mac-ip 1010003 5000.005f.0000
                                 10.255.5.15           -       100     0       65500 65515 i

``` 
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab07/1.JPG)

![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab07/2.JPG)

![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab07/3.JPG)

![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab07/4.JPG)
