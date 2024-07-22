# collection of ideas

## web scraping
Get all the loved songs from last.fm for an account. Save result as some csv/text for further processing.  
Should be quite easy due to missing authentication.  
**Implemented:** https://github.com/marcelpetrick/pythonCollection/tree/master/MyFirstLastFmCrawler

## Add youtube-songs to last.fm for songs, which have a missing "video" (ergo: no playback)
* no text: idea is still viable

## Set Away/Available mode
* AutoIt-script (most likely) to change the Jabber-status and the RocketChat-status in a synchronized, automatic way

## Markdown-Fixer
* todo: idee: md-files mit File-ending glattziehen (first commandline: inputfile: then check if the line-endings have newline (with two spaces before; except maybe for lines which start with a # or *, because they are wrapped anyway)
  * **Implemented**: via GPT4-prompt. Works well, but is of course not self-contained. No need to spend additioanl ressources at the moment.

## The mother of all gits
Jk, idea is to create a script which retrieves the list of all _my_ (publicly) available git(hub) repositories and then clones them to a specific path. Just to have a local backup.  
I don't want to to this manually for all repos manually.  
Maybe just do baremetal-cloning.  
Implemented: https://github.com/marcelpetrick/codingWithGPT/tree/master/MotherOfAllGits  
**Fixed and improved version which handles private repos as well:** https://github.com/marcelpetrick/codingWithGPT/tree/master/motherOfAllGitsV2

## python-api-access of Azure DevOps
* authentificate
* get all tickets with certain tag (just like usual query)
* check the history of each ticket when it got the "Update3"-tag assigned
* create a graph or structured outout in the form of "date0: ticket1, ticket2, ..; date1: ticket3, ticket; .."
* **Implemented:** https://github.com/marcelpetrick/codingWithGPT/tree/master/azureDevOpsTools

## outlook connector: pull information feom calenser or a person or group, then display as output
* started implementation but frozen due to missing PAT (personal access token) because my current organisation does not allow to create one within their domain, and I have no personal Office365-accoutn which I could use otherwise

## kid's book auto-story-teller
* put a book page under a camera, press "button", get the story told (or the text from the page): use OCR and TTS

## RAG for a chatbot about a product:
* pump in two different ticket-systems, the whole git of two repos, maybe even the sales-documents and then allow to make requests - with resulting pointer to the original document

## kid bookstory teller
take image with camera, do OCR, convert story into age appropriate storytelling, TTS with cloned voice (my own)

## QR code generator and printer
* add possibility to add a log to showcase the error-correction and how safe that algorithm actually is
* maybe even allow to add layers of proctection?

## update my homepage: marcelpetrick.it
* haha
* add photo, make it more convenient to read
* add some context about me - else, keep it short

## fix the wordpress forwarding problem
* someone took over WP - not sure how
* if someone does not use an adblocker, you get forwarded to suspicious pages

## duo/language-learning clone:
* generae level appropriat sentences and word chains for croatian
* give user way to input them, then check /verify via LLM (or even simpler deterministic approach - by usingpre-generated stuff)
* also allow to enter spoke phrases,then correct them
* also generate spoken output and then let the user type (or input by given word blocks) 
  
---------

* edgeML idea: recognition of movement like weight lifting, etc..what would sensor fusion do?
* diary cutter: separates the given entries into specific files based on month and creates proper directory/file-stucture; needs proper unit-test-coverage, because loss of information is not acceptable
* RAG/finetuning of an LLM for ESP32-related dev-tasks: the espressif documentation is nice, but what about a custom tailored answering machine?
* refresh personal homepage; only html5/css, responsive design, no cookies - just like now; add image; add mini disclaimer (not adresse, not neede d bceause not commercial)
