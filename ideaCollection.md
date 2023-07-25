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

## The mother of all gits
Jk, idea is to create a script which retrieves the list of all _my_ (publicly) available git(hub) repositories and then clones them to a specific path. Just to have a local backup.  
I don't want to to this manually for all repos manually.  
Maybe just do baremetal-cloning.  
**Implemented:** https://github.com/marcelpetrick/codingWithGPT/tree/master/MotherOfAllGits

## python-api-access of Azure DevOps
* authentificate
* get all tickets with certain tag (just like usual query)
* check the history of each ticket when it got the "Update3"-tag assigned
* create a graph or structured outout in the form of "date0: ticket1, ticket2, ..; date1: ticket3, ticket; .."
