# BMS-und-ESP32
BMS mittels BLE auslesen mit einem ESP32 <br>
Es sind 3 Versionen, für den TTGO mit 1.8 oder 2.4" Display oder den ESP32 Nodemcu mit getrenntem Display.<br>
Der Sketch läuft auf jedem Fall auf dem ESP32, evtl. muss das Display und die Pins für die Tasten noch angepasst werden.<br>
Im Sketch steht – im ersten Reiter in der loop -  um die Zeile 488<br>
packBasicInfo.ProtectionStatus = 32767;                  // 111111111111111 alle Fehler<br>
damit werden zum Testen alle Fehler-Flags gesetzt, das muss im Betrieb auskommentiert werden.<br>
Und ohne BMS bezw. Bluetooth-Verbindung geht auch nicht viel 😉.<br>
In der Arduino-IDE <br>
  Board ESP 32 DEV<br>
  Flash Size 4 MB<br>
  Partition Scheme "NO OTA/2 MB App 2 MB SPIFFS"<br>
  oder<br>
  Partition Scheme "minimal SPIFFS/ 1,9MB App with OTA/ 190 kB SPIFFS"<br>
einstellen. OTA geht grundsätzlich, aber dann ist fast zu wenig SPIFFS da.<br>
Viel Erfolg.
