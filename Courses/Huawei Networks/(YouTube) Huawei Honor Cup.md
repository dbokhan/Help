# 4. Network Security 

В ACL Huawei нет неявно указанного deny any в конце списка.

Пример настройки ACL:
```
acl number 3001
rule 10 permit tcp source 192.168.1.0 0.0.0.255 destination 202.1.5.1 0.0.0.0 source-port any destination-port 80
rule 20 deny ip source any destination any
```

**Классификация ACL:**
- Basic - фильтрация только по ip адресу источника
- Advanced - фильтрация по tcp\udp\icmp
- L2 ACL - по MAC адресам (номера ACL от 4000)
- User-Defined - сложные ACL с фильтрацией до прикладного уровня

