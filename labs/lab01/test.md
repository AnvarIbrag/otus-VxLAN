1. Топология сети:
![Схема](https://github.com/user-attachments/assets/2b42b5e4-ca3e-46bf-be5c-354f684afea0)
2. Распределение адресного пространства:
Адреса для интерфейсов Lo overlay:
Spine501 - 10.255.5.1/32
Spine502 - 10.255.5.2/32
Leaf511 - 10.255.5.11/32
Leaf512 - 10.255.5.12/32
Leaf513 - 10.255.5.13/32
Leaf514 - 10.255.5.14/32
Leaf515 - 10.255.5.15/32
Leaf516 - 10.255.5.16/32
Leaf517 - 10.255.5.17/32
Leaf518 - 10.255.5.18/32
Leaf519 - 10.255.5.19/32
Leaf520 - 10.255.5.20/32
Leaf521 - 10.255.5.21/32
Leaf522 - 10.255.5.22/32

Адреса для интерфейсов UnderLay:
Spine501 Eth1 - 10.254.15.1/30 < ---> Leaf511 Eth49 - 10.254.15.2/30
Spine502 Eth1 - 10.254.16.1/30 < ---> Leaf511 Eth50 - 10.254.16.2/30

Spine501 Eth2 - 10.254.15.5/30 < ---> Leaf512 Eth49 - 10.254.15.6/30
Spine502 Eth2 - 10.254.16.5/30 < ---> Leaf512 Eth50 - 10.254.16.6/30

Spine501 Eth3 - 10.254.15.9/30 < ---> Leaf513 Eth49 - 10.254.15.10/30
Spine502 Eth3 - 10.254.16.9/30 < ---> Leaf513 Eth50 - 10.254.16.10/30

Spine501 Eth4 - 10.254.15.13/30 < ---> Leaf514 Eth49 - 10.254.15.14/30
Spine502 Eth4 - 10.254.16.13/30 < ---> Leaf514 Eth50 - 10.254.16.14/30

Spine501 Eth5 - 10.254.15.17/30 < ---> Leaf515 Eth49 - 10.254.15.18/30
Spine502 Eth5 - 10.254.16.17/30 < ---> Leaf515 Eth50 - 10.254.16.18/30

Spine501 Eth6 - 10.254.15.21/30 < ---> Leaf516 Eth49 - 10.254.15.22/30
Spine502 Eth6 - 10.254.16.21/30 < ---> Leaf516 Eth50 - 10.254.16.22/30

Spine501 Eth7 - 10.254.15.25/30 < ---> Leaf517 Eth49 - 10.254.15.26/30
Spine502 Eth7 - 10.254.16.25/30 < ---> Leaf517 Eth50 - 10.254.16.26/30

Spine501 Eth8 - 10.254.15.29/30 < ---> Leaf518 Eth49 - 10.254.15.30/30
Spine502 Eth8 - 10.254.16.29/30 < ---> Leaf518 Eth50 - 10.254.16.30/30

Spine501 Eth9 - 10.254.15.33/30 < ---> Leaf519 Eth49 - 10.254.15.34/30
Spine502 Eth9 - 10.254.16.33/30 < ---> Leaf519 Eth50 - 10.254.16.34/30

Spine501 Eth10 - 10.254.15.37/30 < ---> Leaf520 Eth49 - 10.254.15.38/30
Spine502 Eth10 - 10.254.16.37/30 < ---> Leaf520 Eth50 - 10.254.16.38/30

Spine501 Eth11 - 10.254.15.41/30 < ---> Leaf521 Eth49 - 10.254.15.42/30
Spine502 Eth11 - 10.254.16.41/30 < ---> Leaf521 Eth50 - 10.254.16.42/30

Spine501 Eth12 - 10.254.15.45/30 < ---> Leaf522 Eth49 - 10.254.15.46/30
Spine502 Eth12 - 10.254.16.45/30 < ---> Leaf522 Eth50 - 10.254.16.46/30

3. План работ:
   Название всех Leaf и Spine расшифровываются следующим образом:
   Spine501:
   Spine - роль коммутатора в фабрике VxLAN
   5 - номер дата-центра
   01 - номер Spine внутри фабрики

   Leaf511:
   Leaf - роль коммутатора в фабрике VxLAN
   5 - номер дата-центра
   11 - номер Spine внутри фабрики
   В дальнейшем для лучшего ориентирования мы будет привязывать к данным номерам Leaf номера AS eBGP и сможем очень легко ориентироваться в адресации и AS внутри фабрики. Также у нас есть закономерность, номер порта Spine совпадает с номером Leaf, например Leaf511 подключается в порты eth1 Spine501 и Spine 502, Leaf512 подключается в порты eth2 Spine501 и Spine 502 и тд. Также по AS на стороне Leaf они будут соответсвовать своим номерам в фабрике например Leaf511 AS 65511, Leaf512 AS 65512 и тд. На Spine будем использовать одну AS 65500. Определившись с логикой адресации интрефейсов и AS, начинаем собирать топологию CLOS (что отображено на скриншоте выше). Далее прописываем ip адреса на интерфейсах и проверяем доступность удаленных ip адресов. по количеству Spine и Leaf схема распределения следующая:
   В каждой стойке будет установлено по 2 Leaf (для увеличения пропускной способности и отказоустойчивости сети), между двумя leaf коммутаторами и каждым серверов (конечным хостом) будет настроен etherchannel. Схема подключения сервера: две сетевые карты подключаются в два разных leaf коммутатора в стойке (желательно чтобы нумерация портов иподключенных к ним сервера были зеркальными на двух leaf), например: server eth1 <---> leaf511 eth1, server eth2 <---> leaf512 eth1. реальная сетевая нагрузка расчитывается по критериям:
   - Максимальное разрешеное (веделенное) питание в PDU на каждый луч
   - Максимальное количество unit в стойке
   - Порты на серверах в стойке
   - Максимальный трафик который смогут сгенерировать, обработать сервера.
   Тем самым решено использовать на стороне серверов порты SFP+ и SFP28, Leaf и Spine между собой будут соединяться QSFP28 100Gbit каждый. Итог внутри фабрики каждая стойка сможет обрабатывать без потерь до 200Gbit/sec. Увеличение пропускной способности будет идти по следующему сценарию:
- если дополнительно не будет рост по стойкам, мы добавляем по одному линку между Spine и Leaf, добавляем на данные интерфейсы ip адреса и прописываем в BGP neighbor. Таким образом мы вдвое увеличим пропускную способность фабрики.
- если не достаточно портов либо увеличилось количество стоек и первый вариант не возможен, мы добавляем дополнительные Spine и увеличиваем пропускную способность до нужной скорости фабрики.

   Конфигурации устройств:
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

Spine502
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

Leaf511
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

Leaf512
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

Leaf513
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

Leaf514
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

Leaf515
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

Leaf516
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

Leaf517
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

Leaf518
hostname leaf518
interface Ethernet49
   description -> spine501
   no switchport
   ip address 10.254.15.30/30

interface Ethernet50
   description spine502
   no switchport
   ip address 10.254.16.30/30

interface Loopback0
   ip address 10.255.5.18/32

Leaf519
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

Leaf520
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

Leaf521
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

Leaf522
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
   
