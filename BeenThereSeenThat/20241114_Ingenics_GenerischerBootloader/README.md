# 20241114 - Ingenics - Generischer Bootloader
* Alexander Bergner

## Anforderungen
* FBL soll Mutlibaning, Recovery unterstützten
* in nichtflüchten Speicher schreiben
* Failsafe, downgrade sicherheits und konsistenz schultzalgorithmen
* FBL ist portierbar auf verschieden e MCU: angefangen STM32F4
* FBL verhindert flashen von inkompatiblen applikationen
* bank: 1 slot fuer eine applikation
* erst wenn authentizität und ineriät sichegestet ist, wird geladen
* gültigkeit: signatur: ECDSA und RSA
* implementiert, so dass die business logic fest ist, nur die treiber (unterster layer) zB. wie man in flash seichert oder löscht, welche schnittstellen, send receive, timer ..
* Aurix TC357?
* two stage bootloader: primary recht klein, ydass es auch in den OTP speicher (one time rogrammable) passt
* secondary stage: kommunikation mit externen flash tool, kann auchnue apps flashen
* flags: flag/markeirung im ram zwecks speziellem wert an spezieller adresee; dann software reset - flag prüfen und neu eapp flashen
* anwedungen müssen nach ähnlicher art an bestimmter stelle ei "gultig flag" setzen
* live demo: mit erfolgreichem flashen und auch mit unterbrocenem
  * bisher nur externern flash: aber intern auch möglich
  * dynmaische bank-size wäre auch eineoption
  * GD32 als entwicklungsboard
  + wenn RAM ggroß genug wäre, knnte man auch über RAM flashen
  * HILT: ycush um serielle schnittstelle zu unterrechen
