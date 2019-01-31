# TELCOMA Global - 4G LTE Training (YouTube)

## What is LTE Network Architecture

4G полностью пакетно-коммутируемая технология (Fully Packet-Switched Network).

![](https://upload.wikimedia.org/wikipedia/commons/d/d7/Evolved_Packet_Core.svg)

**Архитектура 4G - System Architecture Evolution (SAE) включает:**
1. Radio Network - E-UTRAN (Evolved-Universal Terrestrial Radio Network)

E-Utran состоит из нескольких eNodeB, один из которых Network Controller.

2. Core Network - EPC (Evolved Packet Core)

EPC включает несколько устройств:

1. MME (Mobility Managment Equipment) - отвечает за подключения и хэндоверы, подключается в базе HSS для проведения авторизации абонентов

2. HSS (Home Station Subsystem) - база данных, хранит данные о абонентах

3. S-GW (Serving Gateway)

4. P-GW (Public Gateway)

eNodeB подключаются к MME и SGW через MME идет Control Plane, через SGW идет Data Plane.

eNodeB подключаются друг к другу через x2 интерфейс, а связь между U-TRAN и EPC через S1 интерфейсы, причем для control plane - S1-C, а для data plane S1-U.

## LTE Drive Test Parameters

**Параметры для радио-части LTE:**

1. RSRP - Reference Signal Recuived Power

2. RSRQ - Reference Signal Recuived Quality

3. RSSI - Reference Symbol Signal Intencity

4. SINR - Signal to Interference Noise Ratio

5. COI - Channel Quality Index

6. PCI - Physical Cell Identiry

7. BLER - Block Error Ratio

8. DL Throughput

9. UP Throughput

**RSRP - Reference Signal Recuived Power** - этот параметр показывает силу сигнала. Если мы хотим узнать силу сигнала соты, то нужно смотреть этот параметр.

[YouTube канал](https://www.youtube.com/channel/UCQLQxPH8mL0bnA7B3lIfNww/playlists)