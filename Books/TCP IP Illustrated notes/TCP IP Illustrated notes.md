# TCP/IP Illustrated

# TCP/IP Illustrated 1st edition

**Network byte order** (про физ.ур.) - это последовательность бит при передаче данных по сети. Входит в категорию Big-Endian последовательностей. 
  
> Последовательность Big-Endian - наиболее значимые значения нумеруются меньшим адресом ячейки памяти.
>
> Последовательность Little-Endian - наиболее значимые значения нумеруются большим адресом ячейки памяти.
>
> Устройства хранящие данные в формате отличном от Big-endian должны быть переформатированы перед отправкой по сети.
>
> [Big-endian and little-endian terms](https://www.webopedia.com/TERM/B/big_endian.html)

# TCP/IP Illustrated 2nd edition
## 2. The Internet Address Architecture

**IPv4-mapped IPv6 addresses** - тип записи IPv4 адреса в IPv6 формате. Предназначен для работы IPv4 адресов в приложениях предназначенных только для IPv6.

> Пример адреса: ::FFFF:129.144.52.38
>
> [IPv4-mapped IPv6 addresses](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.3.0/com.ibm.zos.v2r3.hale001/ipv6d0031001726.htm)



**EUI (Extended Unique Identifier)** - это схема присвоения адресов. Например, EUI-64, EUI-48, MAC-48(Устаревшая). Отличие EUI-64 и EUI-48 в длине адресов.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/94/MAC-48_Address.svg/800px-MAC-48_Address.svg.png)

EUI состоят из двух частей:
1) OUI (Organizationally Unique Identifier) - часть назначенная IEEE Registration Authority для идентификации производителя. Занимает 24 бита = 3 байта
2) NIC (Network Interface Controler) - часть идентификации конкретного сетевого адаптера. Занимает всю оставшуюся часть адреса в EUI-48: 24 бита = 3 байта

Первые 2 бита первого байта в OUI определяют:
- 2'ой бит (u бит) - определяет является ли адрес глобальным или назначен администратором:
  - Universally Administered Addresses (UAA) - если бит = 0
  - Locally Administered Addresses (LAA) - если бит = 1
- 1'ый бит (g бит) - определяет является ли адрес юникастовый или мультикастовым:
  - Unicast - если бит = 0
  - Group - если бит = 1
  
  Процесс преобразования MAC адреса в IPv6 link-local адрес:
  1) Изначальный MAC адрес: 00:30:48:2A:19:89
  2) Преобразование EUI-48 в EUI-64. Т.е. на место 4 и 5 бита вставляется стандартная последовательность бит. 00:30:48:FF:FE:2A:19:89
  3) Инвертируется u бит. 02:30:48:FF:FE:2A:19:89
  4) Добавляется link-local префикс (FE80::/10). FE80::230:48FF:FE2A:1989/64

