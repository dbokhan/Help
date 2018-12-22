# Базовая настройка

Вход в configure terminal
```
<> system-view
```

Смена имени хоста
```
[] sysname R2
```

Настройка пароля на консоль Huawei Router
```
[] user-interface console 0
[ui-console0] authentication-mode password
[ui-console0] set authentication password cipher 12345
[ui-console0] quit
```

Настройка пароля (telnet) на VTY Huawei Router
```
[] user-interface vty 04
[ui-vty4] authentication-mode password
[ui-vty4] set authentication password cipher 12345
[ui-vty4] quit
[] quit
<> save
```

Настройка VLAN на Huawei Switch
```
[] interface vlanif 1
[Vlanif1]ip address 192.168.1.2 24
[Vlanif1] quit
```

Настройка пароля на консоль Huawei Switch
```
[] user-interface console 0
[ui-console0] authentication-mode password
[ui-console0] set authentication password simple 12345
[ui-console0] set authentication password cipher 12345
[ui-console0] quit
```

Настройка пароля (telnet) на VTY Huawei Switch
```
[] user-interface vty 04
[ui-vty4] authentication-mode pass
[ui-vty4] set authentication password simple 12345
[ui-vty4] set authentication password cipher 12345
[ui-vty4] quit
[] quit
<> save
```

Ограничение доступа на подключение к VTY на Huawei Switch
```
[] acl number 2001
[acl-basic-2001] rule permit source 192.168.1.10 255.255.255.0
[acl-basic-2001] quit
[] user-interface vty 04
[ui-vty4] acl 2001 inbound
[ui-vty4] quit
```

# Статическая маршрутизация

Настройка статического маршрута
```
[] ip route-static 0.0.0.0 0.0.0.0 192.168.1.1
```

# Настройка RIP
```
[] rip
[rip-1] version 2
[rip-1] network 10.0.0.0
```

# Настройка OSPF
```
[] ospf
[ospf-1] area 0
[ospf-1-area-0.0.0.0] network 10.0.0.0 0.0.0.255
```

# Настройка DHCP сервера
```
[] dhcp enable
[] ip pool pool1
[ip-pool-pool1] network 10.1.0.0 mask 29
[ip-pool-pool1] gateway-list 10.1.0.1
[ip-pool-pool1] dns-list 192.168.10.2
[ip-pool-pool1] excluded-ip-address 10.1.1.6
[ip-pool-pool1] quit
[] interface Ethernet 0/0/0
[Ethernet0/0/0] dhcp select global
[Ethernet0/0/0] quit
```

# Настройка VLAN и trunk

Настройка VLAN на Huawei Switch:
```
[] vlan batch 101 to 103
[] interface vlanif 101
[vlanif101] description VLAN101
[vlanif101] quit
[] interface Gi 0/0/1
[GigabitEthernet0/0/1] port link-type access
[GigabitEthernet0/0/1] port default vlan 102
[GigabitEthernet0/0/1] quit
[] interface Gi 0/0/0
[GigabitEthernet0/0/0] port link-type trunk
[GigabitEthernet0/0/0] port trunk allow-pass vlan 101 102 103
[GigabitEthernet0/0/0] quit
```

Настройка trunk порта на Huawei Router:
```
[] interface Ethernet 0/0/0.101
[Ethernet0/0/0.101] dot1q termination vid 101
[Ethernet0/0/0.101] ip address 192.168.101.1 24
```

# Настройка STP
```
[] STP enable
[] stp mode stp
[] stp root secondary
[] interface Gi 0/0/24
[GigabutEthernet0/0/24] stp disable
[GigabutEthernet0/0/24] quit
[] interface G0/0/0
[GigabutEthernet0/0/0] bpdu enable
[GigabutEthernet0/0/1] quit
```
