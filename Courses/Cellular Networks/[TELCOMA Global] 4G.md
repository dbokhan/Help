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

5. CQI - Channel Quality Index

6. PCI - Physical Cell Identiry

7. BLER - Block Error Rate

8. DL Throughput

9. UP Throughput

**RSRP - Reference Signal Received Power** - этот параметр показывает силу сигнала. Если мы хотим узнать силу сигнала соты, то нужно смотреть этот параметр. Этот параметр используется в обоих режимах работы: idle и connected. _(PS. При изменении RSRP в худшую сторону, это значит, что абонент должен изменить соту (хэндовер), т.к. он выходит из зоны действия соты)_.

Формула:

	RSRP = RSSI - 10 log(N*12)

	N - кол-во ресурсных блоков (RB)
	12 - кол-во sub-carriers (поднесущих)
	Диапазон значений от -44 до -140 dbm

	Диапазон значений является KPI (Key Performance Indicatior) и показывает эффективность работы, если RSRP меньше чем -140 dbm, то надо оптимизировать сеть

**RSRQ - Reference Signal received Quality**

Формула:

	RSRQ = RSRP/(RSSI/N)

	Диапазон значений от -3 до 19,5 dbm
	(Большие значения говорят о хорошем качестве, меньшее о плохом)

**SINR - Signal to Interference Noise Ratio**

Формула:
	SINR = S/I+N 

	S - Avg. received signal power
	I - Avg. received Interference
	N - Avg. received Noise

**RSSI - Reference Symbol Signal Intencity**

RSSI включает в себя noise + Spower + Interference Power

Формула:
	RSSI = 12 * N * RSRP

	12 - кол-во sub-carriers (поднесущих)
	N - кол-во ресурсных блоков (RB)

**CQI - Channel Quality Index** - показывает качество DownLink

Принимает значения от 1 до 15. 15 - хорошее значение

**PCI - Physical Cell Identiry**

Формула:

	PCI = PSS + 3 * SSS

	PSS - Primary Synchronization Signal, принимает значения 0; 1; 2
	SSS - Secondary Synchronization Signal, принимает значения от 0 до 167

**BLER - Block Error Rate** - общее кол-во ошибочных блоков деленое на общее кол-во переданных блоков

Формула:

	BLER = Total Erroneous Blocks / Total Blocks tx

Пример:
	Всего переданно 100 блоков.

	Ошибочных блоков 20.

	BLER = 20/100*100 = 20%

Хорошим показателем является, когда BLER < 10%

**DL Throughput и UP Throughput** - показатели скорости DL и UP каналов

[YouTube канал](https://www.youtube.com/channel/UCQLQxPH8mL0bnA7B3lIfNww/playlists)