# 20260916 zartis workshop anthropic claude (code)

* in mindspace stachus munich

----

```
Hi Marcel,
We're looking forward to meeting you next week on September 16th at our Claude Code Workshop in Munich!

 

If you haven't done so yet, please complete the following prior to the workshop:

 

1. Fill the API Credits Form:

This will ensure you have sufficient credits for the workshop. Everyone completing this form will receive $25 of Claude Credits.

 

P.S. All participants need to claim their API Credits by EOD on September 11th to ensure they are activated before the event day.
API Credits Form

2. Review the pre-install checklist and ensure that it is complete:

Please follow these steps to set-up Claude Code.
Pre-Install Checklist

3. Make sure you can access the exercise beforehand:

    Check the hands-on exercise code on GitHub
    Clone or download the repo as a zip, so the code is on your laptop
    Open your local workshop.html in the browser to check the hands-on exercise guide
    Complete the Prerequisites & Setup sections

Access GitHub Repo 
```

https://github.com/marcelpetrick/x-clone-starter/tree/main

---- 

* zartis with 350 people headcount
* tenth venue this october; second workshop in germany; second in Berlin
* your AI compass: alignment, enablement, ai development
  * ai culture and mindset;
  TODO add image photo
  
---- 

* skills, hooks, .. as advanced usage
* understand agentic coding, get hands on with claude code, learn and share best practises
* agentic evoluation; from single line with copilot in 2021 to complete tasks with agents with claude code in 2025; 2026, agents tackle projects: collect user feedback, etc.
* matesuz now: multi environment coding agn, that lets you delegate comlex asks optimized to work with anthropics frontier models; andle range of tasks from coding to non-coding tasks; accelerating dev work
* how is it governed: six permission modes and rules down to tool arguments, 33 lifecycle hook events teh model cannot skip; sandboxing, an auo mode classifier, tjat reviews risky actions. settings the admin can pin centrally.
* what eveidence says: rakuten: from 254 working days to 5. Wiz: migrate a 50k LoC python library to go in one day of active work; agsinst 2-3 months of estimated anual work
* ehere it runs: terminal, vs code, jetbrains, desktop app, web, mobile, etc. - on config tavels with the repo to evert surface
* wehere inference lives: anthropicapi, amazon bedrock, microsoft foundry, claude platforn onAWS, corporate proxy and llm gateway
* trust and governance:
  * ermission policy; six modes from read only planning to "uto". deny rules with every mode, including byass
  * lifecycle hooks: 33 event across sesions; tuna nd tool call; handlers in hslel. httü, mcp, dterministig: model cannot ski them. admins can allow managed hooks only?
  * isolation and the classifier: sandboxed bash: filesstem and network; containers and vms, self hosten cloudenvironments; in auto mode a second model reviews actions and blocks exfiltration, production depyls, IAM grants and force psh by default
  * managed settings: delviered by MDM or from the server; pin the permission mode, disable bypass, force plugins and MCP servers, restrict models, a repo cannot grant itself more autonomy than the organization allows
  * TODO add the photo
* what can be done with claude code? discover, design, build, deply, support & scale
  * explore code base, search docu, onboard and setzp
  * plan project, develop tech specs, define architecture
  * implement code, write and execute tests, create omits and PRs,
  * deplyoy: automate ci/cd, configure environments, manage deployments
  * support and scale: debug errors; large-clerefactor; monitor usage and performance
  
* how anthropuic uses claude code?
  * not just for coding; add the screenshot
  * also for the legal team
  * pilot, standardise, scale: week 1 to 6; 6-12; quarter two
    * delivery champions, sptarts spreading
  * what is possible: stripe 1.300 per week zero hand written
  * satispay: 75% of engineer adoption within 30 days of rollout
  * ramp: 80% incident investigation cut by 80%; teams are now ble to query the data warehouse without SQL - natural language

* economics: coster drivers and cost controls
 * subscription sets; per user, centalised billing, admin controls; preduictable budget
 + consumption: token based through the anthopic console
 * what drives the cost? token scalewkit context size times number of tunrs
 * model choice: sonnet 5 is the default; opus for hard probelsm
 * effort level (default hight) and extended thinking
 * parallelism; subagents, agent teams and dynamic workflow multiply usage
 * auto-mode classifier calls count on entreprsie, api and cloud accounts
 
*  outcomes: baseline first
  * lead times for changes and PR cycle time
  * review turnaround per PR
  * change failure rate and MTTR
  * time to first merged PR for new joiners
  * deliver o fommitted roadmap items
  
* leading indicators: weekly active enginers; from indivudal tool setups to team starndards as code; claude.md, rules, skills and hookes, versined and reviewed like any other code?
  * manual quality gated: dterministic gates; hooks rn test aand linters before completion; plus atuomated first-pass review
  * nmove the knowledge from the heads of the eningeers, to skills
    * risks to manage: over-trust: review stays a human responsibility; prompt injction through web pages and mcp pdata
    * secretes entering context; runaway cost from parallelism
    
* true SOTA agentic models meetthe infite compability: no just for writing code
* effort level and ultrathink? (TODO check) raises the effort for one single urn@-file mode (to mention); be a s contrained as you want
* using hooks: to control the agents; to coordinate the deliveries; prevent that the agent goes nbeyong what it should do
  * claude agent sdk: ultacode - TODO check
  
-------------
### Ultrathink — 5 sentences

1. **Ultrathink** is a one-prompt instruction in Claude Code: putting `ultrathink` anywhere in the prompt asks Claude to reason more deeply for that turn, without changing the session’s configured effort level. ([Claude][1])
2. Technically, Claude Code adds an in-context instruction; importantly, it **does not change the API effort value**, so think of it as “spend extra attention on this particular problem,” not a new model or permanent mode. ([Claude][1])
3. For developers, it is most useful for difficult debugging, architecture decisions, subtle concurrency/data issues, migration planning, or reviewing a risky implementation—not routine CRUD, renames, or boilerplate.
4. The impact is mainly **better reasoning at the expense of additional thinking tokens and latency**, but Anthropic does not publish a universal “X% better/X× more expensive” number because the effect depends heavily on task and model. ([Claude][1])
5. For a Head of Application Software, a sensible policy is therefore **normal effort for everyday engineering and `ultrathink` selectively for high-consequence decisions**, rather than making maximum reasoning the default.

### Ultracode — 5 sentences

1. **Ultracode is substantially different:** it is a Claude Code orchestration mode that runs the model at `xhigh` effort **and** asks Claude to construct dynamic multi-agent workflows for substantive tasks. ([Claude][1])
2. You can enable it with `/effort ultracode` or `claude --effort ultracode`, after which Claude may split a problem into parallel research, implementation, verification, and review work instead of having one agent work sequentially. ([Claude][1])
3. For developers, that can materially improve large refactors, unfamiliar repositories, cross-service changes, migrations, broad test/review work, and problems where several independent investigations are valuable.
4. Its resource impact can be **much larger than Ultrathink** because you are paying not only for deeper `xhigh` reasoning but potentially for many subagents; Anthropic therefore characterizes `xhigh` as higher-token-spend reasoning and Ultracode as workflow orchestration on top of it, rather than publishing a fixed cost multiplier. ([Claude][1])
5. For a Head of Application Software, treat Ultracode as an **engineering acceleration mode for complex/high-value work**, with usage and token consumption monitored, rather than enabling it globally for every developer task.

**Shortest distinction:** `ultrathink` = **one problem → one Claude thinks harder**; `ultracode` = **complex problem → Claude thinks hard and can organize multiple agents to solve/verify it**. ([Claude][1])

[1]: https://code.claude.com/docs/en/model-config "Model configuration - Claude Code Docs"

-------------
* /init for a claude-md; as readme for the coding harness; what are the cdne stanard, codebase documentation
  * no benchmarks at hand, so maybe do one myself - can also be used to refine an exsting claude.md
* hierachies of claude.md'S - TODO add screenshot
  * structure it with subdirectores
  * system overview, root dir; user/.claude/claude.md; hierarchivcal and updateable nstruction managemnts; quite refined strategy
  * whole agent has full contetxt subagent has only the context it needs
  * agents as subdirectory: with sepcialied roles: code-reviewer.md, and researcher.md and writer.md
  * possible to control the token usage of the subagents: tell them to use lower models; (where to put this) and what, usggest via prompt; also tell this via the primopt how many turns to run; nbut not deterministic: TODO do research, no definitive answer: aso make sure teh subagents shut zup (brief results)
  
* skills: create, manage and share skills to extend claudes capbility in claude code; custom slash commnds
  * skills give an agent: general capabilities claude ist good at out of the box (yet)
  * claude sues skills when relevant, oryou can invoke them dirctly with /commandName
  * write your own skill.md

## getting the most out of claude code
+ common workflows: explore, plan forncirm, code, commits
* or with tdd: write tests, commit, code, iterate, commit
* write code, screehsit result; iterate
* parallel claude: run miltiple claude code instance smulatenaursly each in its onw termin: each instance works on a seprate task indenepntendy with its own context
* git worktrees
* parallel claude versus subagents: parallel claude is competey independente claude code instance
* plugins: share mcp servers, sills, subagents; and hooks in a single plugin format
* nstalled via terminal commands -> TODO Entreprise marketplaes; irganizations can create internal and external markeplace to share plugins across teams and customers, 
* anthrpic academy ... TODO


* TODO hooks for event hamdlers: how to mange several subagents, hand opver work?

* question: how to measure the impact of changes in claude.md, etc?
  
* they will send the slides afterwrds ..

---- 

 breaKFAST BREAK AT 1030
 
* matesuz strycharski takes over: the lvie coding session
* running the stuff shall give us a login prompt in browser: 

---- 
* scoped rules with the path:-prefix - only tirggered when finding matvhing file
* dont use passwords or credetials with agnetic harneses; even if masked - this results in spillage
* todo what are all those modes? bypass, plan ode, auto mde, etc?

* so we are listening to amoderator (qute enthusiastic) and watching claude code work. is this a workshop?
* working through: file:///home/mpetrick/repos/x-clone-starter/workshop.html - pklan mode /section4) last step
* grilling features: if no answers, then a lot of assumptions are made
 * but amounts ofr tiny decisions are just automatically answered - but the dev wanted to be questioned
* /grilling as skill - TODO maybe reasearch a bit and make it an article
* plan wqith implementation details: and verification steps; use auto mdoe to run it after approval

---- 

```
License: none, so not automatically free to share
- There's no LICENSE file and no license field in package.json. Without a license, the code and workshop.html legally stay with their authors (Zartis, zartis-digital/x-clone-starter). Having access doesn't give you the right to reuse or redistribute them.
- Your origin points at your own copy, github.com/marcelpetrick/x-clone-starter. If that copy is public, you're already redistributing Zartis's material. You may want to make it private until you've asked.
- To be sure: ask the Zartis organisers whether the material may be reused internally, and check the event invitation or terms. I can't give you a legal answer.

Backend: yes, everyone uses the same API, and that causes complications
- src/frontend/.env points everyone at one shared API, https://workshops.zartis.com/x-clone-api. The backend isn't in the repo, so your teammates couldn't run their own.
- What that means in practice, as we saw today:
  - Everyone on cluster-test shares likes, retweets and posts. The guide asks for separate accounts for this reason.
  - Posts can't be deleted, and the API doesn't check image keys. My broken test post stays up for everyone.
  - Uploaded images go into Zartis's shared storage.
- Availability is unknown. It's Zartis's server, deployed for this workshop, and nothing says how long it stays online. Teammates using it after the event may find it gone, and would be using a company's infrastructure without permission.

```

* speed over compliance? openai und antrhopic, attacke auf huggingface.

* product development lifefycle: hooks, to orehcstrate agents: design things first, as concept; hook people together to work as "agents" on  task; personify my hook; 
  * hook organizes the work of the lifecycle?
  * hook triggered - MR reviews? where do they run? overwatch?
  * agents with limited privileges: hook and guard-rail as second part; to prevent agents from going off-board; 
* the process is there: peer code review: codex reviews what claude writes
  
* align teams; much of PR fatiquge, with autoamted reviewing and merging, lots of code change; in the end a human needs to accountable - if 2k LoC then who can do this per hour
  * open knowledge document formats: gutefrage.net as QA company, what ispaxcheck and revenue; push devs to be smaller entrpenroues. if yo dont trust engineers, the dont trust agents
  * trunk based development: always devleop on maoin, dedidcated QA pipelines, always push to prod, no PRs; post deplyoment reviews
  * the business in the beginning has to be clear: from there the dev is fully responsible; until it is done; 
  * so the engineers must have full context: state the business goals;
  * gutefrage.net: good exoernece with biger coee bases; dedicated planning befrore doing; good results; but also limited risk - he says
  
  

-----

It is important to stay curious. raise questions, search for answers. not a definitive answer.
