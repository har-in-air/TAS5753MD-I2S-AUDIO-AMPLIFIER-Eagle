# TAS5753MD-I2S-AUDIO-AMPLIFIER-Eagle
Digital audio power amplifier with I2S interface using TI's TAS5753MD chip

Eagle schematic, layout and gerber files

Uses Stereo Bridge Tied Load application schematic from the TI datasheet. Added an A04409 PMOSFET and BSS138 NMOSFET to allow controlled PVDD on/off. Added MAX16904 3.3V (max 600mA) switching regulator to power the TTL logic 3.3V supply - this can also be used to supply 3.3V to the driving circuit, e.g. Espressif ESP32 module with web radio or bluetooth speaker firmware.

Features : 
1. PVDD range is 4.5V to 24V 
2. Can drive 4ohm speakers
3. 90% efficiency
4. Requires external MCLK. However, if used with 44.1kHz or 48kHz sampling rates, and the bit clock (BCK / SCLK) is at least 64 x sampling rate, then MCLK can be tied to BCK. A solder jumper is provided for this. This is how I have tested the board.

## Components
See the datasheet for recommendations. The specific packages used in the layout are :

### Capacitors

1206 : C16, C21, C35, C36, C37

0805 : C1, C3, C14

0603 : remaining smt ceramic caps

### Resistors
All are 0603 package. R9 (18K) specificially needs to be 1% precision. Either populate R7 OR R8 to set the LSb of the TAS5753MD I2C slave address. R4 (22K) should be shorted or replaced with a 0 ohm resistor if PVDD is less than 10V, to ensure that the PMOSFET fully turns on.

I found all the passive components on Aliexpress and Ebay. E.g.:

https://www.aliexpress.com/item/10pcs-lot-12-12-7-15UH-SMT-SMD-Patch-Shielding-Power-Inductors-150-Electronic-Components-Free/32591194870.html

https://www.aliexpress.com/item/10pcs-0-68uF-684J-100V-Free-shipping-CBB-Polypropylene-film-capacitor-pitch-5mm-684-100V-680nF/32712243979.html

https://www.aliexpress.com/item/100pcs-lot-100nF-X7R-Error-10-50V-0603-smd-capacitor/32318089455.html


