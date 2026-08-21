# Vibe Coding App Builder

[中文](./README.md)

A phase-gated SOP and reusable Codex Skill for turning a product idea into a **scoped, tested, runnable Web MVP**.

This project is not about asking AI to generate more code in one shot. It helps humans and AI work from the same product baseline, reduce scope drift, validate risky assumptions early, and ship in small reversible slices.

## Why this exists

AI coding projects often fail in predictable ways:

- coding starts before the problem or MVP boundary is clear;
- a polished prototype is mistaken for a usable product;
- vague requirements let the model improvise;
- frontend and backend are built as disconnected horizontal layers;
- “it should work” replaces actual tests and browser walkthroughs;
- prototype shortcuts silently reach production.

Vibe Coding App Builder turns that uncertainty into seven explicit phase gates.

## The workflow

| Phase | Output | Gate |
|---|---|---|
| 0. Problem & MVP | Product brief, assumptions, P0/P1/P2 | User, situation, job and boundary are clear |
| 1. Experience prototype | Interactive journey and key states | A target user can complete the journey unaided |
| 2. Product specification | Lightweight PRD and acceptance criteria | An implementer can judge conformance without guessing |
| 3. Technical plan | Architecture, data model, vertical slices | Complexity fits the MVP and risks have tests |
| 4. Implementation | Runnable project, tests and setup | Clean setup works and relevant checks pass |
| 5. Quality | Walkthrough evidence and fixes | Blockers and critical UX issues are resolved |
| 6. Release | Production version, record and rollback | The production journey is verified and reversible |

Read the full [Vibe Coding SOP](./Vibe-Coding-SOP.md).

## Repository layout

```text
.
├── README.md
├── README_EN.md
├── Vibe-Coding-SOP.md
├── examples/quick-start.md
├── templates/context-packet.md
└── skill/
    ├── SKILL.md
    ├── agents/openai.yaml
    └── references/vibe-coding-sop.md
```

## Install the Codex Skill

```bash
mkdir -p ~/.codex/skills/vibe-coding-app-builder
cp -R skill/. ~/.codex/skills/vibe-coding-app-builder/
```

Then start with:

```text
Use $vibe-coding-app-builder to turn this idea into a tested, runnable MVP: [your idea]
```

## Five-minute start

```text
Use $vibe-coding-app-builder.

Idea: [one sentence]
Target user: [user]
Critical experience: [desired outcome]

Do not code yet. Identify the three riskiest assumptions, define one core
user journey, split features into P0/P1/P2, and recommend the cheapest
next validation step.
```

More prompts: [examples/quick-start.md](./examples/quick-start.md)

Reusable turn template: [templates/context-packet.md](./templates/context-packet.md)

## Definition of done

- a target user can complete the core journey independently;
- no P0 blocker remains and important failures offer recovery;
- a clean environment starts from the documentation;
- relevant lint, type checks, tests and builds were actually run;
- critical desktop and mobile paths were walked through;
- placeholder data, temporary implementations and open risks are explicit.

## Scope

This workflow is ideal for individual builders and small teams creating Web MVPs. Authentication, payments, uploads, health data, personal information, native capabilities, high traffic or regulated domains still require dedicated security, privacy and engineering design.
