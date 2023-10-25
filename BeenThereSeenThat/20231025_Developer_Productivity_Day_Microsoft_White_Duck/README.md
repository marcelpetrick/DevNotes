# 20231025 Developer Productivity Day - Microsoft, White Duck
* event by White Duck
* hosted by Microsoft

## Introduction
* markus suemmchen, white duck <-- TODO needs correction
* christina von github <-- TODO needs correction
* Prof Dr. Alexander Pretschner <-- TODO needs correction
* Shqiponj Alidemi, MS Deutschland <-- TODO needs correction

![](img00.png)
![](img01.png)

## Keynote: Prof. Dr. Alexander Pretschner - Was bedeutet ChatGPT?
* Bayrisches Forschungsinstitut für Digitale Transformation
* "Für uns alle - und im Software Engineering"
* Thema aufmachen, Gesellschaft, SW-Engineering
* Scherz: sie kann drei Dinge nicht, karten mischen, kraulen und pfeifen: aber alles andere ..
* Diskursverschiebung: KI kann alles, man muss es einhegen - aber macht das Sinn?
* Wie gut ist KI? Deepfake Challenge 2020 mit 1 Mio Preisgeld; erknnung von DeepFakes, mit Accuracy 65% - ist das jetzt gut?
  * gute Deepfakes, aber keine gute Detektionssoftware
* kein hinreichend gutes Verfahren mit ChatGPT erzeugte TExte zu erkennen
* keine App, die Börsenkurse vorhersagen kann, dass man investieren kann
* Moratorien starten um die KI, welche mit Nuklearwaffen verglichen wird, zu stoppen
* "Kinder fragen: wisst ihr das? ja, klar. Aber hatten nur Angst, dass ich es ihnen erkläre."
* ChatGPT als Reflexionstool; aber nur machbar, wenn jemand nicht sofort abschaltet
* ChatGPT wird manchmal auch Quatsch erzählen, daher muss man sich darauf einlassen und kritisch aufnehmen
* alle  Medien als Inut und für Output nutzbar: multimodal
* Funktionsweise: neuronales Netz, Encoder-Decoder-Architektur; ChatGPT nur Decodernetzwerk
* GPT-3.5 rund 100 Schictehn mit 175 Mrd. Verbindungen
* Aber: was heisst Qualität, wenn man für eine bestimmte Sequenz von Wörtern das nächstwahrscheinliche Token?
* Chancen:
  *  Chatbbots, virutelle asistenten, texterzeugung, codeerzugung, bild- und filmerzeugnung
  * der Use-case sorgt dafür, dass Digitalisierung funktioniert - siehe Großeltern und Whatsapp
  * Wikis read-only? wird erstellt, aber nicht gelesen; wäre ein chatbot nicht hilfreicher?
* Idee: Fehlerdatenbanken zur Auswertung nutzen
* Resultate nicht perfekt, aber mit menschlicher Prüfung und Überwachung recht hilfreich
* werden wir alle Prompter? Vielleicht anders stellen: "sind wir alle googler?" na klar
* Anwendungsideen:
  * alternative suchmaschine
  * texterstellung
  * dokumentation
  * präzisierung von texten
  * Excel-Formeln, Zeitplanung, Ideenspiel, Zusammenfassung

* Drafts von B. oder Masterarbeiten, so dass er als Prof dazu auffordert: Pack das bitte mal in ChatGPT - sonst muss er selber die Arbeit der Maschine machen
* auch zur Hausaufgaben oder Klausurerstellung nutzen
* kontrafaktische Analysen durchführen - TODO for me
* was lehren oder lernen wir? grundlagenwissen gut durch KI vermittelbar und auch prüfbar; nachvollziehbarkeit der erstellten artefakte notwendig, urteilsfähig sein
* durchblick durch den sprachlicehn nebel, vergleicht mit Latein
* Informatik: Verschiebung vom Schaffenden zum Überprüfenden. Geht das vielleicht schneller?
* Kompetenzorientierung bei Pisa/Iglu debattierbar .. keine Verbersserung der Ergebnisse in den letzten 20 Jahren
### Kennzeichnung von Quellen
* Verwendung von generierten codeerzugung
* Google für Snippets verwenden und die ersten fünf Treffer dann als Quelle verwenden?!? (Einwurf: das kann man automatisieren..)
* Urheberschaft: sollte respektiert werden
* im Deutschen nur Mensch kann Urheber sein; keine Maschine
* die Frage ist, wenn man sich durch Ideen inspirieren lässt: ist das schlimm, wenn man es weiterträgt? Vergleich zu alten MEistern: "aus der Schule von.."
* Dokumentation: Arztbrief und Klageschriften; auch eklatante Fehler in den USA; aber da auch vorher schon template-baisertes Arbeiten
* Grund der Doku: Accountability - das ist der Zweck
* Wenn man die Doku automatische erstellen kann, macht es dann noch Sinn, dass die Doku existiert
* LLMs extrem gut im Vergleich bei standardisierten Tests; im ersten oder zweiten Perzentil
  * Kritik: wel unklar ist, wieviele Fragen man für das Training verwendet hat
* github.com/LudwigStumpp/llm-leaderboard <-- todo: check this
* ähnliche Ergebnisse auch für Bayern: Schulabitur oder auch Bachelorvorlesungen an der Uni

### Letzlich entscheiden: gut genug?
* kontextabhängig
* kind ohne Zugang zu jemanden um über schulstoff zu reden
* kommunikation mit demenzkranken
* kommunikation mit kleinkindern
* In jedem Fall: zum erzeugen von Vorschlägen sehr gut geeeignet - mit Überprüfung durch Sie!

### Risiken
* bewusste oder unbewusste Irreführung: Deep Fakes, Halluzinationen
* möglicherweise rassisstische, frauenfeindliche, beleidigende und anderweitig inadaquat texte
* verlust: geistiger regsamkeit: deskilling, verlassen auf maschinen bei arztbriefen, ..

### Software engineering
* nicht nur kodieren; sonddrn konzete in realwelt erkennen und im code umsetzen
* alte konzepte gut machbar, neues ... braucht noch Zeit
* Requirements engineering: erste Versuche
* codieren, erklärn, refactring, optimieren, migrieren, reparieren
* abap programmiersprache? todo

### zentrale Ideen
* heterogener qualität der ergebnisse
* DORA-Kriterien für die messung der produktivität
* wir sitzen im Fahrersitz, aber wir können schneller fahrne
* Begriff der Urteilsfähigkeit kann früher geprägt werden

## Accelerate Developer PRoductivity - ShqiponjAlidemi
* Warum sollten Sie die Produktivität der Entwickler steigern?
* fast 100 M+ developers; 4M organsations
* github gehört microsfot, abseits davon gibt es noch azure devops
* 2023 magic garnter quadratng: mitcrosoft und gitlab als visionaires und leaders
* copilot chat - wie chatgpt TODO ausprobieren
*  was ist devops? union zwischen people, processes und products
* Common pain points across the market:
  * tools sprawl to accomodate developer repferences
  * time spent onboarding, task switching and troubleshooting
  * siloed teams and projects
  * security and increased risk
  * expensive solutions and a fragmented procedure procurement experience
* todo: check shift left - sichrheitsaspekte(?)
* github advanced security: alles relative neu
* github platform: powered by ai; neben reinen collaborations aufgaben; erstellung von codespaces soll schnell gehen
* (githeb event in zwei wochen - eventuell virtuell anmelden)
* copilot enables faster coding; 55%; 46% of the code is written with the help of copilot; ore than 1 m developers
* copilot verbindet openai, microsoft und github
* copilot for business wird keine daten leaken
* 562% ROI within three years; extrem große zahl - als total economic impact
* 66% in decrease of time to market, reduction in time to remediate, ..
* roundtable der github-legal; eigene firmenanwälte hinschciekn zwecks rücksprache; gerade wichtige bei lizenzierungsproblemen
* use cases: reduction time with onnoarding task switching, better collaboration in siloed teams and projects; shifting left with security and risk mitigation; one solution and an aligned procurement experience

## Die Vorteile der Anwendungsentwicklung mit Github Copilot - Martin Brandl
* wie schafft man in der gleichen Zeit mehr? und auch sicerer und qualitativ ansprechender
* vergleich zu lochkarten vor ueber 50 jahren versus aktuelle IDEs mit HoDebugging, IntelliSense, ..
* why copilot, wat you need, example..
* effizienter, mehr im Flow, produktiver .. sagen Entwickler über ihrer Erfahrungen
* Aufgabe: Webserver in Javascript zu bauen
  * nochmal das 95 Entwickler-Beispiel
* copilot seat: free for opensource (maintainer); business variante hat zugriff auf mehr preview-features
* supported: visual studio, code, vim, neovim, jetbrains IDEs, azure data studio
* VS Code: unten rechts an Octocat ansehbar

### beispiel: verwendung mit powershell: aufgabe: skript, welches die komplexität eines passwortes überprüft
* neue datei: fun.ps1
* erster Vorschlag nicht hilreich, weil keine direkte Verwendung der Variable geplant; aber erstmal Kommentar schreiben: Was beduetet ein sicheres Passwort?
* er will ein Regex: wird automatisch erzeigt in weniger als 1s
* copilot chat: färbung der zeilen für die ausgabe: direkter vorschlag, copy&paste, done
* nächste frage mit copilot chat: show missing policies: auch ein guter vorschlag
* testerzeugung: /tests -> brauchte aber noch die anweisung bitte alle alternatien abzudecken; lief dann
* ergebnis in 15 min statt 1h für einen erfahrenen entwickler

### tipps
* keep certain relevant tabs open in the IDE to tell this context to the IDE
* use good coding practices
* use descriptive variable names and functions -> better results
* follow consistent coding styles and patterns

## Can I use copilot to create code in a business context?
* .. and should I worry about copyright claims? or even copyleft-force
* statement von microsoft: ja, kann man ohne bedenken einsetzen, dann übernimmt microsoft den fall und alle verbundenen kosten <-- extrem wichtig
* copilot copyright commitment von microsoft
* see: githubnext.com
* Copilot for Pullrequests; for Docs; Copilot Voice (mit dem ding reden); Copilot for CLI - dürfte recht hilfreich sen bei den Unterschieden
* CTRL+Enter um ein Fenster mit mehr Vorschlägen zu erhalten
* oder Kommando /explain
* achtung: deprecation-problem; also vorschläge basierned auf der "mehrheit" im internet -> neuerungen sezten sich erst nachfolgend durch
* nachfolge frage: wie oft wird copilot im hintergund aktualisiert - unklar TODO
* copilot explorer: some reverse engineering - how does it work

## Der gesamte DevOps-Lebenszyklus - Nico Meisenzahl
* hilft den Kunden ihre Anwendungen in die Cloud zu bekommen; DevOps-Schiene
* "The tools you need to build what you want."
* Unify your DevOps lifecycle with Github
* your environment at your fingertips with github codespaces
* collaborate with your fellows with issues and PRs
* manage your team with github projects
* automate everything with github actions
* artefakte bereistellen ebenfalls möglich; komplett integriert in einer plattform
* cyber security: integrated into all stages

### github codespaces
* "dev environments that just work" - kein aufwand dependencies vorzubereiten
* ready-to-go developer environment in the cloud
* fully integrated in your favorite IDE orabstracted in your browser
* secure by design
* faster than your laptop
* auch als runtime in eigene IDE (jetbrains..) einzupacken
* TODO definitiv checken wie man das einsetzen kann
* devcontainer.json als basis
* wird später auch beim hackathon genutzt

### github actions
* es gibt vordefinierte Actions, die schon existieren: Chance, dass man etwas vorgefertigtes findet, ist sehr groß
* auch eigene Actions zu erstellen, bringt auch extremen Aufwind

### DevSecOps
* early vulnerability detection aka "shift left"
* cntinuous security testing & streamline drisk management
* greater business agility & faster delivery aka "fail-fast"
* increased collaboration
* gleich während man ein feature entwickelt, kann man dort nachbessern, gegenarbeiten, falls etwas unsicher ist
* siehe: dependabot
* how can github help?
  * security policy
  * security advisories
  * dependabot alerts and security updates
  * dependabot version updates: packages, ..
 * dependency graph
 * secret scanning alerts for partners (public repos only) - azure könnte zB. einen Storage-key direkt invalidieren
* Github Advanced Security features:
  * CodeScanning, codeQL
  * available for free for public repos n github.com - ok, mal checken
  * secret scanning; denial on push

### demo time
* see github meisenzahl/gh-demo
* ganzer lifecycle fon entwickler über devops-mensch
* erstellt erst issue "redis cache" with information
*  automatische projectsortierung und label - passiert automatisch
* dependabot liefert auch drei warnungen
* dependabot.yml in .github im repo: dort parameter festlegen wie etwas arbeitet
* code spaces: erstellt sich in sekunden; lief im browser
* versuch secrets zu pushen im commit - wird verweigert, steht dann auch im git commit
