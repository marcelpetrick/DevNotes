# 20260916 Zartis workshop Anthropic Claude Code

* in Mindspace Stachus, Munich

---

```
Hi Marcel,
We're looking forward to meeting you next week on September 16th at our Claude Code Workshop in Munich!

If you haven't done so yet, please complete the following prior to the workshop:

1. Fill out the API Credits Form:

This will ensure you have sufficient credits for the workshop. Everyone completing this form will receive $25 of Claude Credits.

P.S. All participants need to claim their API Credits by EOD on September 11th to ensure they are activated before the event day.
API Credits Form

2. Review the pre-install checklist and ensure that it is complete:

Please follow these steps to set up Claude Code.
Pre-Install Checklist

3. Make sure you can access the exercise beforehand:

    Check the hands-on exercise code on GitHub
    Clone or download the repo as a ZIP, so the code is on your laptop
    Open your local workshop.html in the browser to check the hands-on exercise guide
    Complete the Prerequisites & Setup sections

Access GitHub Repo
```

[https://github.com/marcelpetrick/x-clone-starter/tree/main](https://github.com/marcelpetrick/x-clone-starter/tree/main)

---

* Zartis with a headcount of 350 people
* tenth venue this September; second workshop in Germany; second in Berlin
* your AI compass: alignment, enablement, AI development

  * AI culture and mindset
  * TODO add image/photo

---

* skills, hooks, ... as advanced usage

* understand agentic coding, get hands-on with Claude Code, learn and share best practices

* agentic evolution: from single-line completion with Copilot in 2021 to complete tasks with agents using Claude Code in 2025; in 2026, agents tackle projects: collect user feedback, etc.

* Mateusz now: multi-environment coding agent that lets you delegate complex tasks, optimized to work with Anthropic's frontier models; handle a range of tasks from coding to non-coding tasks; accelerating development work 
* how is it governed: six permission modes and rules down to tool arguments, 33 lifecycle hook events the model cannot skip; sandboxing, an auto-mode classifier that reviews risky actions; settings the admin can pin centrally

* what evidence says: Rakuten: from 254 working days to 5; Wiz: migrate a 50k LoC Python library to Go in one day of active work, against 2–3 months of estimated manual work

* where it runs: terminal, VS Code, JetBrains, desktop app, web, mobile, etc. — one config travels with the repo to every surface

* where inference lives: Anthropic API, Amazon Bedrock, Microsoft Foundry, cloud platform on AWS, corporate proxy and LLM gateway 

* trust and governance:

  * permission policy: six modes from read-only planning to "auto"; deny rules with every mode, including bypass
  * lifecycle hooks: 33 events across sessions, turns, and tool calls; handlers in shell, HTTP, MCP; deterministic: the model cannot skip them; admins can allow managed hooks only? <-- check: admins can restrict environments to managed hooks only?
  * isolation and the classifier: sandboxed Bash, filesystem and network; containers and VMs, self-hosted cloud environments; in auto mode, a second model reviews actions and blocks exfiltration, production deploys, IAM grants, and force pushes by default
  * managed settings: delivered by MDM or from the server; pin the permission mode, disable bypass, force plugins and MCP servers, restrict models; a repo cannot grant itself more autonomy than the organization allows
  * TODO add the photo

* what can be done with Claude Code? discover, design, build, deploy, support & scale

  * explore codebase, search documentation, onboard and set up
  * plan project, develop technical specs, define architecture
  * implement code, write and execute tests, create commits and PRs
  * deploy: automate CI/CD, configure environments, manage deployments
  * support and scale: debug errors; large-scale refactoring; monitor usage and performance

* how Anthropic uses Claude Code?

  * not just for coding; add the screenshot
  * also for the legal team
  * pilot, standardize, scale: weeks 1–6; 6–12; quarter two

    * delivery champions, adoption starts spreading
  * what is possible: Stripe 1,300 per week, zero handwritten
  * Satispay: 75% engineer adoption within 30 days of rollout
  * Ramp: incident investigation cut by 80%; teams are now able to query the data warehouse without SQL — natural language <-- check: incident investigation time cut by 80%

* economics: cost drivers and cost controls

  * subscription seats: per user, centralized billing, admin controls; predictable budget
  * consumption: token-based through the Anthropic Console
  * what drives the cost? tokens scale with context size times number of turns
  * model choice: Sonnet 5 is the default; Opus for hard problems <-- check: Sonnet [version] is the default; Opus for hard problems
  * effort level (default high) and extended thinking
  * parallelism: subagents, agent teams, and dynamic workflows multiply usage
  * auto-mode classifier calls count on Enterprise, API, and cloud accounts

* outcomes: baseline first

  * lead times for changes and PR cycle time
  * review turnaround per PR
  * change failure rate and MTTR
  * time to first merged PR for new joiners
  * delivery of committed roadmap items

* leading indicators: weekly active engineers; from individual tool setups to team standards as code; `CLAUDE.md`, rules, skills, and hooks, versioned and reviewed like any other code?

  * manual quality gates: deterministic gates; hooks run tests and linters before completion, plus automated first-pass review
  * move the knowledge from the heads of the engineers to skills

    * risks to manage: over-trust — review stays a human responsibility; prompt injection through web pages and MCP data
    * secrets entering context; runaway cost from parallelism

* true SOTA agentic models meet infinite composability: not just for writing code 

* effort level and `ultrathink`? (TODO check) raises the effort for one single turn; `@`-file mode to mention; be as constrained as you want 

* using hooks: to control the agents; to coordinate deliveries; prevent the agent from going beyond what it should do

  * Claude Agent SDK: Ultracode — TODO check 

---

## Ultrathink — 5 sentences

1. **Ultrathink** is a one-prompt instruction in Claude Code: putting `ultrathink` anywhere in the prompt asks Claude to reason more deeply for that turn, without changing the session's configured effort level ([Claude][1])
2. Technically, Claude Code adds an in-context instruction; importantly, it **does not change the API effort value**, so think of it as "spend extra attention on this particular problem," not a new model or permanent mode ([Claude][1])
3. For developers, it is most useful for difficult debugging, architecture decisions, subtle concurrency/data issues, migration planning, or reviewing a risky implementation — not routine CRUD, renames, or boilerplate
4. The impact is mainly **better reasoning at the expense of additional thinking tokens and latency**, but Anthropic does not publish a universal "X% better/X× more expensive" number because the effect depends heavily on the task and model ([Claude][1])
5. For a Head of Application Software, a sensible policy is therefore **normal effort for everyday engineering and `ultrathink` selectively for high-consequence decisions**, rather than making maximum reasoning the default

## Ultracode — 5 sentences

1. **Ultracode is substantially different:** it is a Claude Code orchestration mode that runs the model at `xhigh` effort **and** asks Claude to construct dynamic multi-agent workflows for substantive tasks ([Claude][1])
2. You can enable it with `/effort ultracode` or `claude --effort ultracode`, after which Claude may split a problem into parallel research, implementation, verification, and review work instead of having one agent work sequentially ([Claude][1]) 
3. For developers, that can materially improve large refactors, unfamiliar repositories, cross-service changes, migrations, broad test/review work, and problems where several independent investigations are valuable
4. Its resource impact can be **much larger than Ultrathink** because you are paying not only for deeper `xhigh` reasoning but potentially for many subagents; Anthropic therefore characterizes `xhigh` as higher-token-spend reasoning and Ultracode as workflow orchestration on top of it, rather than publishing a fixed cost multiplier ([Claude][1]) <-- check: verify Anthropic's characterization
5. For a Head of Application Software, treat Ultracode as an **engineering acceleration mode for complex/high-value work**, with usage and token consumption monitored, rather than enabling it globally for every developer task

**Shortest distinction:** `ultrathink` = **one problem → one Claude thinks harder**; `ultracode` = **complex problem → Claude thinks hard and can organize multiple agents to solve/verify it** ([Claude][1]) 

[1]: https://code.claude.com/docs/en/model-config "Model configuration - Claude Code Docs"

---

* `/init` for a `CLAUDE.md`; as README for the coding harness; what are the coding standards, codebase documentation

  * no benchmarks at hand, so maybe do one myself — can also be used to refine an existing `CLAUDE.md`

* hierarchies of `CLAUDE.md` files — TODO add screenshot

  * structure it with subdirectories
  * system overview, root dir; `~/.claude/CLAUDE.md`; hierarchical and updateable instruction management; quite refined strategy 
  * whole agent has full context; subagent has only the context it needs
  * agents as subdirectory, with specialized roles: `code-reviewer.md`, `researcher.md`, and `writer.md`
  * possible to control the token usage of the subagents: tell them to use lower models; where to put this and what? Suggest via prompt; also tell them via the prompt how many turns to run, but not deterministic — TODO do research, no definitive answer; also make sure the subagents shut up (brief results)

* skills: create, manage, and share skills to extend Claude's capabilities in Claude Code; custom slash commands

  * skills give an agent general capabilities Claude isn't good at out of the box yet
  * Claude uses skills when relevant, or you can invoke them directly with `/commandName`
  * write your own `SKILL.md`

## Getting the most out of Claude Code

* common workflows: explore, plan, confirm, code, commits

* or with TDD: write tests, commit, code, iterate, commit

* write code, screenshot the result, iterate

* parallel Claude: run multiple Claude Code instances simultaneously, each in its own terminal; each instance works on a separate task independently with its own context

* Git worktrees

* parallel Claude versus subagents: parallel Claude is a completely independent Claude Code instance

* plugins: share MCP servers, skills, subagents, and hooks in a single plugin format

* installed via terminal commands → TODO Enterprise marketplaces; organizations can create internal and external marketplaces to share plugins across teams and customers

* Anthropic Academy ... TODO

* TODO hooks for event handlers: how to manage several subagents, hand over work?

* question: how to measure the impact of changes in `CLAUDE.md`, etc.?

* they will send the slides afterwards ...

---

BREAKFAST BREAK AT 10:30

* Mateusz Strycharski takes over: the live coding session
* running the stuff should give us a login prompt in the browser

---

* scoped rules with the `path:` prefix — only triggered when finding a matching file 

* don't use passwords or credentials with agentic harnesses, even if masked — this results in spillage

* TODO what are all those modes? bypass, plan mode, auto mode, etc.?

* so we are listening to a moderator (quite enthusiastic) and watching Claude Code work. Is this a workshop?

* working through: `file:///home/mpetrick/repos/x-clone-starter/workshop.html` — plan mode (`/section4`), last step <-- check: plan mode, section 4, last step

* grilling features: if there are no answers, then a lot of assumptions are made

  * but many tiny decisions are just automatically answered — but the developer wanted to be questioned

* `/grilling` as skill — TODO maybe research a bit and make it an article

* plan with implementation details and verification steps; use auto mode to run it after approval

---

```
License: none, so not automatically free to share
- There's no LICENSE file and no license field in package.json. Without a license, the code and workshop.html legally stay with their authors (Zartis, zartis-digital/x-clone-starter). Having access doesn't give you the right to reuse or redistribute them
- Your origin points at your own copy, github.com/marcelpetrick/x-clone-starter. If that copy is public, you're already redistributing Zartis's material. You may want to make it private until you've asked
- To be sure: ask the Zartis organizers whether the material may be reused internally, and check the event invitation or terms. I can't give you a legal answer

Backend: yes, everyone uses the same API, and that causes complications
- src/frontend/.env points everyone at one shared API, https://workshops.zartis.com/x-clone-api. The backend isn't in the repo, so your teammates couldn't run their own
- What that means in practice, as we saw today:
  - Everyone on cluster-test shares likes, retweets, and posts. The guide asks for separate accounts for this reason
  - Posts can't be deleted, and the API doesn't check image keys. My broken test post stays up for everyone
  - Uploaded images go into Zartis's shared storage
- Availability is unknown. It's Zartis's server, deployed for this workshop, and nothing says how long it stays online. Teammates using it after the event may find it gone and would be using a company's infrastructure without permission
```

* speed over compliance? OpenAI and Anthropic, attack on Hugging Face <-- check: OpenAI and Anthropic; attack on Hugging Face?

* product development lifecycle: hooks to orchestrate agents; design things first, as a concept; hook people together to work as "agents" on a task; personify my hook

  * hook organizes the work of the lifecycle?
  * hook triggered — MR reviews? Where do they run? Overwatch? <-- check: hook-triggered MR reviews; where do they run?
  * agents with limited privileges: hook and guardrail as second part, to prevent agents from going off-board

* the process is there: peer code review; Codex reviews what Claude writes

* align teams; much PR fatigue, with automated reviewing and merging, lots of code changes; in the end, a human needs to be accountable — if 2k LoC, then who can do this per hour?

  * gutefrage.net as a Q&A company
  * push devs to be smaller entrepreneurs; if you don't trust engineers, then don't trust agents
  * trunk-based development: always develop on main, dedicated QA pipelines, always push to prod, no PRs; post-deployment reviews
  * the business requirements in the beginning have to be clear; from there, the developer is fully responsible until it is done
  * so the engineers must have full context: state the business goals
  * gutefrage.net: good experience with bigger codebases; dedicated planning before doing; good results, but also limited risk — he says
