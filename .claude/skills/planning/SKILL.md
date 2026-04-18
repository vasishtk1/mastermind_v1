---
name: planning
description: Break down features, tasks, or projects into structured implementation plans. Use when asked to "plan", "design an approach for", "how should I implement", or before starting any non-trivial feature.
---

# Planning

Structured planning before implementation — requirements, breakdown, risks, and open questions.

## How It Works

1. Clarify the goal and constraints (ask if ambiguous)
2. Identify affected files/components/systems
3. Break work into ordered, completable tasks
4. Surface risks, unknowns, and decisions needed
5. Present the plan for approval before writing code

## Usage

Invoke when starting any non-trivial work:

```
"Plan the implementation of user authentication"
"How should I approach adding search to this app?"
"/planning add a notifications system"
```

## Output Format

```markdown
## Goal
[One sentence: what we're building and why]

## Scope
**In scope:** [what will change]
**Out of scope:** [explicit exclusions]

## Implementation Plan
1. [Task] — [file/component affected] (~[time estimate])
2. ...

## Open Questions
- [Decision needed before starting]

## Risks
- [Risk]: [mitigation]

## Success Criteria
- [ ] [Observable outcome]
```

## Present Results to User

After producing the plan:
- Wait for explicit approval before writing any code
- If the user asks to adjust scope, revise the plan rather than starting implementation
- Flag any task that blocks others

## Rules

ALWAYS:
- Ask clarifying questions if the goal is ambiguous
- List tasks in dependency order
- Separate "design decisions" from "implementation tasks"
- Include a rollback or cleanup step if the change is hard to reverse

NEVER:
- Start implementation without plan approval
- Produce a plan that skips testing or documentation tasks
- Assume unstated requirements
