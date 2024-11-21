# 20241121 Dann machen wir halt schnell eine digitale Signatur dran .. - Dr. Markus Wamser
* Ingenics Expert Session
* mehr Personal in der Security benötigt; bis 1530 in Ingolstadt eine Vorlesung gehalten

## Code RED: raio equipment directive
* warum jetzt alle secure boot haben wollen
* s§4 A3-8 und A9; Sicherheitsneinreichtungnen, Schutz vor Betreug; nur solche Software ladbar, welche konform ist
  * dort steht erstmal kein SecureBoot drin
* 2022 Delegierte Verordnung EU 2022/30 der Kommission
  * mit dem Internet verbundene Funkanlagen
  * ab 01.08.2024 gültig - initial; jetzt ab um ein Jahr verschoben, also 01.08.2025
* CRA auch seit vorgesern im europäischen Amtsblatt


## Secure boot
* hash (fused) über Frimware, welche in ROM code; wird dann beim start geprüft
* hash ist eingebrannt: nicht mehr veränderbar
* falls nicht passt, dann Halt mit gegebenenfalls einer Message
* falls aufwendiger: Update von der Firmware ... aber dann stimmt dre eingebrannte Code nicht mehr ... was dann?

## alternative:
* public key-verfahren; privaten behalten, public verteilen
* pub-key is fused: check signature, then check hash, then pass control
* if one fails, then abort the mession
* der entickler kann das auf seinem eigenen laptop machen: und fertig?
  * aber was, wenn dieser laptop abhanden kommt?
  * oder mitarbeiter kündigung -> hat eine kopie des schlüssels -> compliance probleme
  * vertraulichkeit sicherstellen! nur einmal und nicht kopierbar
* best practise: sichere schlüsselablage
   * nitrokey: hsm1-sticks? 60-100 €
   * einsatz von separatem schlüsselspeicher als separate physische einheit
   * ausschliessliche verarbeitung von daten mit dem schlüssel und keinen diretekn zugriff auf den schlüssel
   * falls zertifizierung notwendig ist dann 4stellige beträge
   * aber bei brandhscäden nicht abgesichert (siehe produkthaftungsgesetz) - business continuity managment (was ist das?)
   * bei Großsschadensereignisse: offiste backup - nicht mit der Post schicken
* organisatorische planung wichtig um zu bestmmen, ob man das gestemmt bekommt
* best practise: hochverfgbare schlüsselablage: nitrokeys können auch verschrnänkt werden bei initialisierung
* falls in tresor gelagert: geht, aber nicht praktikabel
* alternative: zentral gemenagten service anbieten
* vier augen prinzip für entwickler: gute idee für die developer experience
* best practice: automatisierte signing pipeline:
  * signing pipeline (DevOps)
  * Signing Server
  * Signing Service
  * Firewalls
  * merer eEntwicler invlviert:
  1 devops engineers
  2. firmware engineers
  3. it-admins
  4. security engineers

## was wäre wenn sich keiner um  das schlüsselmanagemtn kümmert?
* was bei erher eteilen, welche vo unterschiedlichen zulieferern kommt?
* 2 aus 3 prinzip: so dass auch leute mal abwesend sein können; auch personalwechsel machbar
* das braucht dann auch dokumentierte prozesse um so etwas erneut zu erzeugen
* transparenz sicherstellen: vier-augen-prinzip; auditierbarkeit
* best practise: erzeugung der schlüssel in einer eremonie
  * dedizierter prozess für die erzeugung
  * zeremoieportokoll
  * doppelbesetzung der rollen
  * aufbau einer public key-infrastructure (PKI)

* secure boot versus secure update (für die metadaten)
* ARM-chips mit trustzone können sich auch darüber identifizieren
* imx-Plattform erlaubt bis zu vier fusekeys: muss dann auch sichegestellt werden, dass ein aufragsferiger da nicht noch einen zusätzlichen key reinpackt ..
* soides sclüsselmanagement nd die integration der signing-prozesse in den ci-workflow st kein hexenwerk
* akzeptanz und einbindung dr entwickler ist notwendig

* Entwicklungsprozess: kein Merge ohne Code-Review; signierte Commits; in Verbindung mit 4 uage prinzip hebt das die hürde an
* secure testing: schliesst teilweise auch das problem erhöhen
* ebenfalls auch die eigenbundenen abhängigkeiten tracken und nachstellen
* security: mmer wieder anpassen; schleife "wo stehe ich, was kann ich verbessern"
* bei safety hingegen nur ein einziger erfolgreicher check notwendig
* je grßer die softwarebasis, desto größer die notwendig zum update
