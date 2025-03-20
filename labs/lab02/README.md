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
   Необходимо соединить интерфейсы Leaf и Spine коммутаторов с помощью технологии OSPF. Для полносты  тестов созданной сети, необходимо настроить ospf на overlay и underlay уровнях VxLAN. Так как у нас не большая сеть будем использовать зону backbone. 
   
   
   Для underlay: 
   - соединить по схеме интерфейсы
   - ip адреса должны соответствовать схеме
   - используем интерфейсы Lo 0 и добавляем их в ospf
   - мы будем ананонсировать не ip адреса, а интерфейсы
   - для настроики используем area 100

Для overlay:
   - соединить по схеме интерфейсы
   - ip адреса должны соответствовать схеме
   - используем интерфейсы eth 49, eth50 и добавляем их в ospf
   - мы будем ананонсировать не ip адреса, а интерфейсы
   - для настроики используем area 0

Конфигурации устройств:
```
   Spine501:
   hostname spine501
   aaa authorization exec default local

interface Ethernet1
   description ->leaf511
   no switchport
   ip address 10.254.15.1/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet2
   description ->leaf512
   no switchport
   ip address 10.254.15.5/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet3
   description ->leaf513
   no switchport
   ip address 10.254.15.9/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet4
   description ->leaf1414
   no switchport
   ip address 10.254.15.13/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet5
   description ->leaf515
   no switchport
   ip address 10.254.15.17/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet6
   description ->leaf516
   no switchport
   ip address 10.254.15.21/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet7
   description ->leaf518
   no switchport
   ip address 10.254.15.25/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet8
   description ->leaf519
   no switchport
   ip address 10.254.15.29/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet9
   description ->leaf519
   no switchport
   ip address 10.254.15.33/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet10
   description ->leaf520
   no switchport
   ip address 10.254.15.37/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet11
   description ->leaf521
   no switchport
   ip address 10.254.15.41/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet12
   description ->leaf522
   no switchport
   ip address 10.254.15.45/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.1/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet1
   no passive-interface Ethernet2
   no passive-interface Ethernet3
   no passive-interface Ethernet4
   no passive-interface Ethernet5
   no passive-interface Ethernet6
   no passive-interface Ethernet7
   no passive-interface Ethernet8
   no passive-interface Ethernet9
   no passive-interface Ethernet10
   no passive-interface Ethernet11
   no passive-interface Ethernet12
   max-lsa 12000

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
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet2
   description ->leaf512
   no switchport
   ip address 10.254.16.5/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet3
   description ->leaf513
   no switchport
   ip address 10.254.16.9/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet4
   description ->leaf514
   no switchport
   ip address 10.254.16.13/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet5
   description ->leaf515
   no switchport
   ip address 10.254.16.17/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet6
   description ->leaf516
   no switchport
   ip address 10.254.16.21/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet7
   description ->leaf517
   no switchport
   ip address 10.254.16.25/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet8
   description ->leaf518
   no switchport
   ip address 10.254.16.29/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet9
   description ->leaf519
   no switchport
   ip address 10.254.16.33/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet10
   description ->leaf520
   no switchport
   ip address 10.254.16.37/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet11
   description ->leaf521
   no switchport
   ip address 10.254.16.41/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet12
   description ->leaf522
   no switchport
   ip address 10.254.16.45/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
   
interface Loopback0
   ip address 10.255.5.2/32
   ip ospf area 0.0.0.0

router ospf 100
   passive-interface default
   no passive-interface Ethernet1
   no passive-interface Ethernet2
   no passive-interface Ethernet3
   no passive-interface Ethernet4
   no passive-interface Ethernet5
   no passive-interface Ethernet6
   no passive-interface Ethernet7
   no passive-interface Ethernet8
   no passive-interface Ethernet9
   no passive-interface Ethernet10
   no passive-interface Ethernet11
   no passive-interface Ethernet12
   max-lsa 12000
ip routing
end
```
Leaf511
```
hostname leaf511
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.2/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.2/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.11/32
   ip ospf area 0.0.0.0

ip routing
router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf512
```
hostname leaf512
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.6/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.6/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.12/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf513
```
hostname leaf513
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.10/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.10/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.13/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf514
```
hostname leaf514
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.14/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.14/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.14/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf515
```
hostname leaf515
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.18/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.18/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.15/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf516
```
hostname leaf516
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.22/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.22/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.16/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf517
```
hostname leaf517
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.26/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.26/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.17/32
    ip ospf area 0.0.0.0

   ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf518
```
hostname leaf518
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.30/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.30/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.18/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

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
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf520
```
hostname leaf520
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.38/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.38/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.20/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf521
```
hostname leaf521
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.42/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.42/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.21/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```
Leaf522
```
hostname leaf522
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.46/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.46/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0

interface Loopback0
   ip address 10.255.5.22/32
   ip ospf area 0.0.0.0

ip routing

router ospf 100
   passive-interface default
   no passive-interface Ethernet49
   no passive-interface Ethernet50
   max-lsa 12000

end
```   
### 3. Доступность коммутаторов в underlay и overlay:

``` 
leaf511#ping 10.255.5.12 source loopback 0
PING 10.255.5.12 (10.255.5.12) from 10.255.5.11 : 72(100) bytes of data.
80 bytes from 10.255.5.12: icmp_seq=1 ttl=63 time=6.99 ms
80 bytes from 10.255.5.12: icmp_seq=2 ttl=63 time=5.27 ms
80 bytes from 10.255.5.12: icmp_seq=3 ttl=63 time=3.52 ms
80 bytes from 10.255.5.12: icmp_seq=4 ttl=63 time=3.91 ms
80 bytes from 10.255.5.12: icmp_seq=5 ttl=63 time=3.73 ms

--- 10.255.5.12 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 26ms
rtt min/avg/max/mdev = 3.521/4.683/6.992/1.307 ms, ipg/ewma 6.554/5.770 ms

leaf511#ping 10.255.5.13 source loopback 0
PING 10.255.5.13 (10.255.5.13) from 10.255.5.11 : 72(100) bytes of data.
80 bytes from 10.255.5.13: icmp_seq=1 ttl=63 time=5.90 ms
80 bytes from 10.255.5.13: icmp_seq=2 ttl=63 time=3.90 ms
80 bytes from 10.255.5.13: icmp_seq=3 ttl=63 time=3.27 ms
80 bytes from 10.255.5.13: icmp_seq=4 ttl=63 time=3.34 ms
80 bytes from 10.255.5.13: icmp_seq=5 ttl=63 time=3.77 ms

--- 10.255.5.13 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 22ms
rtt min/avg/max/mdev = 3.274/4.036/5.898/0.961 ms, ipg/ewma 5.525/4.933 ms

leaf511#ping 10.255.5.14 source loopback 0
PING 10.255.5.14 (10.255.5.14) from 10.255.5.11 : 72(100) bytes of data.
80 bytes from 10.255.5.14: icmp_seq=1 ttl=63 time=5.55 ms
80 bytes from 10.255.5.14: icmp_seq=2 ttl=63 time=4.03 ms
80 bytes from 10.255.5.14: icmp_seq=3 ttl=63 time=4.61 ms
80 bytes from 10.255.5.14: icmp_seq=4 ttl=63 time=3.87 ms
80 bytes from 10.255.5.14: icmp_seq=5 ttl=63 time=3.75 ms

--- 10.255.5.14 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 21ms
rtt min/avg/max/mdev = 3.745/4.361/5.553/0.665 ms, ipg/ewma 5.251/4.925 ms

leaf511#ping 10.254.16.33
PING 10.254.16.33 (10.254.16.33) 72(100) bytes of data.
80 bytes from 10.254.16.33: icmp_seq=1 ttl=64 time=3.57 ms
80 bytes from 10.254.16.33: icmp_seq=2 ttl=64 time=1.96 ms
80 bytes from 10.254.16.33: icmp_seq=3 ttl=64 time=2.00 ms
80 bytes from 10.254.16.33: icmp_seq=4 ttl=64 time=1.84 ms
80 bytes from 10.254.16.33: icmp_seq=5 ttl=64 time=1.86 ms

--- 10.254.16.33 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 13ms
rtt min/avg/max/mdev = 1.836/2.243/3.567/0.664 ms, ipg/ewma 3.251/2.879 ms
leaf511#ping 10.254.16.25
PING 10.254.16.25 (10.254.16.25) 72(100) bytes of data.
80 bytes from 10.254.16.25: icmp_seq=1 ttl=64 time=3.43 ms
80 bytes from 10.254.16.25: icmp_seq=2 ttl=64 time=2.11 ms
80 bytes from 10.254.16.25: icmp_seq=3 ttl=64 time=2.09 ms
80 bytes from 10.254.16.25: icmp_seq=4 ttl=64 time=1.98 ms
80 bytes from 10.254.16.25: icmp_seq=5 ttl=64 time=1.88 ms

--- 10.254.16.25 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 13ms
rtt min/avg/max/mdev = 1.879/2.297/3.429/0.571 ms, ipg/ewma 3.145/2.838 ms
``` 
