# 20251113 ingenics: unit testing

* Design, Coding, Prechecks, Versionierung, Build und Testautomatisierung, Statische Codeanalyse, Unit Testing, Deployment, Funktionale Systemtests
  * Für statische Codeanalyse: Cppcheck verwenden, diverse andere Open-Source-Tools
  * Komponenten, welche man simulieren kann, ermöglichen Tests ohne Hardware – HILT durch SILT ersetzen

* Anforderung:
  * Toolevaluierung notwendig
  * Nachvollziehbarkeit (des gesamten Entwicklungsprozesses): falls Normung gefordert ist durch den Branchenhintergrund
  * HW-Unabhängigkeit: muss egal sein, auf was es läuft; Unterschiede Windows, Linux, FPGA, Embedded Linux Board?
  * Lokal und serverbasiert: Ausführung lokal, egal welche Unterlage; Steuerung aus der Cloud
  * Amortisierung ab zweitem Projekt gegeben
  * Hardware nachbauen: SIL (Akkupack, welcher serielle Schnittstelle kommuniziert, einfach ersetzen)
  * Nicht zertifizierbar, weil Toolings nicht zertifizierbar – aber dafür die billige Variante
* HILF (RPi), schaltbare Steckdose, steuerbare Spannungsversorgung, schaltbares USB-Hub (Abstecken simulieren: Enumeration geht verloren); digitales Oszilloskop (Strommessung beim Anfahren, Spannungsverläufe); Bluetooth (ESP32 perfekt zum Nachstellen; Out of Reach; Spannung wegnehmen, wieder geben – Fehler finden); Dauertests kann man damit ebenfalls umsetzen
* Testrunner basieren auf Pytest (Asserts weiternutzen, Test Reports, 90% der Entwickler hatten Python an Schule, Uni ... daher Vorerfahrung gegeben); Testdurchführung und Reporting gleich miterledigt

## hardware
* USB Hub: Yepkit YKUSH <-- check: ubs husb
* Desktop PSU: Siglent
* MQTT-basierte IPC zwischen den Services
* Bluetooth über MicroPython

## geplant
* Grafana Dashboard
* Echtzeitmessungen?

* Funktionale Sicherheit: Was muss man erreichen, um SIL2 zu erreichen (was ist das überhaupt)?
* ISO/IEC 29119: Ab 2007 entwickelt als Testing-Norm: I liefert Fachbegriffe (95 Stück); Top-Down-Approach; firmenweite Strategie; III man muss dokumentieren; IV beschreibt Testverfahren: wirklich klasse

* Parser für Bootlog/Screen: Test recht schnell gemacht

## Wwas bietet ingenics -- aber auch gut zum Abkupfern
* Softwarequalität von Projektbeginn an sicherstellen
* Konzept und Realisierung von Frameworks
* Methodik
