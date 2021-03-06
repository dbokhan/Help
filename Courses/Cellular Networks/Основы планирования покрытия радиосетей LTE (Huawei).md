# Основы планирования покрытия радиосетей LTE

## Этап планирования

1. На этапе подготовки определяется тип застройки:
- Dense urban  (типо как Москва-сити)
- Urban (некоторые районы мегаполисов)
- Suburban (много низко этажной застройки)

2. Определяются целевые показатели качества сот
- Целевая территории
- Целевые сервисы
- Целевые показатели качества сервисов
- Целевые показатели вероятности зоны покрытия
- Целевые нагрузки

Соответствия моделей распространения и типов застройки:

- Dense Urban = ETU 3 (Extended Typical Urban model) - скорость передви = 3км\ч
- Urban = ETU 30 = 30км\ч
- Suburban = ETU 60
- Rural = EVA (Extanded Vihicular A model) 120 = 120 км\ч
- High Speed Railway = HST = 350 км\ч

Это скорости передвижения абонентов.

Параметры возможности покрытия в России для всех типов застройки = 95%

Перед Dimensioning'ом вся зона покрытия делится на кластеры. Каждый кластер должен иметь один тип застройки и примерно одинаковый трафик внутри себя. Далее по каждому кластеру производится Dimensioning.

**Определение размерности сети (Dimensioning)** определяет примерное кол-во сайтов (сот или базовых станций eNode-B), которые нужно построить с точностью +-10%. В дальнейшем это число при детальном планировании может быть увеличено или уменьшено при расположении сот на карте.

Dimensioning делится на:

- **Coverage dimensioning** - определяется сколько сайтов необходимо построить для покрытия всей местности. При этом обязательно закладываются те скорости передачи данных, которые будут у пользователя на краю соты (при худшей ситуации).

- **Capacity dimensioning** - определяется общий трафик (какое кол-во абонентов должно обслуживаться и какое кол-во сот для этого необходимо)

Обычно сначала рассчитывают coverage dimensioning, затем, если условия не соответствуют capacity dimensioning, то уменьшают размер сот и увеличивают их кол-во.


## Номинальное планирование

1. Определение точного местоположения сайтов
2. Определение параметры радио-части сетей
3. Выполняются расчеты (Предсказания и Симуляции)

На электронную карту наносится теоретически оптимальное место для базовых станций. Карта покрывается 6-ти угольной сруктурой (сотой). Если сеть строится на основе GSM и UMTS сетей, то берутся существующие сайты.

**System simulation** - тестовое расположение абонентов. Из этих тестов производится корректировка расположения и кол-во сайтов.

**Тильдование** - изменение наклона антенн

## Детальное планирование

1. Site Survey - проверка, что на данной соте можно поставить оборудование и антенны, так как было спланировано
2. Планирование параметров сот
	- 2.1.  Планирование PCI (Physical Cell ID) - чтобы не было соседей с одинаковыми PCI
	- 2.2. Планирование TA (Tracking Area) - зона пейджинга
	- 2.3. Планирование PRACH - корневые последовательности PRACH
	- 2.4. Планирование соседей
3. Планирование радио алгоритмов - планирование алгоритмов голоса, handover'а и т.д.

***

## Основные отличия LTE от 2G/3G

1. LTE имеет более гибкое распределение частот, чем 2G\3G
2. Улучшенное MIMO
3. ICIC и IRC - алгоритмы устранения интерференций
4. Определение размерности сети (Dimensioning) зависит от MCS (Modulation & Coding Scheme) на краях соты

## Алгоритм проведения LTE Coverage Dimensioning
1. Расчет EIRP (Equivalent Isotropic Radiated Power) т.е. излучаемая мощьность с антенны передатчика и minimum receiver sensitivity т.е. минимальная мощьность приемника.
2. На основе предыдущего пункта отдельно вычисляются:
	- 2.1. Расчитывается Uplink MAPL (Maximum Allowed Path Loss) и радиус соты
	- 2.2 Рассчитывается Downlink MAPL и радиус соты
3. Берется минимальный радиус соты вычисленный на предыдущем этапе. Effective cell radios = Min(uplink cell radius, downlink cell radius)
4. Расчитывается кол-во необзодимых сайтов для покрытия площади кластера. Т.е. площадь покрытия делится на площадь покрытия одного сайта (обычно 3-х секторного) и получаем кол-во сайтов.

### Модели распространения (Propagation Models) ###
Чтобы из MAPL получить радиус соты (Cell radius) надо правильно выбрать модель распространения. 

Модель Okamura-Hata - применима к диапазону от 150 до 1500 МГц, для urban и saburban.

Модель Cost231-Hata - применима к диапазону 1500 - 2000 МГц

Модель CCIR - для urban и dense urban застройки с антеннами ниже крыш здания (редко для России)

Модель LEE - для 450-2000 МГц, редко применима

Модель K parametr - самая распространненая и используеся в большинстве случаев, в частотах от 800-2000 Мгц. Также эта модель называется SPM - Standart Propagation Model.

### Бюджет линка (Link Budget)

Обычно бюджет линка расчитывается только для входящего и выходящего **каналов с данными. (PUSCH и PDSCH)**

**Что учитывается в параметрах расчета бюджета PDSCH:**
1. Morphology (Dense Urban / Urban / Suburban / Rural / Highway)
2. Duplex Mode (FDD / TDD)
3. User Environment (Indoor / Outdoor)
4. System Bandwidth (Mhz) (1.4 / 3 / 5 / 10 / 15 / 20)
5. Channel Model (EPA 3 / ETU 3 / ETU 30 и т.д.)
6. MIMO Scheme (1*2 / 1*4 / 1*8 (Uplink), 1*2 / 2*2 SFBC / 4*2 SFBC + FSTD / 4*2 SFBC / 8*2 SFBC (Downlink))
7. Cell Edge Rate (kbps)
8. MCS

**Расчет Downlink MAPL**:

	MAPL (db) = EIRP pre Subcarrier (dBm) - Min Signal Reception Strangth (dBm) - Penetration loss (dB) - shadow fading margin (dB)

	EIRP per Subcarried (dBm) = Subcarrier Power (dBm) + Tx Antenna Gain (dBi) - Tx Cable Loss (dB) - Tx body Loss (dB)

	Subcarried Power (dBm) = Max Total Tx Power (dBm) - 10*log(The Number of Subcarriers to Distribute Power)

	Min Signal Reception Strength (dBm) = Receiver Sensitivity (dBm) - Rx Antenna Gain (dBi) + Rx Cable Loss (dB) + Rx Body Loss (dB) + Interference Margin (dB)

Количество **поднесущих (Subcarriers)** зависит от **полосы пропускания (bandwidth)**:
- Для 20 МГц, Subcarrier Power (dBm) = 46 - 10*lg(12*100) = 15.2dBm
- Для 10 МГц, Subcarrier Power (dBm) = 46 - 10*lg(12*50) = 18.2dBm

**Tx Antenna Gain (dBi)**:

- Для диапазона 700 - 900 МГц = 15 dB
- Для диапазона 1500 - 2000 МГц = 18 dB
- Для диапазона 2100 - 2600 МГц = 18 dB

**Tx Body Loss (dB)** = 0

**Tx Cable Loss (dB)**:

Обычно, используются передатчики RRU (Remoute Radio Unit) установленные на башне, то Tx Cable Loss = 0.5dB.
Но если используются RRU внизу башни, то Tx Cable Loss = 3dB.

**Receiver Sensitivity (dBm)** - чуствительность приемника на стороне мобильной станции. 
	Receiver Sensitivity (dBm) = Thermal noise pre subcarrier (dBm) + Noise figure of UE (dB) + Required SINR (dB)

	Thermal noise pre subcarrier (dBm) = 10*log(K*T*W) = 132.2dBm
	K = 1.38*10^22 (константа Больцмана)
	T = 290 (Температура в Кельвинах ~17 Цельсия) 
	W = 15KHz (Ширина поднесущей)

**Rx Antenna Gain (dBi)** = 0 если приемник абонента неизвестен

**Rx Cable Loss (dB)** = 0

**Rx Body Loss (dB)** = 0, но для голосовой связи = 3dB

**Interference Margin (dB)** тяжело оценивать. Обычно принимают равным в несколько dB, но затем корректируют на этапе симуляции.

**Penetration loss (dB)** - табличные значения для различных частот и застроек

**Shadow fading margin (dB)** - табличные значения для различных типов застроек

**Расчет Uplink MAPL**:

**Tx Antenna Gain (dBi)** = 0

**Tx Cable Loss (dB)** = 0

**Receiver Sensitivity (dBm)** - чувствительность приемника на стороне eNode-B. 
	Receiver Sensitivity (dBm) = Thermal noise pre subcarrier (dBm) + Noise figure of eNode-B (dB) + Required SINR (dB)

**Noise figure of eNode-B (dB)** - это табличные значения

**Required SINR (dB)** - считается на основе симуляции (часто это темы дипломных работ студентов)

**Rx Antenna Gain (dBi)** усиление антенны eNode-B

**Rx Cable Loss (dB)** = 0

**Rx Body Loss (dB)** = 0

**Interference Margin (dB)** - результаты симуляции, но обычно это небольшие значения

**Penetration loss (dB)** и **Shadow fading margin (dB)** - аналогичны Downlink

У Huawei есть утилита Radio Network Dimensioning(RND)для LTE планирования. И утилита Genex U-NET.

[Ссылка на видео](https://www.youtube.com/watch?v=H5QplBYu6aE)