# Информация по различным протоколам туннелирования

## L2TP (Чистый)

## L2TP Server Минимальная настройка на примере Debian

### Установка 
```
apt-get install xl2tpd ppp
```

### Настройка l2tp в файле "/etc/xl2tpd/xl2tpd.conf"

```
[global]

[lns default]
 ip range = 192.168.100.2-192.168.100.254 ; * Назначается l2tp клиентам
 local ip = 192.168.100.1 ; * Назначается l2tp серверу (LNS)
 refuse pap = yes ; * Не использовать аутентификацию по pap
 require authentication = yes ; * Запрашивать аутентификацию
 pppoptfile = /etc/ppp/options ; * Ссылка на файл конфигурации PPP
```
