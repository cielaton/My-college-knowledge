#### Spreading Factors
The spreading factor controls the speed of data transmission. Lower spreading factors mean a higher data transmission rate.

|**Spreading Factor**|**Data Rate**|**Range**|**Time on-Air**|
|:-:|:-:|:-:|:-:|
|SF7|5470 bps|2 km|56 ms|
|SF8|3125 bps|4 km|100 ms|
|SF9|1760 bps|6 km|200 ms|
|SF10|980 bps|8 km|370 ms|
|SF11|440 bps|11 km|40 ms|
|SF12|290 bps|14 km|1400 ms|

**Data rate (bit rate)**: The number of bits that are conveyed or processed per unit of time.
**Time on-air**: The amount of time the receiver takes to receive the data after the sender starts to transmit.

Lower spreading factors reduce the range of LoRa transmissions, because they reduce the *processing gain* and increase the bit rate.

>Higher spreading factors provide higher receiver sensitivity. Usually, LoRa uses higher spreading factors when the signal is weak.

---
#### Coding rate
The coding rate refers to the proportion of transmitted bits that actually carry information. 
Coding rate can be \*/5 or  \*/8.

So if CR is 4/8 we are transmitting twice as many bits as the ones containing information.

---
