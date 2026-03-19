
#linux #networking #interfaces
Сетевые интерфейсы в Linux: физические (eth0, enp0s3), виртуальные (lo, veth, bridge, bond, vlan).
## Просмотр
```bash
ip link show
```

## Управление состоянием

```

ip link set eth0 up     # включить интерфейс
ip link set eth0 down   # выключить
```

## Создание виртуальных интерфейсов

### VLAN

```

ip link add link eth0 name eth0.10 type vlan id 10
```


### Veth-пары (для network namespaces)

```

ip link add veth0 type veth peer name veth1
```


## Алиасы (устаревшее)

bash

ifconfig eth0:0 192.168.1.1 netmask 255.255.255.0 up

Современный способ – назначать несколько IP на один интерфейс через `ip addr`.

## Постоянная конфигурация

- **Netplan** (Ubuntu) – YAML-файлы в `/etc/netplan/`.
    
- **NetworkManager** – для десктопов, управление через `nmcli`.
    
- **ifupdown** (Debian) – `/etc/network/interfaces`.
    

## Связанные заметки

- [[IP addressing CIDR]]
    
- [[VLAN]]
    
- [[Network namespaces]]