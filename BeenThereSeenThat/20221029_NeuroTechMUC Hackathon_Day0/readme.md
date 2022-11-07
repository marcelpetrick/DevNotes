# 20221029 - NeuroTechMUC Hackathon

## Agenda (from )
```
Center for Digital Technology and Management
20 Marsstraße
München, BY 80335

What to expect

    Work on super cool neurotech projects. Hardware, software, whatever!
    Get to know other people that are interested in neurotech and Brain-Computer-Interfaces
    You can work with hardware from OpenBCI and hackerBCI

Schedule: Saturday, 29.October
10 am
Welcome and Introductions
Welcome words from the organizers Sebastian & Lisa

11 am
Project suggestions
You can either present your own neurotech idea or you can join someone else 

1 pm
Team building
By now there should be a couple of 3-5 person teams 

2 pm
Start hacking & building
Start working on your ideas/projects 

8 pm
End of the first day
We won't close the building, you can also work through the night if you want to

Schedule: Sunday 30.October
12 pm
Lunch together
We will start the second day with a lunch with everybody

1 pm
Continue hacking & building
Use the rest of the day to work on your project and prepare a presentation

6 pm
Project presentation
Show what you & your team has build during the weekend

8 pm
End of the hackathon
End the hackathon by connecting with all of the other neurotech enthusiasts
```

---------------

* todo: check the discord: there are some ressources and stuff
* equipment:
  * three openbci bords
  * one musebit?
* evaluation by the guys from blackrock tomorrow
* neurotechx munich: connect people who want to become experts in that space
* companies: openbci starter kit, raspberry pis
* over 600 people world wide, different locations
* pairing with people in the room or worldwide
* 3-4 slides, one minute pitch; 3 pm for the pitch

* todo: book: the neurotech primer - buy this
xr biosense 2022; was online in 2022
* three tracks: tech/handson / the data challnge / design/strategy
* links for the datassets will be published as well: to handle that task maybe later
* in the ende everything goes for design/strategy
* 1 hackathon, 600 signups, 6 in person locations, 6 judges, 16 happy sponsors, awesome prize pool ..

hackathon process walkthrough:
* first welcome-rules; resourrces in the files ..
* my intro for the discord-channel
```
Greetings, I am Marcel. I am a software engineer with some experience in C++/Qt/Python and Desktop and embedded environments. My experience with the whole BCI topic is zero (sadly), I just stumbled over that quite interesting field two week ago. But I am willing to learn and participate and bring in my skills. github: https://github.com/marcelpetrick - located in Munich. Would prefer a local team 🙂
```

## g.tec medical engineering:
* bio-engineering, medical eletronics, bio-electricity
* developing hard- and software products for biosignal research
* mainly: austria: schiedlberg, austria
* EEG or ECOG (for invasive) interfaces
* BCI is analysizing the signals
* you always need a task for stimulation for the subject
* device could be the easiest one your computer
* FMRI or MEG are skipped for this, because not optimal and slow
* Electrocorticogram: ECoG: surgery is needed
* Electroencephalogram (EEG) - easy ot apply and the signal is pretty good
  * moderate spacial resolution, hih temporal resolution, low signal tonoise ratio, 0-40Hz, 1-64(128) channels, 1 mV - 100 mV
* important is to get a clean EEG signal; if the subject is clenching with teeth, then the signal degrades much
* unicorn-bi.com - a brain interface - https://www.unicorn-bi.com/product/unicorn-hybrid-black/ - 999€ ..
* todo: bee bot kaufen ... 92 euro
* g.Tec Suite 2020: for access to the channels, programming interfaces, just output of data - all in one
* how to do measurems, how to mount a cap? active electrodes, which amplify the signal put cap on, then chin strap, the massage it to the head, reference electrode on the earlobe (with gel), one electrode on the forehead as groudn eelctrode (yellow), the inject gel in all of the signal electrodes, then with gel really clean signals, takes roundabout 6 minutes (for someone experienced)
* eyeblinks, moving the teeth, rolling eyes, bithing teeth really screws up the signal (movement artifacts)
* dry-electrode-cap with screwing electrods and 16 inputs it took like 30 seconds to get the cap fixed

slow cortical potentials: anticipation tasks: not used anymore because of easy defets
* event-related, non-phase-locked changes
* the phenomenon of synchronisation of the signals happens even before the finger moves;before and after the movement the amplitude is getting really big
  * the signal looks really similar when you just imagine the movement
  * this is used to rehabilitate stroke patients
  * recovering stroke patient had after a while of training (last sessions) alsmost 100% accuracy, just by imagining he movement instead of doing it, usually patients start with 60%

* todo: read this later : https://www.researchgate.net/publication/357698587_PIEEG_Turn_a_Raspberry_Pi_into_a_Brain-Computer-Interface_to_measure_biosignals_arXiv220102228
* PIEEG - where to buy and price?

* quick overview of the brain can be done with EEG quite fast: like cortex-mapping
* also where the face-decoding is located: characters versus faces, quite well doable

* new idea: pangolin grid: really small electrode with 16 positions, one clip to connect the grid to

### P330 - approach (EEG):
* after 300ms a peak on average, 
* the 6x6 matrix speller

* before using any BCI-application some calibration is needed first
* out of the collected data offline some classifier is generated: then the game (world of warccaft, e.g.) can be controlled
* SSVEP: needs update of the classifier every day+

* todo: check this brain41.io - hackathon; BCI designers hackathon (url does not work?)

### practise
* formed a Team with Tom and Shuhong 


* problems to gather data with ganglion or the cyton board ... unclear why

* https://docs.google.com/spreadsheets/d/1yuI23OhaGvtNob2QMKmxH_Hp8yNZVCKmW3oSV6VyfGQ/edit#gid=0