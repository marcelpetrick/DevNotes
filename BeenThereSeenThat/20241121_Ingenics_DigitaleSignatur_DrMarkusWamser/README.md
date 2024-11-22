# 20241121 Dann machen wir halt schnell eine digitale Signatur dran .. - Dr. Markus Wamser
* Ingenics Expert Session
* mehr Personal in der Security benötigt; bis 15:30 in Ingolstadt eine Vorlesung gehalten

## Code RED: Radio Equipment Directive
* warum jetzt alle Secure Boot haben wollen
* §4 A3-8 und A9; Sicherheitseinrichtungen, Schutz vor Betrug; nur solche Software ladbar, welche konform ist
  * dort steht erstmal kein Secure Boot drin
* 2022 Delegierte Verordnung EU 2022/30 der Kommission
  * mit dem Internet verbundene Funkanlagen
  * ab 01.08.2024 gültig - initial; jetzt um ein Jahr verschoben, also 01.08.2025
* CRA auch seit vorgestern im europäischen Amtsblatt

## Secure Boot
* Hash (fused) über Firmware, welche im ROM-Code ist; wird dann beim Start geprüft
* Hash ist eingebrannt: nicht mehr veränderbar
* Falls nicht passt, dann Halt mit gegebenenfalls einer Message
* Falls aufwendiger: Update von der Firmware ... aber dann stimmt der eingebrannte Code nicht mehr ... was dann?

## Alternative
* Public Key-Verfahren; privaten behalten, Public verteilen
* Public Key ist fused: check signature, then check hash, then pass control
* If one fails, then abort the mission
* Der Entwickler kann das auf seinem eigenen Laptop machen: und fertig?
  * Aber was, wenn dieser Laptop abhanden kommt?
  * Oder Mitarbeiter kündigt -> hat eine Kopie des Schlüssels -> Compliance-Probleme
  * Vertraulichkeit sicherstellen! Nur einmal und nicht kopierbar
* Best Practice: sichere Schlüsselablage
   * Nitrokey: HSM1-Sticks? 60-100 €
   * Einsatz von separatem Schlüsselspeicher als separate physische Einheit
   * Ausschließliche Verarbeitung von Daten mit dem Schlüssel und keinen direkten Zugriff auf den Schlüssel
   * Falls Zertifizierung notwendig ist, dann vierstellige Beträge
   * Aber bei Brandschäden nicht abgesichert (siehe Produkthaftungsgesetz) - Business Continuity Management (was ist das?) <-- check: Was genau ist Business Continuity Management?
   * Bei Großschadensereignissen: Offsite-Backup - nicht mit der Post schicken
* Organisatorische Planung wichtig, um zu bestimmen, ob man das gestemmt bekommt
* Best Practice: hochverfügbare Schlüsselablage: Nitrokeys können auch verschränkt werden bei Initialisierung
* Falls im Tresor gelagert: geht, aber nicht praktikabel
* Alternative: zentral gemanagten Service anbieten
* Vier-Augen-Prinzip für Entwickler: gute Idee für die Developer Experience
* Best Practice: automatisierte Signing-Pipeline:
  * Signing Pipeline (DevOps)
  * Signing Server
  * Signing Service
  * Firewalls
  * Mehrere Entwickler involviert:
    1. DevOps Engineers
    2. Firmware Engineers
    3. IT-Admins
    4. Security Engineers

## Was wäre, wenn sich keiner um das Schlüsselmanagement kümmert?
* Was bei fehlerhaften Teilen, welche von unterschiedlichen Zulieferern kommen?
* 2 aus 3 Prinzip: so dass auch Leute mal abwesend sein können; auch Personalwechsel machbar
* Das braucht dann auch dokumentierte Prozesse, um so etwas erneut zu erzeugen
* Transparenz sicherstellen: Vier-Augen-Prinzip; Auditierbarkeit
* Best Practice: Erzeugung der Schlüssel in einer Zeremonie
  * Dedizierter Prozess für die Erzeugung
  * Zeremonieprotokoll
  * Doppelbesetzung der Rollen
  * Aufbau einer Public Key-Infrastructure (PKI)

* Secure Boot versus Secure Update (für die Metadaten)
* ARM-Chips mit TrustZone können sich auch darüber identifizieren
* i.MX-Plattform erlaubt bis zu vier Fuse-Keys: Muss dann auch sichergestellt werden, dass ein Auftragsfertiger da nicht noch einen zusätzlichen Key reinpackt
* Solides Schlüsselmanagement und die Integration der Signing-Prozesse in den CI-Workflow ist kein Hexenwerk
* Akzeptanz und Einbindung der Entwickler ist notwendig

* Entwicklungsprozess: kein Merge ohne Code-Review; signierte Commits; in Verbindung mit Vier-Augen-Prinzip hebt das die Hürde an
* Secure Testing: schließt teilweise auch das Problem ein, die Hürde zu erhöhen <-- check: "das Problem ein, die Hürde zu erhöhen" klingt unklar
* Ebenfalls auch die eingebundenen Abhängigkeiten tracken und nachstellen
* Security: immer wieder anpassen; Schleife "Wo stehe ich, was kann ich verbessern"
* Bei Safety hingegen nur ein einziger erfolgreicher Check notwendig
* Je größer die Softwarebasis, desto größer die Notwendigkeit zum Update
