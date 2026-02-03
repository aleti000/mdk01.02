# Лабораторная работа №3: Управление сетевыми устройствами с помощью Ansible

## Тема: Управление сетевыми устройствами с помощью Ansible

## Цель работы:
Настроить адресацию, установить Ansible и коллекцию cisco.ios, настроить hosts и playbook для базовой конфигурации сетевых устройств.

## Схема сети:

![Схема сети для лабораторной работы по Ansible](https://github.com/aleti000/mdk01.02/blob/main/pic/network.jpg)

## Теоретические основы

### Что такое Ansible?
Ansible — это система автоматизации с открытым исходным кодом, используемая для настройки и управления компьютерными системами. Он работает по агентному принципу, используя SSH для подключения к управляемым узлам.

### Архитектура Ansible
- **Control Node**: Машина, с которой выполняются команды Ansible
- **Managed Nodes**: Устройства, которые настраиваются Ansible
- **Inventory**: Файл, содержащий информацию об управляемых узлах
- **Playbooks**: YAML-файлы, описывающие задачи для выполнения
- **Modules**: Библиотеки кода, выполняющие конкретные задачи

## Ход работы

### Шаг 1. Установка Ansible

#### 1.1. Установка Ansible
```bash
# Обновление системы
sudo apt-get update

# Установка Ansible
sudo apt install ansible -y

# Проверка версии
ansible --version
```

### Шаг 2. Установка коллекции cisco.ios

#### 2.1. Установка коллекции
```bash
# Установка коллекции cisco.ios
ansible-galaxy collection install cisco.ios

# Проверка установки
ansible-galaxy collection list
```

### Шаг 3. Настройка адресации

#### 3.1. Создание inventory файла
Создайте файл `inventory/hosts.yml`:
```yaml
all:
  children:
    routers:
      hosts:
        hq-rtr:
          ansible_host: ip-address
          ansible_user: admin
          ansible_network_os: cisco.ios
        br-rtr:
          ansible_host: ip-address
          ansible_user: admin
          ansible_network_os: cisco.ios
      vars:
        ansible_connection: network_cli
        ansible_become: yes
        ansible_become_method: enable
```


### Шаг 4. Создание playbook

#### 4.1. Playbook для базовой настройки
Создайте файл `playbooks/basic_config.yml`:
```yaml
---
- name: Basic configuration for network devices
  hosts: routers
  gather_facts: no

  tasks:
    - name: Configure hostname
      cisco.ios.ios_config:
        lines:
          - hostname {{ inventory_hostname }}

    - name: Configure interface GigabitEthernet0/1
      cisco.ios.ios_config:
        parents: interface GigabitEthernet0/1
        lines:
          - description To {{ inventory_hostname }} network
          - ip address 192.168.252.1 255.255.255.0
          - no shutdown

    - name: Configure interface GigabitEthernet0/2
      cisco.ios.ios_config:
        parents: interface GigabitEthernet0/2
        lines:
          - description To {{ inventory_hostname }} LAN
          - ip address 10.0.1.1 255.255.255.0
          - no shutdown

    - name: Save running config
      cisco.ios.ios_config:
        save_when: modified
```

#### 4.2. Выполнение playbook
```bash
# Проверка подключения
ansible all -m ping -i inventory/hosts.yml

# Выполнение playbook
ansible-playbook playbooks/basic_config.yml -i inventory/hosts.yml
```

## Проверка корректности настройки

### Команды для диагностики Ansible
```bash
# Проверка подключения к устройствам
ansible all -m ping -i inventory/hosts.yml

# Проверка синтаксиса playbook
ansible-playbook --syntax-check playbooks/basic_config.yml -i inventory/hosts.yml

# Выполнение playbook с детальным выводом
ansible-playbook playbooks/basic_config.yml -i inventory/hosts.yml -v
```

### Команды для диагностики сетевых устройств
```bash
# Проверка состояния интерфейсов
show ip interface brief

# Проверка таблицы маршрутизации
show ip route

# Проверка конфигурации
show running-config
```

## Критерии выполнения работы

Работа считается выполненной при соблюдении следующих условий:

- [ ] Ansible установлен и настроен на control node
- [ ] Коллекция cisco.ios установлена
- [ ] Inventory файл создан и работает корректно
- [ ] SSH-доступ к сетевым устройствам настроен
- [ ] Playbooks выполняются без ошибок
- [ ] Конфигурация применена на устройствах

### Проверка выполнения
```bash
# Проверка подключения
ansible all -m ping -i inventory/hosts.yml

# Выполнение playbook
ansible-playbook playbooks/basic_config.yml -i inventory/hosts.yml
```

## Контрольные вопросы:

1. **Что такое Ansible и для чего он используется в сетевом администрировании?**
2. **Какие основные компоненты Ansible и их назначение?**
3. **Как работает inventory в Ansible и как его настраивать для сетевых устройств?**
4. **Какие модули используются для управления сетевыми устройствами в Ansible?**
5. **Какие способы аутентификации существуют в Ansible для подключения к сетевым устройствам?**
6. **Как создать playbook для автоматизации настройки сетевых интерфейсов?**
7. **Какие команды используются для диагностики Ansible и сетевых устройств?**
8. **Как настроить резервное копирование конфигурации с помощью Ansible?**

## Примечания:

- Все изменения конфигурации сохраняйте в системе контроля версий
- Перед внесением изменений создавайте резервные копии конфигурации
- Используйте модуль `cisco.ios.ios_config` для безопасного применения изменений
- Для отладки используйте параметр `-v` при выполнении playbook
- Проверяйте синтаксис playbook перед выполнением с помощью `--syntax-check`
