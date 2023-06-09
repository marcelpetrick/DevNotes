# collection of resources for C4

* short how-to for drawing: [https://www.gliffy.com/blog/c4-model](https://www.gliffy.com/blog/c4-model)
* in regard with PlantUML: [https://engineering.linecorp.com/en/blog/diagramming-software-architecture-using-c4-model-and-c4-plantuml/](https://engineering.linecorp.com/en/blog/diagramming-software-architecture-using-c4-model-and-c4-plantuml/)
* TBC


-----------
```
Level 1: Context Diagrams

Context diagrams are the most general description of what your system does, who will use it, and what other systems it will interact with. A context diagram will help you describe the scope of your project and help you pinpoint who the user is and what problem you’re going to solve.
Level 2: Container Diagrams

The container diagram takes the first step into describing the software system and shows the APIs, applications, databases, and microservices that the system will use. Each of these applications or services is represented with a container and the interactions between them are shown at a high level.
Level 3: Component Diagrams

One step deeper than the container diagram, the component diagram details groups of code within a single container. These components represent abstractions of your codebase.

This diagram type is comparable to a UML component diagram, but follows a less-strict set of “rules” in order to create the software architecture diagram.
Level 4: Representing Code with Class Diagrams

The last level requires lots of detail to show how the code of a single component is actually implemented. To do this, you would want to make a UML class diagram or entity relationship diagram that describes the component.
```
