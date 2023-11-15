# 20231115 Der Cloud-native Product Owner

* Hosted By Mick und Martin R.
+ Mick im net


```
# Die Rolle des Cloud-Native Product Owners und die Vorteile der Cloud-Nutzung

Du fragst dich, was ein Cloud-Native Product Owner ist und welche Herausforderungen du in einer agilen Entwicklungsumgebung meistern musst? Oder du bist neugierig auf die Vorteile der Nutzung von Cloud-Diensten für dein Unternehmen?
Johann-Peter Hartmann geht in seinem Vortrag auf das Konzept des Cloud-Native Product Owners ein, diskutiert seine Bedeutung in einem agilen Umfeld und hebt einige spezifische Herausforderungen hervor, denen du in der Cloud-Umgebung gegenüberstehst. Darüber hinaus werden auch die zahlreichen Vorteile untersucht, die Unternehmen durch den Einsatz von Cloud-Services erzielen können – von finanziellen Einsparungen über Effizienzsteigerungen bis hin zu verbesserter Flexibilität und Skalierbarkeit.
Diese Themen sind besonders relevant in unserer zunehmend digitalisierten Welt, wo Agilität, Kosteneffizienz und schnelle Anpassungsfähigkeit entscheidende Faktoren für den Geschäftserfolg sind.

Ablauf

    17:50: Wir öffnen den Zoom Konferenzraum
    18:00: Begrüßung
    18:05: Start des Vortrags von Johann (Q&A im Anschluss)
    ca 19:30: Ende & Ausklang der Veranstaltung

Wir freuen uns auf den Vortrag und viele Teilnehmende :-)
```

# Johann Hartmann - von Mayflower
* 48 Folien vorbereitet ..
* der PO macht alle relevanten Entscheidungen; aber bei "cloud" kann man alles fortlaufend enthscieden (weil elatisch)
* agiles manifest auf dem rücken tättowiert trägt
* beste anforderungen und entwürfe entstehen in agilen teams: selbstorganisiertend
  * wer hat den Hoster ausgesucht?
  * wer hat die datenbank oder sprache ausgesucht?
  * wer trift die make or buy Entscheidung?
TODO image
* früher hatte das einen guten Grund, weil höhere Reichweite
* aber jetzt: cloud-basiert
*  beispiel AWS:
![](img02.png)
*  mehr Effizienz, geringere Kosten, ... er merkt dies noch nicht
* von CapEx zu OpEx - Kernwechsel: BWL und technisches braucht gleiche Gehirnbereiche
* vor cloud: Capital Expenditures
  * ich bezahle alles, was wir mal brauchen jönnten
![](img03.png)
* nicht nur HW an sich, auch die Einrichtung, etc. kostet alles
* cloud: operational expenditures
  * ich bezahle nur, was ich gerade nutze; pay as you go; flexibel und direkt anpassbar; finanzielle Entwicklung nicht vorhersehbar
  * wenn der container läuft während niemand etwas tut, dann ist das ein Server!
### Folgen:
* Budgets sind nicht mehr da: weil nicht vorher allokierbar
* warum sollte man dann noch in Budgets und Investments denken?
* die Architektur ist nicht mehr da: technologieentscheidungen werden on demand getroffen; das gilt für Einführung, Beednigung, Wechsel von Technologien
* "die Applikation" ist nicht mehr da: dank SaaS, Lambda, MicroServices Verteilung bis auf Featureebene hinunter
* die Grenzen meiner Software sind nicht mehr da: alles inst integrierbar, alles ist eine API, dan SDK und DevEx: Integration geht schnell; weniger Reuse von Soiurce code, sondern von software applikationen
* non-funktionale Capabilities sind jetzt eh.da: früher teuer, jetzt mit in der Tüte
  * skalieren, security, Ausfallsicherheit, Backup -> wenn man skalieren will, tut man das einfach
* Cloudversprechen: zehnmal weniger SW-Kosten: einfach 90% der Arbeit weglassen
![](img05.png)
* dinge, welche man nicht selber macht, sind eh dinge, welche man sparen sollte
* Was sollte ich denn alles weglassen? falls man sich entscheidet kostensparend zu arbeiten, dann kann ich das machen - aber wie trifft man diese enthscieudng
  * DDD - domain driven design-guys:  either core, supporting oder generic
* ![](img06.png)
* falls es trivial ist, was man macht, was andere machen, dann ist man schnell ausgetauscht - siehe ganze AI-Startups
* supporting domain: unterstütuzt nur die core-domain;: kann spezifische aber unkritische lösungen enthalten (wie zum beispiel: reporting)
* reduziert die komplexität der core-domain
* kann flexible off-the-shelf-Lösung sein
* user management war früher teil der lösung: heute kein sinn mehr; nur einkauf-lösung, off-the-shelf (aber anpassbar)
  * Beispiel: anpassbarer Meister: SAP
* general domain: standardisierte lösungen, die Pflicht sind; entwickler mögen es, aber keine Prio
* Frage: welche Domains sollte ich selbst machen, welche nicht?
 * Core-Domain: selber machen:; supporting aussuchbar (Services, SaaS), General Domain (SaaS) - auf gar keinen Fall selber machen
  * falls man kein Hoster ist, sollte man nicht selber hosten

## Was bdeutet das für mich als Product Owner?
* lohnt sich das Feature?
 * wenn ja: auf welcher Plattform am meisten?
 * Kosten pro Feature: on premises, cloud/container oder SaaS/Service
 * in cloud für LLM-Dienste sehr viel einfacher verfügbr als wenn man erst die GPUs beschaffen muss
 ![](img07.png)
* operative Kosten versus maintenance versus initiale entwicklungskosten: definitiv entscheidende Punkte
* andere formen von Kosten: kosten pro Feature
* opportunitätskosten für leerlauf; cost of delay, skalieren, feature wieder entfernen
  * cloud gewinnt überall: alles sehr niedrig; auf Blech alles sehr teuer; bei Service auch niedrig
 ![](img08.png)
* größte kosten entstehen aus maintenance phase; also anpassungen und wartungen
* nur sieben prozent die initialen entwicklungskosten; testing mit 15% auch teuer; requirement engineering auch recht preiswert
 ![](img09.png)
* Woher kommen die Maintenance-Kosten

###  Konvergenzschritt:
* Case: wir brauchen ein user-management.optiinen
 * selbstgebaut
 * Authentik als Container?
 * Cognito auf AWS? (hat Analgoien auch bei Azure oder GCP)
 * Auth0 als Service?
* folgend: was sind die Entwicklungskosten, anpassbarkeit, betriebskosten pro ahr, Skalierbarket, security, cost of delay?
* wen muss ich dafür fragen? wer kennt den Bedarf?
![](img10.png)
   * das sind Fragen, welche in klassischen agilen Teams keine Heimat findet
* Wer hat die verantwortung, dass Value/TCO 8total cost of wonership) stimmen?
  * eigentlich klassische Frage für den PO
* Solution: gewichtetet; Trade-Off-Analyse: bei dem
 ![](img11.png)
 * entscheidungen treffen indem man die informationsdichte erhöht und daaus entscheidungen ableitet
   * informationen zusammenbringen
* resultierende Empfehlung: wird wegen der Skalierbarkeit gewinnen; aber Interne Leute werden eventuell sich übergangen fühlen
  * alle darunterliegenden PArtikularinteressen gibt es noch - aber wenn man darauf hört, hätte man eine ganz furchtbare lösung gehabt
 ![](img12.png)
 * daher braucht man das Wissen von PO und Team um fundierte Entscheidung zu treffen

* ergo: business agilität gibt es nur, wenn der PO und das Team sie machen darf
![](img13.png)
* Nonfunktionale Anforderungen und Optionen verstehen und nutzen: NFRs (als PO muss man sie nicht 100% verstehen, dafür gibt es techniker)
* daher braucht man einen Mechanismus um solche Informationen in die eigene Beerwrtung einzubringen
* architekturentscheidungen sollte man explizit machen und auf Basis von Bsuinessvalue gemeinsam fällen: "Ich mache das weil .." eventuell zu kurz
  *  daher ist das Team in der Pflicht auch in Bereichen des Business-Value zu denken; nicht mehr nur den "Programmcode machen"
* operative Kosten: FinOps etablieren und als Ticket-Quelle nutzen (Analyse von Reporting was die meisten Kosten veraursacht) - ein Prozess, wo man als Team und PO weiss, was sich in welche Richtugn bewegt - und dies als Ticketqzuelle nutzen
* support für diese Themen bekommen, per Triade, Architegkturgilde (teamübergreifend)
* Faizt: der PO und das Team können den Value wirklich steuern. Wenn sie Macht und Support bekommen.
![](img14.png)

## Diskussion
* "Kickoff2" - danach Review

 ---
 * Info: starke Gegenstimme als Zuschauer; elegant darauf eingegangen von Johann Hartmann und souverän die Ausführungen angepasst während des Vortrages
