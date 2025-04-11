### 1. Топология сети:
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab05/VxLAN.JPG)

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
   Необходимо настроить eBGP на underlay и overlay, запустить VxLAN с EVPN. После настройки необходимо подключить к разным VTEP PC и проверить их доступность с других PC в фабрике. 
   
   
   Для underlay: 
   - соединить по схеме интерфейсы
   - ip адреса должны соответствовать схеме
   - используем интерфейсы Lo 0 и интерфейсы подключенные к Spine добавляем их в eBGP
   - мы будем ананонсировать подсети
   - для настройки будем использовать разные AS
  
   Для overlay: 
   - соединить по схеме интерфейсы
   - ip адреса должны соответствовать схеме
   - используем ip адреса интерфейсов подключенных к Spine добавляем их в eBGP
   - мы будем ананонсировать разные подсети
   - для настройки будем использовать разные AS
   - создаем VxLAN1 и прописываем vni, rd, rt, evpn

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001
   
ip routing

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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   !
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.11/32
end
```
Leaf512
```
hostname leaf512

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001

ip routing
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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.12/32
end
```
Leaf513
```
hostname leaf513

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001

ip routing
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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.13/32

end
```
Leaf514
```
hostname leaf514

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001

ip routing
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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.14/32

end
```
Leaf515
```
hostname leaf515

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001

ip routing

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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.15/32

end
```
Leaf516
```
hostname leaf516

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001

ip routing

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
 
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      vlan 1

    address-family evpn
      neighbor OVERLAY activate
   !
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.16/32
end
```
Leaf517
```
hostname leaf517

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001

ip routing
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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.17/32
end
```
Leaf518
```
hostname leaf518

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
   vxlan vlan 1 vni 1010001

interface Loopback0
   ip address 10.255.5.18/32

ip routing

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
   
   vlan-aware-bundle lan
      rd 10.255.5.11:101
      route-target both 65500:101
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.18/32
end
```
Leaf519
```
hostname leaf519

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001

ip routing
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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.19/32
end
```
Leaf520
```
hostname leaf520

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001

ip routing
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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.20/32

end
```
Leaf521
```
hostname leaf521

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001

ip routing
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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.21/32
end
```
Leaf522
```
hostname leaf522

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

interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 1 vni 1010001


ip routing

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
      vlan 1

   address-family evpn
      neighbor OVERLAY activate
   
   address-family ipv4
      neighbor UNDERLAY activate
      network 10.255.5.22/32
end
```   
### 3. Доступность коммутаторов в underlay и overlay:

``` 
spine501#show bgp summary 
BGP summary information for VRF default
Router identifier 10.255.5.1, local AS number 65500
Neighbor              AS Session State AFI/SAFI                AFI/SAFI State   NLRI Rcd   NLRI Acc
------------ ----------- ------------- ----------------------- -------------- ---------- ----------
10.254.15.2        65511 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.6        65512 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.10       65513 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.14       65514 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.18       65515 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.22       65516 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.26       65517 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.30       65518 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.34       65519 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.38       65520 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.42       65521 Established   IPv4 Unicast            Negotiated              1          1
10.254.15.46       65522 Established   IPv4 Unicast            Negotiated              1          1
10.255.5.11        65511 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.12        65512 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.13        65513 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.14        65514 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.15        65515 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.16        65516 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.17        65517 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.18        65518 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.19        65519 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.20        65520 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.21        65521 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.22        65522 Established   L2VPN EVPN              Negotiated              2          2

spine501#show bgp ipv4 unicast 
BGP routing table information for VRF default
Router identifier 10.255.5.1, local AS number 65500
Route status codes: s - suppressed contributor, * - valid, > - active, E - ECMP head, e - ECMP
                    S - Stale, c - Contributing to ECMP, b - backup, L - labeled-unicast
                    % - Pending best path selection
Origin codes: i - IGP, e - EGP, ? - incomplete
RPKI Origin Validation codes: V - valid, I - invalid, U - unknown
AS Path Attributes: Or-ID - Originator ID, C-LST - Cluster List, LL Nexthop - Link Local Nexthop

          Network                Next Hop              Metric  AIGP       LocPref Weight  Path
 * >      10.255.5.1/32          -                     -       -          -       0       i
 * >      10.255.5.11/32         10.254.15.2           0       -          100     0       65511 i
 * >      10.255.5.12/32         10.254.15.6           0       -          100     0       65512 i
 * >      10.255.5.13/32         10.254.15.10          0       -          100     0       65513 i
 * >      10.255.5.14/32         10.254.15.14          0       -          100     0       65514 i
 * >      10.255.5.15/32         10.254.15.18          0       -          100     0       65515 i
 * >      10.255.5.16/32         10.254.15.22          0       -          100     0       65516 i
 * >      10.255.5.17/32         10.254.15.26          0       -          100     0       65517 i
 * >      10.255.5.18/32         10.254.15.30          0       -          100     0       65518 i
 * >      10.255.5.19/32         10.254.15.34          0       -          100     0       65519 i
 * >      10.255.5.20/32         10.254.15.38          0       -          100     0       65520 i
 * >      10.255.5.21/32         10.254.15.42          0       -          100     0       65521 i
 * >      10.255.5.22/32         10.254.15.46          0       -          100     0       65522 i
spine501#show ip route bgp 

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

 B E      10.255.5.11/32 [200/0]
           via 10.254.15.2, Ethernet1
 B E      10.255.5.12/32 [200/0]
           via 10.254.15.6, Ethernet2
 B E      10.255.5.13/32 [200/0]
           via 10.254.15.10, Ethernet3
 B E      10.255.5.14/32 [200/0]
           via 10.254.15.14, Ethernet4
 B E      10.255.5.15/32 [200/0]
           via 10.254.15.18, Ethernet5
 B E      10.255.5.16/32 [200/0]
           via 10.254.15.22, Ethernet6
 B E      10.255.5.17/32 [200/0]
           via 10.254.15.26, Ethernet7
 B E      10.255.5.18/32 [200/0]
           via 10.254.15.30, Ethernet8
 B E      10.255.5.19/32 [200/0]
           via 10.254.15.34, Ethernet9
 B E      10.255.5.20/32 [200/0]
           via 10.254.15.38, Ethernet10
 B E      10.255.5.21/32 [200/0]
           via 10.254.15.42, Ethernet11
 B E      10.255.5.22/32 [200/0]
           via 10.254.15.46, Ethernet12

spine501#ping 10.255.5.1
PING 10.255.5.1 (10.255.5.1) 72(100) bytes of data.
80 bytes from 10.255.5.1: icmp_seq=1 ttl=64 time=0.909 ms
80 bytes from 10.255.5.1: icmp_seq=2 ttl=64 time=0.029 ms
80 bytes from 10.255.5.1: icmp_seq=3 ttl=64 time=0.012 ms
80 bytes from 10.255.5.1: icmp_seq=4 ttl=64 time=0.011 ms
80 bytes from 10.255.5.1: icmp_seq=5 ttl=64 time=0.012 ms

--- 10.255.5.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4ms
rtt min/avg/max/mdev = 0.011/0.194/0.909/0.357 ms, ipg/ewma 1.077/0.539 ms
spine501#ping 10.255.5.13
PING 10.255.5.13 (10.255.5.13) 72(100) bytes of data.
80 bytes from 10.255.5.13: icmp_seq=1 ttl=64 time=3.75 ms
80 bytes from 10.255.5.13: icmp_seq=2 ttl=64 time=1.39 ms
80 bytes from 10.255.5.13: icmp_seq=3 ttl=64 time=1.47 ms
80 bytes from 10.255.5.13: icmp_seq=4 ttl=64 time=1.24 ms
80 bytes from 10.255.5.13: icmp_seq=5 ttl=64 time=1.64 ms

--- 10.255.5.13 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 13ms
rtt min/avg/max/mdev = 1.242/1.898/3.750/0.934 ms, ipg/ewma 3.369/2.796 ms
spine501#ping 10.254.15.29
PING 10.254.15.29 (10.254.15.29) 72(100) bytes of data.
80 bytes from 10.254.15.29: icmp_seq=1 ttl=64 time=0.263 ms
80 bytes from 10.254.15.29: icmp_seq=2 ttl=64 time=0.015 ms
80 bytes from 10.254.15.29: icmp_seq=3 ttl=64 time=0.013 ms
80 bytes from 10.254.15.29: icmp_seq=4 ttl=64 time=0.012 ms
80 bytes from 10.254.15.29: icmp_seq=5 ttl=64 time=0.014 ms

--- 10.254.15.29 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3ms
rtt min/avg/max/mdev = 0.012/0.063/0.263/0.099 ms, ipg/ewma 0.687/0.159 ms

leaf511#ping 10.255.5.18 source loopback 0
PING 10.255.5.18 (10.255.5.18) from 10.255.5.11 : 72(100) bytes of data.
80 bytes from 10.255.5.18: icmp_seq=1 ttl=63 time=8.42 ms
80 bytes from 10.255.5.18: icmp_seq=2 ttl=63 time=2.97 ms
80 bytes from 10.255.5.18: icmp_seq=3 ttl=63 time=2.48 ms
80 bytes from 10.255.5.18: icmp_seq=4 ttl=63 time=2.57 ms
80 bytes from 10.255.5.18: icmp_seq=5 ttl=63 time=2.57 ms

--- 10.255.5.18 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 31ms
rtt min/avg/max/mdev = 2.480/3.801/8.421/2.315 ms, ipg/ewma 7.692/6.024 ms

leaf511#show bgp summary 
BGP summary information for VRF default
Router identifier 10.255.5.11, local AS number 65511
Neighbor             AS Session State AFI/SAFI                AFI/SAFI State   NLRI Rcd   NLRI Acc
----------- ----------- ------------- ----------------------- -------------- ---------- ----------
10.254.15.1       65500 Established   IPv4 Unicast            Negotiated             12         12
10.254.16.1       65500 Established   IPv4 Unicast            Negotiated             12         12
10.255.5.1        65500 Established   L2VPN EVPN              Negotiated             22         22
10.255.5.2        65500 Established   L2VPN EVPN              Negotiated             22         22

spine502#show bgp summary 
BGP summary information for VRF default
Router identifier 10.255.5.2, local AS number 65500
Neighbor              AS Session State AFI/SAFI                AFI/SAFI State   NLRI Rcd   NLRI Acc
------------ ----------- ------------- ----------------------- -------------- ---------- ----------
10.254.16.2        65511 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.6        65512 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.10       65513 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.14       65514 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.18       65515 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.22       65516 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.26       65517 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.30       65518 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.34       65519 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.38       65520 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.42       65521 Established   IPv4 Unicast            Negotiated              1          1
10.254.16.46       65522 Established   IPv4 Unicast            Negotiated              1          1
10.255.5.11        65511 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.12        65512 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.13        65513 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.14        65514 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.15        65515 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.16        65516 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.17        65517 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.18        65518 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.19        65519 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.20        65520 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.21        65521 Established   L2VPN EVPN              Negotiated              2          2
10.255.5.22        65522 Established   L2VPN EVPN              Negotiated              2          2

spine502#show bgp evpn 
BGP routing table information for VRF default
Router identifier 10.255.5.2, local AS number 65500
Route status codes: * - valid, > - active, S - Stale, E - ECMP head, e - ECMP
                    c - Contributing to ECMP, % - Pending best path selection
Origin codes: i - IGP, e - EGP, ? - incomplete
AS Path Attributes: Or-ID - Originator ID, C-LST - Cluster List, LL Nexthop - Link Local Nexthop

          Network                Next Hop              Metric  LocPref Weight  Path
 * >      RD: 10.255.5.11:101 imet 1010001 10.255.5.11
                                 10.255.5.11           -       100     0       65511 i
 * >      RD: 10.255.5.12:101 imet 1010001 10.255.5.12
                                 10.255.5.12           -       100     0       65512 i
 * >      RD: 10.255.5.13:101 imet 1010001 10.255.5.13
                                 10.255.5.13           -       100     0       65513 i
 * >      RD: 10.255.5.14:101 imet 1010001 10.255.5.14
                                 10.255.5.14           -       100     0       65514 i
 * >      RD: 10.255.5.15:101 imet 1010001 10.255.5.15
                                 10.255.5.15           -       100     0       65515 i
 * >      RD: 10.255.5.16:101 imet 1010001 10.255.5.16
                                 10.255.5.16           -       100     0       65516 i
 * >      RD: 10.255.5.17:101 imet 1010001 10.255.5.17
                                 10.255.5.17           -       100     0       65517 i
 * >      RD: 10.255.5.18:101 imet 1010001 10.255.5.18
                                 10.255.5.18           -       100     0       65518 i
 * >      RD: 10.255.5.19:101 imet 1010001 10.255.5.19
                                 10.255.5.19           -       100     0       65519 i
 * >      RD: 10.255.5.20:101 imet 1010001 10.255.5.20
                                 10.255.5.20           -       100     0       65520 i
 * >      RD: 10.255.5.21:101 imet 1010001 10.255.5.21
                                 10.255.5.21           -       100     0       65521 i
 * >      RD: 10.255.5.22:101 imet 1010001 10.255.5.22
                                 10.255.5.22           -       100     0       65522 i
 * >      RD: 10.255.5.11:101 imet 1010002 10.255.5.11
                                 10.255.5.11           -       100     0       65511 i
 * >      RD: 10.255.5.12:101 imet 1010002 10.255.5.12
                                 10.255.5.12           -       100     0       65512 i
 * >      RD: 10.255.5.13:101 imet 1010002 10.255.5.13
                                 10.255.5.13           -       100     0       65513 i
 * >      RD: 10.255.5.14:101 imet 1010002 10.255.5.14
                                 10.255.5.14           -       100     0       65514 i
 * >      RD: 10.255.5.15:101 imet 1010002 10.255.5.15
                                 10.255.5.15           -       100     0       65515 i
 * >      RD: 10.255.5.16:101 imet 1010002 10.255.5.16
                                 10.255.5.16           -       100     0       65516 i
 * >      RD: 10.255.5.17:101 imet 1010002 10.255.5.17
                                 10.255.5.17           -       100     0       65517 i
 * >      RD: 10.255.5.18:101 imet 1010002 10.255.5.18
                                 10.255.5.18           -       100     0       65518 i
 * >      RD: 10.255.5.19:101 imet 1010002 10.255.5.19
                                 10.255.5.19           -       100     0       65519 i
 * >      RD: 10.255.5.20:101 imet 1010002 10.255.5.20
                                 10.255.5.20           -       100     0       65520 i
 * >      RD: 10.255.5.21:101 imet 1010002 10.255.5.21
                                 10.255.5.21           -       100     0       65521 i
 * >      RD: 10.255.5.22:101 imet 1010002 10.255.5.22
                                 10.255.5.22           -       100     0       65522 i

``` 
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab05/PC.JPG)
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab05/PC1.JPG)
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab05/PC2.JPG)
![Схема](https://github.com/AnvarIbrag/otus-VxLAN/blob/main/labs/lab05/PC3.JPG)
