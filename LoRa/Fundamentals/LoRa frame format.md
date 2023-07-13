**Also known as the packet format**

![[Pasted image 20230713125158.png]]

**Preamble** is used to synchronize the receiver with the transmitter. 
It MUST consist of 8 symbols for all regions as mentioned in the LoRaWAN Regional Parameters document. However, the radio transmitter will add another 4.25 symbols resulting in a final preamble length of 8 + 4.25 = 12.25 symbols