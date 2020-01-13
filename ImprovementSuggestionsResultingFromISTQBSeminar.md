# Requirements
- **aufschreiben!**
- **Review der Anforderungen** vor dem Start des Tickets (also nicht nach Schätzung, sondern bevor es in die Effort Estimation kommt)
- Reviews mit getrennten Rollen
- **Testbarkeit ein Entwicklungskriterium** - Testautor bei Spezifikation einbezogen?
- Testaufwände vorher abschätzen und einplanen

# Testdurchführung
- Testrollen vergeben - testen unter bestimmten Gesichtspunkten
- Testausführungsplan
- Fehlerchecklisten
- derzeit sehr viel erfahrungsbasiert und intuitiv; teilweise auch als erweiterter Smoketest.

# statische Codeanalyse
- **Warnungsfreiheit** (Compiler ist ein Mittel der statischen CA; daher sollten die Warnungen auch ernst genommen werden; Beispiel Linksverkehr und "aktuell freie Spur", aber Code trotzdem nicht wohlgeformt)
- eventuell cppcheck und andere Tools stärker einbeziehen

# "Testen" (vor Release)
- gibt es vor Releases einen **Testausführungsplan** oder "Alles"?
- Regressionen (gezielt; bestimmt durch **Auswirkungsanalyse**), und Fehlernachtest; Wartungstest (Umgebungsänderung)
- Testkonzept & Endekriterium: Abbruch bei so und so vielen Fehlern von Klasse 1? Wie wird Eingaben-, UI-Element-Überdeckung gemessen, Eingaben Grenztwertanalyse?
- **Risikomanagement**
- Priorisierung der Fehler, so dass man nicht mit Illusion "nur komplett fehlerfreies Produkt wird releast" herangeht: **"testen kann Fehlerfreiheit nicht nachweisen!"**
- **Fehlerbericht-Template:** sollte Daten zur Ausführungsumgebung beinhalten, welche Installer-Version, Fehlerwahrscheinlichkeit (immer, sporadisch), Reproduzierbarkeit?, Ablauf zu Fehler, Link zu Testdaten

- **Testautomatisierung**: Ende-zu-Ende-Test [currently in progress]
