# PM Context Agent

Give your AI the context it needs to help with your product work.

As a PM, one of my biggest frustrations was having to keep teaching my AI the same things: my working style, targets, team, and projects. I built this setup to spend less time repeating that context and more time doing useful work.

Keep that context in simple files, connect your agent to the tools your company already uses, or use both. Optional MCP connections (Model Context Protocol) let a compatible agent read context from tools such as Google Docs, Jira, or Confluence, depending on the connections and permissions available. These connections are not included in this repo.

Describe what you need. The agent reads the relevant context and picks a workflow to help you plan a roadmap, scope a problem, write a PRD, review experiment results, draft an update, or capture meeting notes. You review the work and make the decisions.

The core setup uses plain Markdown files. No code, build step, or required plugins. Start with one useful workflow and add more context as you need it.

## What using it looks like

You can start with a request like this:

> Users keep dropping out of onboarding. Help me figure out whether we should tackle it this quarter.

The agent checks your goals and available evidence, then helps you define the problem. If key information is missing, it asks rather than making it up. It drafts the first sections of an opportunity scope and pauses for your review.

As the work develops, you can ask:

- “Turn the agreed first phase into a PRD.”
- “Review these experiment results against our success metrics.”
- “Turn the findings into a short update for the team.”
- “What did we decide in the last review?”

The agent uses the relevant files or connected sources for each request. You do not need to name a workflow or repeat the background. When you ask it to recall a decision, it cites the recorded notes. It drafts shared-document changes for your approval before writing them.

*This example is fictional. Your context and available tools determine what the agent can access.*

## Quick start

You need an AI agent that can read files in a folder. Connections to company tools are optional.

### 1. Create a private working copy

Download this repository as a ZIP and extract it into a private folder, or clone it:

```sh
git clone https://github.com/nakularora19/pm-context-agent.git
```

Keep your working copy private before adding company information. Do not push real work context to a public repository.

### 2. Open it in your AI tool

Open the folder in your agent's workspace. Start a conversation and paste this prompt:

```text
Read AGENTS.md and help me set up this private working copy.

Start with my role, how I like to work, and one current goal. Ask only what you need for my first task. Leave anything unknown unfilled and do not invent details.

Draft the updates to pm-profile.md and context/current-quarter.md for me to review before saving them. If you cannot read these files, tell me.
```

### 3. Try one real task

Pick something you are already working on. For example:

> Help me scope [problem]. Here is what we know so far: [evidence].

You do not need to complete every template first. The agent can work with the context you provide and flag what is missing.

### 4. Add context as you need it

Fill in live project status and team context when they become useful. Add links to project documents, or use your agent's available MCP connections to read from company tools. Keep each fact in one place and tell the agent which source to use.

For shared documents, review the draft before the agent writes changes. If a connection is unavailable, provide the relevant content in your private conversation.

If you find this useful, consider starring the repository so other PMs can discover it.

## What is in the folder

Start with `pm-profile.md` and `context/current-quarter.md`. The other files are there when you need them.

```text
pm-context-agent/
├── AGENTS.md                    Instructions the agent follows
├── CLAUDE.md                    Points Claude to those instructions
├── pm-profile.md                Your role, working style, and preferences
├── context/
│   ├── current-quarter.md       Your goals, metrics, and project links
│   ├── now.md                   Current status, next actions, and blockers
│   └── team-charter.md          Your team's purpose, scope, and responsibilities
├── skills/
│   ├── strategy-vision.md       Set direction for a product area
│   ├── roadmap-planning.md      Choose which problems to work on
│   ├── opportunity-scoping.md   Define a problem and size the opportunity
│   ├── prd.md                   Write requirements for one phase
│   ├── xp-analysis.md           Review A/B experiment results
│   ├── slack-writeups.md        Draft updates and asks
│   └── meeting-notes.md         Save notes and recall decisions
├── ProjectScopingDocs/
│   └── index.md                 Links to project documents and final outcomes
└── Notes/
    └── README.md                Index of your meeting notes
```

The files in `skills/` describe how to approach each task. You can use them as they are or adapt them to your team's way of working.

`ProjectScopingDocs/` holds an index, not copies of your project documents. Keep the full documents in your shared document tool and link to them. In your private copy, meeting notes live in `Notes/`.

## How it works

You describe what you need. The agent follows [AGENTS.md](AGENTS.md) to choose a workflow and read the context the task needs.

| Context | What it tells the agent | Where it lives in this setup |
|---|---|---|
| Your working preferences | Your role, writing style, and how you want to collaborate | [pm-profile.md](pm-profile.md) |
| Your current goals | Priorities, success metrics, constraints, and project links | [current-quarter.md](context/current-quarter.md) |
| Your active work | Current status, next actions, and blockers | [now.md](context/now.md) |
| Your team | Purpose, responsibilities, and who makes decisions | [team-charter.md](context/team-charter.md) |
| The project | Detailed scope, evidence, and past decisions | Linked project documents and recorded notes |

These files are a starting point. If some context already lives in company tools, link to it and use an available connection to read it. Keep one source for each fact so you do not have to maintain duplicate copies. A link alone does not give the agent access.

The agent then follows the relevant workflow. For longer documents, it drafts one or two sections and waits for your review. For short updates and experiment readouts, it produces a full draft. You can ask it to brainstorm, research, draft, or critique, and change the approach at any point.

If important information is missing or sources disagree, the agent flags it. For conflicting status updates, it uses the most recent recorded update date and asks if it cannot tell which is current. An empty placeholder stays unknown.

You review the work and make the decisions. The agent asks for approval before writing changes to a shared document.

## What you can ask for

You do not need to remember workflow names. Describe the work you want help with.

| Example request | What the agent helps you produce | Workflow |
|---|---|---|
| “Help me set the direction for this product area.” | A one-page vision with key bets, metrics, and OKRs | [Strategy and vision](skills/strategy-vision.md) |
| “Which problems should we focus on next?” | A Now / Next / Later roadmap tied to your goals | [Roadmap planning](skills/roadmap-planning.md) |
| “Is this problem worth solving?” | An opportunity scope with evidence, sizing, and phases | [Opportunity scoping](skills/opportunity-scoping.md) |
| “Write requirements for the first phase.” | A PRD with scope, testable requirements, risks, and launch needs | [PRD writing](skills/prd.md) |
| “What did this A/B test tell us?” | An analysis, a plain-language summary, and a Slack draft | [Experiment analysis](skills/xp-analysis.md) |
| “Turn this into an update for the team.” | A Slack draft suited to the audience | [Slack writeups](skills/slack-writeups.md) |
| “File these notes” or “What did we agree?” | A structured meeting note or an answer citing saved notes | [Meeting notes](skills/meeting-notes.md) |

For planning work, the documents connect: strategy sets the direction, the roadmap identifies the bets, opportunity scopes examine the problems, and PRDs define each phase of delivery. Each document links to the relevant work above it. You can start wherever you have a real need and provide the context available.

You can also brainstorm, ask for a critique, or research a question without producing a document. Research depends on the sources and tools your agent can access.

## Where work is saved

Keep full project documents in your shared document tool. Use [the project index](ProjectScopingDocs/index.md) to record their links and final outcomes. Save meeting notes in `Notes/` and link them from [the notes index](Notes/README.md).

The agent drafts shared-document changes for your approval. Drafting a Slack message does not send it.

## Keep it current

- Update goals and priorities in `context/current-quarter.md` when plans change.
- Update `context/now.md` when a project's status, next action, or blocker changes.
- Record new projects, outcomes, and meeting notes in their indexes.
- Refresh your profile, team charter, and workflows when your way of working changes.

If a fact lives in a connected company tool, update it there. Keep update dates current so the agent can spot stale information.

## About this project

Created by [Nakul Arora](https://github.com/nakularora19), based on my day-to-day product work.

Using this in your product work? [Share which workflow you use and what it helps with](https://github.com/nakularora19/pm-context-agent/issues). Keep company details private. If you write about your setup, a link back to this repository is appreciated.

Licensed under the [MIT License](LICENSE).
