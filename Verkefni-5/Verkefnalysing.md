### 5.1 Interrupts 
1. Kynntu þér hvernig interrupts virkar og svaraðu eftirfarandi spurningum:
   1. Svar: Maður notar interrupts til að láta eitthvað sérstakt gerast þegar maður t.d. ýtir á takka.
2. Hvenær er heppilegt að nota interrupts. komdu með dæmi?
   1. Svar: Það er sérstaklega gott að nota interrupts þegar maður er með tæki sem á bara að gera eitthvað þegar maður t.d. ýtir á takka því þá geturðu látið tölvuna sofa á meðan þangað til að það er ýtt á takkann og þá vaknar talvan og gerir eitthvað ákveðið.
3. Hvað eru volatile breytur?
   1. Það eru breytur sem þú munnt nota inn í interrupts lykkjunum og eru gerðar þannig að þær gætu breyst hvenær sem er.
1. Settu upp verklega kóða sem notar takka og led með notkun interrupts.

**Bjargir:**
- [Myndband; Arduino Interrupts](https://www.youtube.com/watch?v=QtyOiTw0oQc) 
- [Vefgrein: Interrupt Service Routines (ISR)](http://gammon.com.au/interrupts)
- [attachinterrupt()](https://www.arduino.cc/reference/en/language/functions/external-interrupts/attachinterrupt/)
- Adafruit - Multi-tasking the Arduino (notar class); [Part 1: millis](https://learn.adafruit.com/multi-tasking-the-arduino-part-1) og [Part 2: interrupts](https://learn.adafruit.com/multi-tasking-the-arduino-part-2/overview)

---

### 5.2 SPI samskiptastaðallinn. 
Lestu [BASICS OF THE SPI COMMUNICATION PROTOCOL](https://www.circuitbasics.com/basics-of-the-spi-communication-protocol), sjá einnig [myndband um SPI](https://www.youtube.com/watch?v=ldRkXTBw9_o) og svaraðu eftirfarandi spurningum:
   
   1. Hvað er átt við með samstilltum (e. synchronous) samskiptastaðli?
      1. Þegar tvö tæki nota sömu clock signal
   3. Útskýrðu master-slave samskipti í SPI útfrá; MISO, MOSI, SCLK og CS/SS.
      1. MISO er master in slave out sem þýðir að slaveinn er að senda information til masterins, MOSI er akkúrat öfugt, SCLK er clock signalið sem er basically hversu hratt upplýsingar ferðast á milli
   5. Hverjir eru helstu kostir og ókostir við SPI?
      1. Það góða er að það er hægt að senda upplýsingar á milli slaves og masters á sama tíma og hraðar, stoppar ekki og ekki flókið að velja slave. Það slæma er að það er aldrei víst hvenær það er er búið að senda upplýsingar á milli, leyfir bara einum master, notar fjóra víra og það er ekkert error check.

---

### 5.3 SPI samskipti milli tveggja Arduino. 
Settu upp á Breadboard með Arduino Uno og [Nano](https://www.arduino.cc/en/pmwiki.php?n=Main/ArduinoBoardNano) þannig að þeir geti notað SPI samskipti með [SPI safninu](https://www.arduino.cc/en/reference/SPI) til að tala saman. [Mynd sem sýnir pinna á Nano](https://i2.wp.com/christianto.tjahyadi.com/wp-content/uploads/2014/11/nano.jpg)
1. Arduino Uno á að geta sent streng (nafnið þitt) til Arduino Nano sem birtir svo nafn á Serial Monitor. Sjá t.d. [How do you use SPI on an Arduino?](https://arduino.stackexchange.com/questions/16348/how-do-you-use-spi-on-an-arduino).
1. Bættu við tökkum og leds, sjá [uppsetningu](https://raw.githubusercontent.com/VESM3/V21/master/Myndir/SPI.png)  þannig að hægt sé að eiga samskipti í báðar áttir með tökkum. Sjá [kóða](https://gist.github.com/gestskoli/d2069beb5c4d0cf7c9351d75dfc3e2b0) og [Communication between two Arduino Boards](https://circuitdigest.com/microcontroller-projects/arduino-spi-communication-tutorial)  
<!-- 1. Bættu takka við Arduino Uno. Þegar ýtt er á hann þá á led sem er tengt við Arduino Nano að lýsa. -->

---

### 5.4 Þráðlaus samskipti tveggja Arduino með notkun nRF24L01 (í eina átt) 
Lestu vel og vandlega og fylgdu tutorial: [How nRF24L01+ Wireless Module Works & Interface with Arduino](https://lastminuteengineers.com/nrf24l01-arduino-wireless-communication/). Skoðaðu einnig fyrra sýnidæmið í [myndbandinu](https://howtomechatronics.com/tutorials/arduino/arduino-wireless-communication-nrf24l01-tutorial/)

1. Notaðu [RF24 safnið](https://github.com/nRF24/RF24) og settu upp verklega með Arduino Uno og Nano. Tengdu nRF24L01 sem hefur **ekki** nRF24L01+ Adapter við 3.3V output, ekki tengja í 5V, það mun skemma nRF24L01. Notaðu einnig 9V batterí (stöðugra) fremur en usb portið á tölvunni. Einnig gott að nota 100f rafþéttir (capacitor).
1. Passaðu að hafa sömu tíðnina (Radio Frequency) og fremur há gildi með `.setChannel()` í setup falli.
1. Strengurinn inniheldur nafnið þitt (ekki Hello World)
1. Láttu LED lýsa hjá `transmitter` sem staðfestir að strengur hafi borist til `receiver`. 
1. Til hvers er `IRQ` pinninn og hvernig væri hægt að nota hann td. fyrir fjarstýrða bílinn?

---

### 5.5 Þráðlaus samskipti í báðar áttir með tveimur Arduino. 
Sýndu samskipti sem fara í báðar áttir með notkun takka og led. Sjá síðara sýnidæmið í [myndbandinu](https://howtomechatronics.com/tutorials/arduino/arduino-wireless-communication-nrf24l01-tutorial/)

---
