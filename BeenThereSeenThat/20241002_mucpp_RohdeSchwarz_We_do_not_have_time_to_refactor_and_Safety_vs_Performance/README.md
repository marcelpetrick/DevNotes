# 20241002 mucpp: "We do not have time to refactor!" and "Safety vs Performance" - Rohde & Schwarz

```
Details

Sponsor: Rohde & Schwarz (www.rohde-schwarz.com).

Thanks to Rohde & Schwarz for hosting this event. In order to participate on-site, you'll have to register via the following form: https://rohdeschwarz.avature.net/MUCplusplus. If you want to participate
online, you don't have to register, but only have to use the link we'll provide on the day of the event.

***

On October 2nd we have the pleasure to see two talks: David Sautter will talk about refactoring and Lukas Bergdoll will talk about the compromises between safety and performance.

***

Title: We do not have time to refactor!

Presenter: David Sautter, Web UI Developer and clean code advocate at Rohde & Schwarz. David is a senior software developer and project lead at Rohde & Schwarz, with a focus on web technologies. He has a strong interest in code maintainability and regularly leads internal trainings on the topic. As a seasoned developer and project lead, he brings a wealth of experience to the subject of refactoring. In this talk, he will share his insights and expertise on how to improve code quality and maintainability.

Abstract: In the fast-paced world of software development, there always seems to be something more urgent than refactoring. However, without regular refactoring, software can quickly turn into an expensive nightmare. This talk will explore effective negotiation strategies for securing the right amount of time for refactoring. Drawing also from his experience teaching Rohde & Schwarz software teams about the value of maintainable software through Clean Code Cafés, David will provide practical tips and tricks and delve into how to strike the right balance between refactoring, feature development, and bug fixes.

***

Title: Safety vs Performance. A case study of C, C++ and Rust sort implementations

Presenter: Lukas Bergdoll, Lukas Bergdoll is a self-taught C++ developer, long-time MUC++ co-organizer and FOSS developer with commercial experience in building distributed systems, security critical software, compilers, interpreters, in-memory databases and language interfaces. At heart a curious mind, he aspires to see the world for what it could be.

Abstract: With 70 years of theoretical and practical exploration, sort algorithms are among the oldest and most famous problems in computer science. Where does safety even come into the picture when sorting a collection of elements? What is the performance impact of safety in the context of sorting? How do popular implementations in C, C++ and Rust compare? Be there and find out.

***

Schedule:
18:30 (CEST) -- Open doors
~19:00 (CEST) -- Welcome with snacks and drinks
~19:50 (CEST) -- Welcome by the MUC++ Organizers
~20:00 (CEST) -- Talk by David Sautter
~20:30 (CEST) -- Talk by Lukas Bergdoll
~22:00 (CEST) -- Official End

***

Lifestream: https://streaming-service.rohde-schwarz.com/Watch/3f5bAq
```

## notes

## Title: We do not have time to refactor! - David Sautter
* coder, project manager, trainer
* trainer how to make code more maintainable for internal teams at R&S
* new hire, bi pile of mud, weird names, complexity, nested functions, ...
*  "we need to rewrite parts of the code" - but not possible in any economic setting
* as experienced progammer an importnt skill is negotation: first answer from manager is no; but then "maybe one refactoring sprint, then continue with the features"
  * what to refactor in that one sprint? big impact on job satisfaction for the next month
  * ROI-formula; but how to measure the gain from a refactoring
  * a beautiful codebase is fine for open source projects, but not business related ones: so "avoid costs"
  * study: "we spend most of our time understanding code": dev-surveillance; 70% of time is spent on trying to understand code
  * martin fowler: "any fool can write code a computer can understand. good programmers write code that humans can understand." - getting mental model into code
  * how to judge if code is readable: not judge yourself; take the code and give it to someone else; when you noticed it takes a longer timer to understand, then comment "i was stuck here for a onger time"
    * but: what does this say about me as programmer? as side-effect
  * complexity: does not really matter which one (LoC and others)
  * second level: do we have to read this file agan in the future
  * so an indicator is needed: what we touched recently, will also change in the future; over a broad scale
    * maybe: number of commits per file - for the last six months -> and this is called "the churn"
    * lower left quadrant: top left, bottom left, bottom right: all fine; but the killer are the files top right
    * focus onto middle and top right quadrant
    * https://codersint.net: sautte_d churcn complexity.git - why not implement this myself? #nih
  * hidden pain:
  * tool YakLog - physical wall: post it with complaint; each time something is touched; draw a hangman (one stroke)
    * also print "a pile of burning money" ... manager will notice it and then ask about it and also advice to get rid of that showstopper ... thank you
    * good tool to recognize problems over time and deal with them
  * clean slate; couple of months it is a mess ... why? knowledge - understanding of the code and features
* why should i touch existing code? no direct benefit, risk to add more defects, maybe not even fitting
* they expet me to be done: slowing down;  why i am taking so long? people stop, when it works and not when it is right
* "the dopamine rush: results, more results."
* you have to spread your knowledge in a team
* "your code is a crime scene" book recommendation

## Title: Safety vs Performance. A case study of C, C++ and Rust sort implementations - Lukas Bergdoll
tbc

