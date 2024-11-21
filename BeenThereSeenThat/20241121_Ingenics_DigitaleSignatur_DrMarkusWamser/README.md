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




* question: key rolling?


