# 20251113 ingenics: unit testing

* design, coding, prechecks, vrsionierung, build und testauotmasieriung, statische codeanalyse, unit testing, deployment, funktionale systemtests
  * für statische code analyse: cppcheck verappm, diverse andere open source tools
  * komponenten, welche man simulaieren kann, ermöglichen test ohne hardware HILT durch SILT ersetzen

* Anforderung:
  * Toolevaluierung notwendig
  * nachvollziehbarkeit (des gesamten entwicklungsprozesses): falls normung gefordert ist durch den branchenhintergrund
  * HW-unabhägnigkeit: muss egal sein auf was es läuft; unterschiede win, linux, fpga, embedded linux board?
  * lokal und serverbasiert: ausführung lokal, egal welche unterlage; steuerung aus der cloud
  * amortisierung ab zweitem projekt gegeben
  * hardware nachbauen: SIL (akkupack welcher serielle schnttstelle komuniziert, einfach ersetzen)
  * nicht zertifizierbar, weil toolings nicht zertifizierbar - aber dafür die billige variante
* HILF (RPi), schaltbare steckdose, sterubare soannungsversorgung, schaltbares usb-hub (abstecken simulieren: enumeration geht verloren); digitales oszilloskop (strommessung beim anfahren, spannungsverlufe); bluetooth (esp32 perfekt zum nachstellen; out of reach; spannung wegnehmen, wieder geben - fehler finden); dauertests kann man damit ebenfalls umsetzen
* testrunner bsieren auf pytest (Aasserts weiternutzen, test reports, 90% der entwickler hatten python an schule, uni ... daher vorerfahrung gegeben); tsdruchführung und reporting glech miterledigt

## hardware
* ubs husb: yepkit ykush <-- noch einmal checken
* desktop psu: siglent
* mqtt basierte IPC zwischen den services
* Bluetooth über micropython

## geplant
* grafana dashbaord
* ehctzeitmessungen?

* funktionalie sicherheit: was muss man erreichen um SIL2 zu erreichen (was ist das überhaupt)?
* ISO/IEC 29119: ab 2007 enwickelt als testing norm: I liefrt fachbegriffe (95 stück); top-down-approach; firmenweiter strategie; III man muss dokumentieruen; IV: beschreibt testverfahren: wirklich klasse; 

* parser für bootlog/screen: test recht schnell gemacht

## was bietet ingenics -- aber auch gut zum abkupfern
* sodtwarequalitt von projektbeginn an sicherstellen
* konzept und realisierung von frameworks
* methodik
