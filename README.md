# BMS-und-ESP32
BMS meiner Wohnmobil LiFePo-Batterie mittels BLE mit einem ESP32 auslesen.<br><br>
Das ZIP-FIle enthält alle Dateien für die ARDUINO-IDE.<br>
Hier läuft die IDE 1.8.19, mit der ESP-Definition für esp32 by Espressic Systems 1.0.6.
Für höhere Versionen sind diverse Anpassungen im Setch notwendig.<br>

Im Sketch steht – im ersten Reiter in der loop - in der Zeile 526<br>
packBasicInfo.ProtectionStatus = 32767;                  // 111111111111111 alle Fehler<br>
damit werden zum Testen alle Fehler-Flags gesetzt, das muss im Betrieb auskommentiert werden.<br>
In Zeile 22 bzw. 23 wird NodeMCU32 oder TTGO definiert,<br>
es werden einige Ports und Farben passend definiert.<br>

Andere Displays müssen angepasst werden. Es ist auf ein JBD-BMS abgestimmt,<br>
andere Protokolle müsste adaptiert werden.
Es gibt noch einige kleinere Probleme:<br>
Zeile 162 im  BLE-Modul der Aufruf<br>
pRemoteService = pClient->getService(serviceUUID);<br>
bei schwachem BLE Signal hängt sich da etwas auf.<br>
Im Modul Kurven, Zeile 49, wird der Bereich der CSV-Datei<br> der für die Kurven gelesen wird auf<br>
40000 Bytes festgelegt, das sind ca. 3 Tage. Mit mehr ging es nicht....<br>

Und ohne BMS bezw. Bluetooth-Verbindung geht auch nicht viel 😉.<br>
In der Arduino-IDE <br>
  Board ESP 32 DEV<br>
  Flash Size 4 MB<br>
  Partition Scheme "NO OTA/2 MB App 2 MB SPIFFS"<br>
  oder<br>
  Partition Scheme "minimal SPIFFS/ 1,9MB App with OTA/ 190 kB SPIFFS"<br>
einstellen. OTA geht grundsätzlich, aber dann ist fast zu wenig SPIFFS da.<br>
Viel Erfolg.
