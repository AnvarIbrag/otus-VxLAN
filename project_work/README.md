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

### 3. План работ:
   Необходимо разместить двух "клиентов" в разных VRF в рамках одной фабрики. Настроите маршрутизацию между клиентами через внешнее устройство (граничный роутер\фаерволл\etc). 
      
   Для overlay: 
   - соединить по схеме интерфейсы
   - ip адреса должны соответствовать схеме
   - используем ip адреса интерфейсов подключенных к Spine добавляем их в eBGP
   - настроить на двух пк разные подсети и привязать их в разные vlan
   - настроить новую vrf
   - создать новый vlan
   - добавить внешнее устрово маршрутизации
   - подключить его к Leaf518
   - создать на leaf518 два новых vlan (под каждую vrf в vxlan), добавить адресацию из подсети /29, привязать новые vlan к интерфейсам
   - на маршрутизируемом уст-ве провести аналогичные leaf518 настройки
   - на leaf 518 и "маршрутизаторе" настраиваем сессии BGP и снимаем ограничения на транслирование маршрутов с собственной AS.
   - проверяем маршрутизацию между vrf.
   
   

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
```   

### 3. Доступность пк в разных vrf:

``` 
lleaf511#show ip route vrf anycast 

VRF: anycast
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

Gateway of last resort is not set

 B E      1.1.1.1/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.5.0.49/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.5.0.0/24 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.255.5.16/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.255.5.18/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.255.5.19/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 C        192.168.0.0/24
           directly connected, Vlan3
 B E      192.168.1.69/32 [200/0]
           via VTEP 10.255.5.12 VNI 2550002 router-mac 50:00:00:ca:26:23 local-interface Vxlan1
           via VTEP 10.255.5.13 VNI 2550002 router-mac 50:00:00:9d:e9:64 local-interface Vxlan1
 C        192.168.1.0/24
           directly connected, Vlan2


leaf516#show ip route vrf anycast 

VRF: anycast
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

Gateway of last resort is not set

 B E      1.1.1.1/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.5.0.49/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.5.0.0/24 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.255.5.16/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.255.5.18/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.255.5.19/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550002 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      192.168.0.68/32 [200/0]
           via VTEP 10.255.5.11 VNI 2550002 router-mac 50:00:00:d9:60:88 local-interface Vxlan1
 C        192.168.0.0/24
           directly connected, Vlan3
 B E      192.168.1.69/32 [200/0]
           via VTEP 10.255.5.12 VNI 2550002 router-mac 50:00:00:ca:26:23 local-interface Vxlan1
           via VTEP 10.255.5.13 VNI 2550002 router-mac 50:00:00:9d:e9:64 local-interface Vxlan1
 C        192.168.1.0/24
           directly connected, Vlan2

leaf516#show ip route vrf servers 

VRF: servers
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

Gateway of last resort is not set

 B E      1.1.1.1/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550001 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 C        10.5.0.0/24
           directly connected, Vlan4
 C        10.255.5.16/32
           directly connected, Loopback1
 B E      10.255.5.18/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550001 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      10.255.5.19/32 [200/0]
           via VTEP 10.255.5.19 VNI 2550001 router-mac 50:00:00:29:5c:f6 local-interface Vxlan1
 B E      192.168.0.68/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550001 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      192.168.0.0/24 [200/0]
           via VTEP 10.255.5.18 VNI 2550001 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      192.168.1.69/32 [200/0]
           via VTEP 10.255.5.18 VNI 2550001 router-mac 50:00:00:23:58:17 local-interface Vxlan1
 B E      192.168.1.0/24 [200/0]
           via VTEP 10.255.5.18 VNI 2550001 router-mac 50:00:00:23:58:17 local-interface Vxlan1


R1#show ip route bgp 

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

 B E      10.5.0.49/32 [200/0]
           via 10.250.50.2, Vlan200
 B E      10.5.0.0/24 [200/0]
           via 10.250.50.2, Vlan200
 B E      10.255.5.16/32 [200/0]
           via 10.250.50.2, Vlan200
 B E      10.255.5.18/32 [200/0]
           via 10.250.50.2, Vlan200
 B E      10.255.5.19/32 [200/0]
           via 10.250.50.2, Vlan200
 B E      192.168.0.68/32 [200/0]
           via 10.250.60.2, Vlan300
 B E      192.168.0.0/24 [200/0]
           via 10.250.60.2, Vlan300
 B E      192.168.1.69/32 [200/0]
           via 10.250.60.2, Vlan300
 B E      192.168.1.0/24 [200/0]
           via 10.250.60.2, Vlan300

leaf518#show bgp evpn route-type mac-ip 
BGP routing table information for VRF default
Router identifier 10.255.5.18, local AS number 65518
Route status codes: * - valid, > - active, S - Stale, E - ECMP head, e - ECMP
                    c - Contributing to ECMP, % - Pending best path selection
Origin codes: i - IGP, e - EGP, ? - incomplete
AS Path Attributes: Or-ID - Originator ID, C-LST - Cluster List, LL Nexthop - Link Local Nexthop

          Network                Next Hop              Metric  LocPref Weight  Path
 * >Ec    RD: 10.255.5.16:25504 mac-ip 5000.002b.0000
                                 10.255.5.16           -       100     0       65500 65516 i
 *  ec    RD: 10.255.5.16:25504 mac-ip 5000.002b.0000
                                 10.255.5.16           -       100     0       65500 65516 i
 * >Ec    RD: 10.255.5.16:25504 mac-ip 5000.002b.0000 10.5.0.49
                                 10.255.5.16           -       100     0       65500 65516 i
 *  ec    RD: 10.255.5.16:25504 mac-ip 5000.002b.0000 10.5.0.49
                                 10.255.5.16           -       100     0       65500 65516 i
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
 * >Ec    RD: 10.255.5.21:101 mac-ip 1010002 5000.005a.0001
                                 10.255.5.21           -       100     0       65500 65521 i
 *  ec    RD: 10.255.5.21:101 mac-ip 1010002 5000.005a.0001
                                 10.255.5.21           -       100     0       65500 65521 i
 * >Ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000
                                 10.255.5.11           -       100     0       65500 65511 i
 *  ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000
                                 10.255.5.11           -       100     0       65500 65511 i
 * >Ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000 192.168.0.68
                                 10.255.5.11           -       100     0       65500 65511 i
 *  ec    RD: 10.255.5.11:101 mac-ip 1010003 5000.0058.0000 192.168.0.68
                                 10.255.5.11           -       100     0       65500 65511 i

``` 
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab08/PC1_anycast.JPG)

![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab08/PC2.JPG)

![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab08/PC1_anycast2.JPG)
