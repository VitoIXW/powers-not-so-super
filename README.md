# powers-not-so-super

Like obra/superpowers but smaller and made for myself.

A lightweight personal toolkit for working with Codex using specialized roles, shared rules, and file-based coordination between agents.

## Core ideas

- Keep it simple.
- Start with planning first.
- Use an Architect role for brainstorming and task planning.
- Let each agent write only in its own area.
- Coordinate agents through files instead of relying only on chat context.

## Current structure

- `AGENTS.md`: global rules for all agents
- `roles/`: role definitions
- `tasks/`: runtime artifacts and reports produced by agents (ignored by git in this repo)

## Submodule setup (recommended)

Use this repository as a submodule named `.powers` inside each target project:

```bash
git submodule add <THIS_REPO_URL> .powers
git submodule update --init --recursive
```

Then run agents from the target project root and keep all coordination files under:

```bash
.powers/tasks/
```

This avoids cross-project collisions because each project has its own `.powers` working tree.
The `tasks/` folder is intentionally ignored in this repository, so generated artifacts do not pollute normal commits.

## Basic usage example

A simple workflow using the four default roles:

1. Architect
2. Coder
3. Reviewer
4. Tester

Agents communicate through files inside `.powers/tasks/`.

---

## Step 1 — Architect (analysis + brainstorming)

Start a Codex session and run:

```
Adopt the role defined in `.powers/roles/architect.md` and follow `.powers/AGENTS.md`.

First analyze the repository to understand its structure and purpose.

Then enter brainstorming mode.

My goal is the following:

[describe the task here]

Ask me questions if something is unclear.
Do not start planning yet.
```

The Architect will:

- analyze the repository
- ask clarification questions
- explore design options
- refine the problem

When the design is clear, ask the Architect to move to planning:

```
Proceed to planning.

Assume there will be 1 coder.

Write the architecture and plan documents, and create the coder assignment.
```

The Architect will then create files under:

```
.powers/tasks/architect/
```

---

## Step 2 — Coder (implementation)

Start another Codex session and run:

```
Adopt the role defined in `.powers/roles/coder.md` and follow `.powers/AGENTS.md`.

Read the assignment from:

.powers/tasks/architect/assignments/coder-1.md

Implement the task described there.

Write your implementation report to:

.powers/tasks/coder/coder-1/report.md
```

The coder will:

- implement the task
- document the work
- report issues or ambiguities

---

## Step 3 — Reviewer (code review)

Start a reviewer session:

```
Adopt the role defined in `.powers/roles/reviewer.md` and follow `.powers/AGENTS.md`.

Read:

.powers/tasks/architect/architecture.md
.powers/tasks/architect/plan.md
.powers/tasks/coder/coder-1/report.md

Review the implementation and produce a report in:

.powers/tasks/reviewer/review.md
```

The reviewer will:

- evaluate correctness
- check architecture consistency
- identify risks or improvements

---

## Step 4 — Tester (validation)

Start a tester session:

```
Adopt the role defined in `.powers/roles/tester.md` and follow `.powers/AGENTS.md`.

Read:

.powers/tasks/architect/plan.md
.powers/tasks/coder/coder-1/report.md

Evaluate the testing strategy and produce a report in:

.powers/tasks/tester/testing.md
```

The tester will:

- identify missing tests
- suggest validation scenarios
- highlight edge cases

---

## Better Architect prompt (recommended)

Use this prompt when starting the Architect to encourage proper repository analysis:

```
Adopt the role defined in `.powers/roles/architect.md`.

Before designing anything:

1. Analyze the repository structure.
2. Identify relevant files and architecture.
3. Determine whether the task is:
   - explaining code
   - modifying code
   - adding a feature
   - refactoring architecture

Then start brainstorming with me.

Do not jump to implementation planning yet.
Ask questions until the problem and constraints are clear.
```
