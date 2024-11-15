# 20241114 - Ingenics - Generischer Bootloader
* Alexander Bergner

## Anforderungen
* FBL soll Multibanking und Recovery unterstützen
* In nichtflüchtigen Speicher schreiben
* Failsafe-, Downgrade-Sicherheits- und Konsistenz-Schutzalgorithmen
* FBL ist portierbar auf verschiedene MCUs: angefangen mit STM32F4
* FBL verhindert das Flashen von inkompatiblen Applikationen
* Bank: 1 Slot für eine Applikation
* Erst wenn Authentizität und Integrität sichergestellt ist, wird geladen
* Gültigkeit: Signatur mit ECDSA und RSA
* Implementiert, so dass die Business-Logic fest ist, nur die Treiber (unterster Layer), z. B. wie man in Flash speichert oder löscht, welche Schnittstellen, Send/Receive, Timer ..
* Aurix TC357? <-- check: Confirm if this is a requirement or a question
* Two-Stage Bootloader: Primary recht klein, sodass es auch in den OTP-Speicher (One-Time Programmable) passt
* Secondary Stage: Kommunikation mit externem Flash-Tool, kann auch neue Apps flashen
* Flags: Flag/Markierung im RAM zwecks speziellem Wert an spezieller Adresse; dann Software-Reset - Flag prüfen und neue App flashen
* Anwendungen müssen nach ähnlicher Art an bestimmter Stelle ein "Gültig-Flag" setzen
* Live-Demo: mit erfolgreichem Flashen und auch mit unterbrochenem
  * Bisher nur externer Flash: aber intern auch möglich
  * Dynamische Bank-Size wäre auch eine Option
  * GD32 als Entwicklungsboard
  * Wenn RAM groß genug wäre, könnte man auch über RAM flashen
  * HILT: Möglichkeit, um serielle Schnittstelle zu unterbrechen <-- check: Confirm if "ycush" was intended to be "HILT" or another term
