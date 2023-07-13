**Also known as the packet format**

LoRa uses two types of packet formats for data transmission: explicit and implicit.
##### Explicit mode:

![[Pasted image 20230713125158.png]]

- **The preamble** is used to synchronize the receiver with the transmitter. 
It MUST consist of 8 symbols for all regions. However, the radio transmitter will add another 4.25 symbols, resulting in a final preamble length of 8 + 4.25 = 12.25 symbols.
- **PHDR (Physical Header)** is an optional element only present in the explicit mode that contains information about *payload size* and *CRC* (Cyclic Redundancy Check).
- **PHDR_CRC (Header CRC)** is an optional field that contains an error detecting code for correcting errors in header.
