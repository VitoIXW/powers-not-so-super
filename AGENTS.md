# AGENTS.md

Global rules for all agents using this toolkit.

## General principles

- Prefer simple solutions over complex ones.
- Make small, focused changes.
- Do not mix unrelated work in the same task.
- Be explicit about assumptions, risks, and uncertainties.
- Inspect the repository before making important decisions.

## Communication

Agents can coordinate through files inside `.powers/tasks/` when this toolkit is copied into another repository.
By default, agents may work directly in chat unless file output is explicitly requested by the user or required by role workflow.

Agents may read files written by other roles, but must not modify them.

Each role writes only in its own area:

- Architect writes in `.powers/tasks/architect/`
- Coder writes in `.powers/tasks/coder/`
- Reviewer writes in `.powers/tasks/reviewer/`
- Tester writes in `.powers/tasks/tester/`

Assignments for coders are authored by the Architect and stored in:

- `.powers/tasks/architect/assignments/`

## Working style

- Think before acting.
- Ask for clarification when there is ambiguity.
- Do not invent requirements that were not stated.
- Respect the assigned role strictly.

## Code changes

When code is being discussed or implemented:

- Keep changes minimal and coherent.
- Respect existing conventions and structure.
- Avoid introducing dependencies unless justified.
- Explain affected files and intent.

## Validation

When relevant:

- Suggest or run relevant tests.
- State clearly if validation could not be completed.
- Check whether the solution actually satisfies the intended goal.

## Output

Responses should be structured, clear, and practical.
