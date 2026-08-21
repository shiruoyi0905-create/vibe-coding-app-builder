# Vibe Coding SOP Reference

Use this as the detailed phase-gate reference. Apply it to the work; do not copy it into project output unless asked.

## Routing

- Undefined idea or feature sprawl: Phase 0.
- Interaction or usability uncertainty: Phase 1.
- Ambiguous requirements: Phase 2.
- Architecture, data, or task slicing: Phase 3.
- Implementation and verification: Phase 4.
- Bugs, UX, responsiveness, or accessibility: Phase 5.
- Deployment, handoff, or production readiness: Phase 6.

## Cross-phase invariants

- Each phase has explicit input, output, acceptance evidence, and a go/revise/stop decision.
- Keep source-of-truth artifacts updated when decisions change.
- Prefer vertical slices through a user journey over horizontal layers.
- Keep changes small, independently verifiable, and reversible.
- Treat tests, browser observations, logs, screenshots, and user behavior as stronger evidence than generated explanations.
- Label the difference between prototype shortcuts and production-ready behavior.

## Phase gates

### 0 — Problem and MVP

Produce a one-page brief covering user, trigger, alternatives, pain, desired outcome, differentiation, and the three riskiest assumptions. Define one core journey and separate P0 from P1/P2. Pass when the audience and job are expressible in one sentence and P0 contains only journey-critical behavior. If demand is the biggest risk, run interviews or a demand test first.

### 1 — Experience prototype

Prototype the end-to-end core journey and relevant loading, empty, error, retry, and completion states. Observe 1–3 representative users without explaining the interface. Pass when they can complete the journey and the riskiest interaction has evidence beyond visual appeal.

### 2 — Product specification

Write a lightweight PRD with problem, user, core journey, P0 behaviors, screens and states, data and permissions, non-functional needs, metrics, non-goals, and Given/When/Then acceptance criteria. Keep a dated decision log. Pass when an implementer can judge conformance without guessing what subjective adjectives mean.

### 3 — Technical plan

Inspect the repository and runtime before choosing a stack. Specify component boundaries, state ownership, routing, data models, interface contracts, persistence, error handling, and environment variables. Slice work vertically through the core journey and give each task a verification method. Pass when complexity fits the MVP and the highest technical risks have tests.

### 4 — Implementation

Establish a runnable baseline and version-control checkpoint. Build skeleton, core path, real data path, failure states, then experience enhancements. After each slice, run relevant static checks, tests, build, and browser walkthrough. Pass when a clean environment can start the project, the core journey works, checks pass, and important failure behavior has automated or recorded manual validation.

### 5 — Quality

Walk through the product on common desktop and mobile sizes. Check refresh/back/repeat submit, slow and offline behavior, keyboard and focus, contrast and reduced motion, all status states, console errors, and resource failures. Record device/page, action, actual behavior, expected observable behavior, evidence, and priority. Fix blockers before comprehension issues, then decoration.

### 6 — Release

Verify the production build and environment, secret handling, error pages, minimum-data analytics, dependency and asset licenses, production core journey, and rollback. Document install, start, test, build, environment examples, structure, and known limitations. Record version, date, changes, verification, and rollback point.

## Safety baseline

- Keep secrets in environment variables and exclude local secret files from version control.
- Give authentication, payments, uploads, location, health, and personal data explicit threat and privacy review.
- Prefer sandbox accounts for external services.
- Confirm production analytics do not collect unnecessary data.

## Context packet

For every substantial turn, state: objective; exact source-of-truth sections; reproducible current state; requested delta; prohibited changes; acceptance commands and path; changed files; observed verification; open risks. Classify new requests as defect, P0 change, or later work. Update specifications before coding a core-journey change.

## Completion standard

The target user can independently complete the core journey; no P0 blocker remains; important failures offer a recovery path; clean setup works from documentation; relevant desktop and mobile paths were checked; placeholder data and temporary implementation are labeled; remaining risks and later work are explicit.
