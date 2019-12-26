# Информация по различным протоколам туннелирования


## Теоретическая информация по L2TP (Без шифрования)

### Инкапсуляция L2TP
![](https://www.researchgate.net/profile/Adrian_Graur2/publication/287458379/figure/fig4/AS:314843556007939@1452075961245/L2TP-Tunnel-Data-Frame-Format_W640.jpg)

## L2TP Server Минимальная настройка на примере Debian

### Предварительные требования

* Включенный IP Routing

В файле "/etc/sysctl.conf":
```
net.ipv4.ip_forward=1
```
Применить изменения:

```
sysctl -p
```

* Открытый UDP порт 1701:


```
iptables -A INPUT -p udp -m udp --dport 1701 -m comment --comment L2TP -j ACCEPT
```

### Установка

```
apt-get install xl2tpd ppp
```

### Настройка L2TP в файле "/etc/xl2tpd/xl2tpd.conf"

```
[global]

[lns default]
 ip range = 192.168.100.2-192.168.100.254 ; * Назначается l2tp клиентам
 local ip = 192.168.100.1 ; * Назначается l2tp серверу (LNS)
 refuse pap = yes ; * Не использовать аутентификацию по pap
 require authentication = yes ; * Запрашивать аутентификацию
 pppoptfile = /etc/ppp/options ; * Ссылка на файл конфигурации PPP
```

### Настройка PPP в файле "/etc/ppp/options"

```
asyncmap 0
auth
hide-password
lcp-echo-interval 30
lcp-echo-failure 4
noipx
```
### Настройка пользователей для аутентификации в файле "/etc/ppp/chap-secrets"

```
username * password *
```

### Запуск и отладка

```
/etc/init.d/xl2tpd start
/etc/init.d/xl2tpd status
cat /var/log/syslog
ip route
```
