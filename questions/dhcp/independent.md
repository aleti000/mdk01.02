# Вопросы для самостоятельной работы: DHCP

## Задания

### Задание 1: Базовая настройка DHCP на маршрутизаторе
**Команды:**
```
Router> enable
Router# configure terminal
Router(config)# ip dhcp pool LAN1
Router(dhcp-config)# network 192.168.10.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.10.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit
Router(config)# ip dhcp excluded-address 192.168.10.1 192.168.10.10
Router(config)# end
```
**Проверка:** ПК получает IP-адрес из диапазона при настройке Automatic (DHCP).

### Задание 2: Настройка нескольких DHCP-пулов
**Команды:**
```
Router(config)# ip dhcp pool VLAN10
Router(dhcp-config)# network 10.10.10.0 255.255.255.0
Router(dhcp-config)# default-router 10.10.10.1
Router(dhcp-config)# exit

Router(config)# ip dhcp pool VLAN20
Router(dhcp-config)# network 10.20.20.0 255.255.255.0
Router(dhcp-config)# default-router 10.20.20.1
```
**Проверка:** ПК из VLAN10 получает IP 10.10.10.x, из VLAN20 — 10.20.20.x.

### Задание 3: Проверка и диагностика DHCP
**Команды:**
```
Router# show ip dhcp binding
Router# show ip dhcp pool
Router# show running-config | section dhcp
```
**Windows команды:**
```
> ipconfig /all
> ipconfig /release && ipconfig /renew
```
**Проверка:** Проверить, что клиенты получили IP-адреса из нужных пулов.

### Задание 4: Настройка DHCP для нескольких интерфейсов маршрутизатора
**Команды:**
```
Router> enable
Router# configure terminal
Router(config)# interface g0/0
Router(config-if)# ip address 192.168.10.1 255.255.255.0
Router(config-if)# no shutdown
Router(config)# interface g0/1
Router(config-if)# ip address 192.168.20.1 255.255.255.0
Router(config-if)# no shutdown
Router(config)# ip dhcp pool LAN_A
Router(dhcp-config)# network 192.168.10.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.10.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit
Router(config)# ip dhcp pool LAN_B
Router(dhcp-config)# network 192.168.20.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.20.1
Router(dhcp-config)# dns-server 8.8.4.4
Router(dhcp-config)# exit
Router(config)# ip dhcp excluded-address 192.168.10.1
Router(config)# ip dhcp excluded-address 192.168.20.1
```
**Проверка:** ПК в сети 192.168.10.0 получает IP 192.168.10.x, ПК в сети 192.168.20.0 получает IP 192.168.20.x.

### Задание 5: Настройка статического назначения DHCP (резервация)
**Команды:**
```
Router(config)# ip dhcp pool STATIC_PC
Router(dhcp-config)# host 192.168.10.50 255.255.255.0
Router(dhcp-config)# client-identifier 0100.5056.9abc.de
Router(dhcp-config)# default-router 192.168.10.1
```
**Проверка:** ПК с этим MAC получает 192.168.10.50 при каждом подключении.

## Рекомендации

Студенты должны выполнить практические задания на оборудовании или в симуляторе, предоставить скриншоты конфигураций и результатов проверки.
