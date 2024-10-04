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

## Notes

### Title: We do not have time to refactor! - David Sautter
* Coder, project manager, trainer
* Trainer on how to make code more maintainable for internal teams at R&S
* New hire, big pile of mud, weird names, complexity, nested functions, ...
* "We need to rewrite parts of the code" - but not possible in any economic setting
* As an experienced programmer, an important skill is negotiation: first answer from manager is no; but then "maybe one refactoring sprint, then continue with the features"
  * What to refactor in that one sprint? Big impact on job satisfaction for the next month
  * ROI-formula; but how to measure the gain from a refactoring
  * A beautiful codebase is fine for open source projects, but not business-related ones: so "avoid costs"
  * Study: "we spend most of our time understanding code": dev-surveillance; 70% of time is spent on trying to understand code
  * Martin Fowler: "Any fool can write code a computer can understand. Good programmers write code that humans can understand." - Getting mental model into code
  * How to judge if code is readable: don't judge yourself; give the code to someone else; if it takes them longer to understand, then comment "I was stuck here for a longer time"
    * But: what does this say about me as a programmer? (as a side-effect)
  * Complexity: does not really matter which one (LoC and others)
  * Second level: do we have to read this file again in the future?
  * An indicator is needed: what we touched recently will also change in the future, over a broad scale
    * Maybe: number of commits per file - for the last six months -> this is called "the churn"
    * Lower left quadrant: top left, bottom left, bottom right: all fine; but the killer are the files in the top right
    * Focus on the middle and top right quadrant
    * https://codersint.net: sautte_d churn complexity.git - Why not implement this myself? #NIH
  * Hidden pain:
  * Tool YakLog - physical wall: post-it notes with complaints; each time something is touched; draw a hangman (one stroke)
    * Also print "a pile of burning money" ... manager will notice it and then ask about it and also advise to get rid of that showstopper ... thank you
    * Good tool to recognize problems over time and deal with them
  * Clean slate; after a couple of months, it is a mess ... why? Knowledge - understanding of the code and features
* Why should I touch existing code? No direct benefit, risk of adding more defects, maybe not even fitting
* They expect me to be done: slowing down; why am I taking so long? People stop when it works and not when it is right
* "The dopamine rush: results, more results."
* You have to spread your knowledge in a team
* "Your Code as a Crime Scene" book recommendation

### Title: Safety vs Performance. A case study of C, C++ and Rust sort implementations - Lukas Bergdoll
* All languages are aspiring system-level languages
* Agenda today: motivating example, property analysis, property results, performance, conclusion
* `std::unordered_map<std::string, int64_t> XX = {...}`
  * Address sanitizer fine, memory sanitizer, is overwritten
  * Then: how to turn it off
  * Ordering safety in C++ is bad: sort vector of float, not possible because of NaN
  * In Rust, not possible to prove that something has a total order
  * Exception safety: in Rust panic (also unwinds the stack)
  * Exception safety: basic exception safety (promises that when an exception happens, during unwinding of the stack) - strong exception safety (if something happens, you go to the state before; nothing in between)
  * Check: `std::aligned_storage`
  * Type confusion: CVE for V8 engine was of this type; really dangerous
* What is crumsort? pdqsort
* Comparison of the implementations: all unstable, different properties, in the end only two from Rust fulfill all properties .. see photo
* Performance benchmarks with prepared input patterns, some pre-sorted: 100x difference between implementations, also spread
* Danila Kutenin
* GitHub: voultapher - Lukas? see avatar
* C++ std-implementation almost never beats Rust ones
* Correlations: performance does not correlate with usage-safety
* Conclusion: safety and performance are not a zero-sum tradeoff
  * Safety is a question of culture
  * Unlock performance with research and creativity

----

* Both speakers were pacing the stage with tremendous speed; like some explosive power waiting to be released
