# 20231025 Developer Productivity Day - Microsoft, White Duck
* event by White Duck
* hosted by Microsoft

## Introduction
* Markus Sümmchen, White Duck
* Prof. Dr. Alexander Pretschner
* Shqiponj Alidemi, MS Deutschland

![](img00.png)
![](img01.png)

## Keynote: Prof. Dr. Alexander Pretschner - Was bedeutet ChatGPT?
* Bayerisches Forschungsinstitut für Digitale Transformation
* "Für uns alle - und im Software Engineering"
* Thema aufmachen, Gesellschaft, SW-Engineering
* Scherz: sie kann drei Dinge nicht, Karten mischen, kraulen und pfeifen: aber alles andere...
* Diskursverschiebung: KI kann alles, man muss es einhegen - aber macht das Sinn?
* Wie gut ist KI? Deepfake Challenge 2020 mit 1 Mio Preisgeld; Erkennung von DeepFakes, mit Accuracy 65% - ist das jetzt gut?
  * gute Deepfakes, aber keine gute Detektionssoftware
* kein hinreichend gutes Verfahren mit ChatGPT erzeugte Texte zu erkennen
* keine App, die Börsenkurse vorhersagen kann, dass man investieren kann
* Moratorien starten, um die KI, welche mit Nuklearwaffen verglichen wird, zu stoppen
* "Kinder fragen: wisst ihr das? ja, klar. Aber hatten nur Angst, dass ich es ihnen erkläre."
* ChatGPT als Reflexionstool; aber nur machbar, wenn jemand nicht sofort abschaltet
* ChatGPT wird manchmal auch Quatsch erzählen, daher muss man sich darauf einlassen und kritisch aufnehmen
* alle Medien als Input und für Output nutzbar: multimodal
* Funktionsweise: neuronales Netz, Encoder-Decoder-Architektur; ChatGPT nur Decodernetzwerk
* GPT-3.5 rund 100 Schichten mit 175 Mrd. Verbindungen
* Aber: was heißt Qualität, wenn man für eine bestimmte Sequenz von Wörtern das nächstwahrscheinliche Token?
* Chancen:
  * Chatbots, virtuelle Assistenten, Texterzeugung, Codeerzeugung, Bild- und Filmerzeugung
  * der Use-case sorgt dafür, dass Digitalisierung funktioniert - siehe Großeltern und WhatsApp
  * Wikis read-only? wird erstellt, aber nicht gelesen; wäre ein Chatbot nicht hilfreicher?
* Idee: Fehlerdatenbanken zur Auswertung nutzen
* Resultate nicht perfekt, aber mit menschlicher Prüfung und Überwachung recht hilfreich
* werden wir alle Prompter? Vielleicht anders stellen: "sind wir alle Googler?" na klar
* Anwendungsideen:
  * alternative Suchmaschine
  * Texterstellung
  * Dokumentation
  * Präzisierung von Texten
  * Excel-Formeln, Zeitplanung, Ideenspiel, Zusammenfassung

* Drafts von B. oder Masterarbeiten, so dass er als Prof dazu auffordert: Pack das bitte mal in ChatGPT - sonst muss er selber die Arbeit der Maschine machen
* Auch zur Hausaufgaben oder Klausurerstellung nutzen
* Kontrafaktische Analysen durchführen - TODO for me
* Was lehren oder lernen wir? Grundlagenwissen gut durch KI vermittelbar und auch prüfbar; Nachvollziehbarkeit der erstellten Artefakte notwendig, urteilsfähig sein
* Durchblick durch den sprachlichen Nebel, vergleicht mit Latein
* Informatik: Verschiebung vom Schaffenden zum Überprüfenden. Geht das vielleicht schneller?
* Kompetenzorientierung bei Pisa/Iglu debattierbar .. keine Verbesserung der Ergebnisse in den letzten 20 Jahren

### Kennzeichnung von Quellen
* Verwendung von generierten Codeerzeugung
* Google für Snippets verwenden und die ersten fünf Treffer dann als Quelle verwenden?!? (Einwurf: das kann man automatisieren..)
* Urheberschaft: sollte respektiert werden
* Im Deutschen nur Mensch kann Urheber sein; keine Maschine
* Die Frage ist, wenn man sich durch Ideen inspirieren lässt: Ist das schlimm, wenn man es weiterträgt? Vergleich zu alten Meistern: "aus der Schule von.."
* Dokumentation: Arztbrief und Klageschriften; auch eklatante Fehler in den USA; aber da auch vorher schon template-basiertes Arbeiten
* Grund der Doku: Accountability - das ist der Zweck
* Wenn man die Doku automatisch erstellen kann, macht es dann noch Sinn, dass die Doku existiert
* LLMs extrem gut im Vergleich bei standardisierten Tests; im ersten oder zweiten Perzentil
  * Kritik: Wel unklar ist, wie viele Fragen man für das Training verwendet hat
* github.com/LudwigStumpp/llm-leaderboard <-- todo: check this
* Ähnliche Ergebnisse auch für Bayern: Schulabitur oder auch Bachelorvorlesungen an der Uni

### Letztlich entscheiden: gut genug?
* Kontextabhängig
* Kind ohne Zugang zu jemanden um über Schulstoff zu reden
* Kommunikation mit Demenzkranken
* Kommunikation mit Kleinkindern
* In jedem Fall: zum Erzeugen von Vorschlägen sehr gut geeignet - mit Überprüfung durch Sie!

### Risiken
* Bewusste oder unbewusste Irreführung: Deep Fakes, Halluzinationen
* Möglicherweise rassistische, frauenfeindliche, beleidigende und anderweitig inadäquate Texte
* Verlust: geistiger Regsamkeit: Deskilling, Verlassen auf Maschinen bei Arztbriefen, ..

### Software Engineering
* Nicht nur kodieren; sondern Konzepte in Realwelt erkennen und im Code umsetzen
* Alte Konzepte gut machbar, Neues ... braucht noch Zeit
* Requirements Engineering: erste Versuche
* Codieren, erklären, Refactoring, optimieren, migrieren, reparieren
* ABAP Programmiersprache? todo

### Zentrale Ideen
* Heterogene Qualität der Ergebnisse
* DORA-Kriterien für die Messung der Produktivität
* Wir sitzen im Fahrersitz, aber wir können schneller fahren
* Begriff der Urteilsfähigkeit kann früher geprägt werden

## Accelerate Developer Productivity - Shqiponj Alidemi
* Warum sollten Sie die Produktivität der Entwickler steigern?
* Fast 100 M+ Developers; 4M Organisations
* GitHub gehört Microsoft, abseits davon gibt es noch Azure DevOps
* 2023 Magic Gartner Quadrant: Microsoft und GitLab als Visionaries und Leaders
* Copilot Chat - wie ChatGPT TODO ausprobieren
* Was ist DevOps? Union zwischen People, Processes und Products
* Common pain points across the market:
  * Tools sprawl to accommodate developer preferences
  * Time spent onboarding, task switching and troubleshooting
  * Siloed teams and projects
  * Security and increased risk
  * Expensive solutions and a fragmented procedure procurement experience
* TODO: Check Shift Left - Sicherheitsaspekte(?)
* GitHub Advanced Security: alles relativ neu
* GitHub Platform: Powered by AI; neben reinen Collaboration-Aufgaben; Erstellung von Codespaces soll schnell gehen
* (GitHub Event in zwei Wochen - eventuell virtuell anmelden)
* Copilot enables faster coding; 55%; 46% of the code is written with the help of Copilot; more than 1 M developers
* Copilot verbindet OpenAI, Microsoft und GitHub
* Copilot for Business wird keine Daten leaken
* 562% ROI within three years; extrem große Zahl - als Total Economic Impact
* 66% in decrease of time to market, reduction in time to remediate, ..
* Roundtable der GitHub-Legal; eigene Firmenanwälte hinschicken zwecks Rücksprache; gerade wichtig bei Lizenzierungsproblemen
* Use Cases: Reduction time with onboarding, task switching, better collaboration in siloed teams and projects; shifting left with security and risk mitigation; one solution and an aligned procurement experience

## Die Vorteile der Anwendungsentwicklung mit Github Copilot - Martin Brandl
* Wie schafft man in der gleichen Zeit mehr? Und auch sicherer und qualitativ ansprechender
* Vergleich zu Lochkarten vor über 50 Jahren versus aktuelle IDEs mit HoDebugging, IntelliSense, ..
* Why Copilot, what you need, example..
* Effizienter, mehr im Flow, produktiver .. sagen Entwickler über ihrer Erfahrungen
* Aufgabe: Webserver in Javascript zu bauen
  * Nochmal das 95 Entwickler-Beispiel
* Copilot Seat: Free for OpenSource (Maintainer); Business Variante hat Zugriff auf mehr Preview-Features
* Supported: Visual Studio, Code, Vim, NeoVim, JetBrains IDEs, Azure Data Studio
* VS Code: Unten rechts an Octocat ansehbar

### Beispiel: Verwendung mit PowerShell: Aufgabe: Skript, welches die Komplexität eines Passwortes überprüft
* Neue Datei: fun.ps1
* Erster Vorschlag nicht hilfreich, weil keine direkte Verwendung der Variable geplant; aber erstmal Kommentar schreiben: Was bedeutet ein sicheres Passwort?
* Er will ein Regex: Wird automatisch erzeugt in weniger als 1s
* Copilot Chat: Färbung der Zeilen für die Ausgabe: Direkter Vorschlag, Copy&Paste, done
* Nächste Frage mit Copilot Chat: Show missing policies: Auch ein guter Vorschlag
* Testerzeugung: /tests -> brauchte aber noch die Anweisung bitte alle Alternativen abzudecken; lief dann
* Ergebnis in 15 Min statt 1h für einen erfahrenen Entwickler

### Tipps
* Keep certain relevant tabs open in the IDE to tell this context to the IDE
* Use good coding practices
* Use descriptive variable names and functions -> better results
* Follow consistent coding styles and patterns

## Can I use Copilot to create code in a business context?
* .. and should I worry about copyright claims? Or even copyleft-force
* Statement von Microsoft: Ja, kann man ohne Bedenken einsetzen, dann übernimmt Microsoft den Fall und alle verbundenen Kosten <-- extrem wichtig
* Copilot Copyright Commitment von Microsoft
* See: githubnext.com
* Copilot for Pull Requests; for Docs; Copilot Voice (mit dem Ding reden); Copilot for CLI - dürfte recht hilfreich sein bei den Unterschieden
* CTRL+Enter um ein Fenster mit mehr Vorschlägen zu erhalten
* Oder Kommando /explain
* Achtung: Deprecation-Problem; also Vorschläge basierend auf der "Mehrheit" im Internet -> Neuerungen setzen sich erst nachfolgend durch
* Nachfolge Frage: Wie oft wird Copilot im Hintergrund aktualisiert - unklar TODO
* Copilot Explorer: Some reverse engineering - how does it work
## Der gesamte DevOps-Lebenszyklus - Nico Meisenzahl
* Hilft den Kunden ihre Anwendungen in die Cloud zu bekommen; DevOps-Schiene
* "The tools you need to build what you want."
* Unify your DevOps lifecycle with GitHub
* Your environment at your fingertips with GitHub Codespaces
* Collaborate with your fellows with issues and PRs
* Manage your team with GitHub projects
* Automate everything with GitHub Actions
* Artefakte bereitstellen ebenfalls möglich; komplett integriert in einer Plattform
* Cyber Security: Integrated into all stages

### GitHub Codespaces
* "Dev environments that just work" - kein Aufwand Dependencies vorzubereiten
* Ready-to-go developer environment in the cloud
* Fully integrated in your favorite IDE or abstracted in your browser
* Secure by design
* Faster than your laptop
* Auch als Runtime in eigene IDE (JetBrains..) einzupacken
* TODO definitiv checken wie man das einsetzen kann
* devcontainer.json als Basis
* Wird später auch beim Hackathon genutzt

### GitHub Actions
* Es gibt vordefinierte Actions, die schon existieren: Chance, dass man etwas Vorgefertigtes findet, ist sehr groß
* Auch eigene Actions zu erstellen, bringt auch extremen Aufwind

### DevSecOps
* Early vulnerability detection aka "Shift Left"
* Continuous security testing & streamline risk management
* Greater business agility & faster delivery aka "Fail-Fast"
* Increased collaboration
* Gleich während man ein Feature entwickelt, kann man dort nachbessern, gegenarbeiten, falls etwas unsicher ist
* Siehe: Dependabot
* How can GitHub help?
  * Security policy
  * Security advisories
  * Dependabot alerts and security updates
  * Dependabot version updates: packages, ..
* Dependency graph
* Secret scanning alerts for partners (public repos only) - Azure könnte z.B. einen Storage-key direkt invalidieren
* GitHub Advanced Security features:
  * CodeScanning, CodeQL
  * Available for free for public repos on github.com - ok, mal checken
  * Secret scanning; denial on push

### Demo Time
* See GitHub meisenzahl/gh-demo
* Ganzer Lifecycle von Entwickler über DevOps-Mensch
* Erstellt erst Issue "Redis Cache" with information
* Automatische Projectsortierung und Label - passiert automatisch
* Dependabot liefert auch drei Warnungen
* dependabot.yml in .github im Repo: Dort Parameter festlegen wie etwas arbeitet
* Code Spaces: Erstellt sich in Sekunden; lief im Browser
* Versuch secrets zu pushen im Commit - wird verweigert, steht dann auch im Git Commit

## Hackathon - The World's Most Widely Adopted AI Develop Tool - Margarita Sanz del Rio (Github)
* Microhack
* MS wants to push everything they have with AI
### The DevEx Experience
* GitHub is built by developers for developers; less focus on collaboration ..
* Focus on the right stuff ..
* Developers are the key resources of the company
* Higher talent retention: High team morale, motivating and rewarding work
* Improved operational efficiency: Drive business performance through increased productivity
* AI is the next frontier in DevEx: says McKinsey study
* The "Copilot Effect" - Maximize developer happiness; productivity, ..
* Copilot works better with much more content
* Copilot is not trained every day & also does not store the used context-code
* What it can: Convert comments to code; autosuggests tests, show alternatives
* Public Beta: Copilot chat piece; command and script explanations, Git command assistance in the terminal; fine tune responses with custom models
* CfB versus CfI: Admin seat management, policy controls, integrated billing and usage report, telemetry policy: Will also give insights how well it is used by the developers
### Time to Hack
* See: [https://github.com/marcelpetrick/CopilotHackathon](https://github.com/marcelpetrick/CopilotHackathon)
* Codespaces aufgesetzt: [https://automatic-bassoon-jj6p5vv4g3qrrr.github.dev/](https://automatic-bassoon-jj6p5vv4g3qrrr.github.dev/)
```
You're signed up for GitHub Copilot Labs!
Thanks @marcelpetrick, you're all signed up for GitHub Copilot Labs!
```
* Nach initialer Einrichtung meiner Codespaces lief dann alles; Vorschläge, Copilot Chat und auch die `Brushes` - Also Standardfunktionen, welche man auf ausgewählte Abschnitte loslassen konnte (Clean, Explain, Document..) - clevere Idee

## round table
* the chat-version is a bit more sophisticated than the comment - because it has more context
* kommend: Stichwort AzureAI

----

## Plan for the post:
* add photos from entrance, door light, slides, maybe the PR, photo of codespaces-IDE
* add summary for each of the talks: 1 sentence?
* make remark about the door-displays and my pitch idea?
* make remark about my genAI-initiative?
* my pull request for the copilot hackathon ..

