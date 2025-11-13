# Вопросы для самостоятельной работы: WAN

## Задания

### Задание 1: Настройка PPP на маршрутизаторе Cisco
**Цель:** Настроить PPP-соединение между двумя маршрутизаторами
**Команды:**
```
Router1(config)# interface Serial 0/0/0
Router1(config-if)# encapsulation ppp
Router1(config-if)# ip address 192.168.1.1 255.255.255.0
Router1(config-if)# ppp authentication chap
Router1(config-if)# username Router2 password cisco123
Router1(config-if)# no shutdown

Router2(config)# interface Serial 0/0/0
Router2(config-if)# encapsulation ppp
Router2(config-if)# ip address 192.168.1.2 255.255.255.0
Router2(config-if)# ppp authentication chap
Router2(config-if)# username Router1 password cisco123
Router2(config-if)# no shutdown
```
**Проверка:** `show interfaces serial 0/0/0`, `show ppp all`

### Задание 2: Настройка HDLC
**Цель:** Настроить HDLC-инкапсуляцию
**Команды:**
```
Router1(config)# interface Serial 0/0/0
Router1(config-if)# encapsulation hdlc
Router1(config-if)# ip address 192.168.2.1 255.255.255.0
Router1(config-if)# no shutdown

Router2(config)# interface Serial 0/0/0
Router2(config-if)# encapsulation hdlc
Router2(config-if)# ip address 192.168.2.2 255.255.255.0
Router2(config-if)# no shutdown
```
**Проверка:** `show interfaces serial 0/0/0`

### Задание 3: Анализ WAN-технологий
**Задание:** Создайте таблицу сравнения следующих WAN-технологий:
- Leased Lines (T1/E1)
- Frame Relay
- ISDN
- DSL
- Cable

**Критерии сравнения:**
- Скорость
- Тип соединения (dedicated/shared)
- Расстояние
- Стоимость
- Надежность

### Задание 4: Расчет пропускной способности
**Задание:** Рассчитайте общую пропускную способность для следующих сценариев:
- 4 × T1 линии
- DSL-соединение с downstream 24 Мбит/с
- Cable модем с 100 Мбит/с
- Frame Relay PVC 512 Кбит/с

## Рекомендации

Студенты должны выполнить настройки на оборудовании или симуляторах, предоставить конфигурации и результаты проверки команд show.
