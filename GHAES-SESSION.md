# GHAES Session Mode — GSI ONE

At the beginning of each AI-assisted development session, load this file once and apply it for the entire session.

This repository follows GHAES — Global Health AI Engineering Standard.

Reference:
https://github.com/erickgomesal/ghaes

## Session Rule

Use the repository instructions from:

- AGENTS.md
- CLAUDE.md
- CODEX.md
- GSI-ONE-STANDARD.md

Do not re-read all instruction files before every prompt unless the task requires it.

For normal tasks, apply the already loaded GHAES rules from the session context.

## Re-read Instructions Only When

Re-read the repository standards when the task touches:

- healthcare workflow;
- patient data;
- triage;
- risk classification;
- consultation;
- prescription;
- exams;
- pharmacy;
- transfer;
- discharge;
- auditability;
- indicators;
- database integration;
- authentication;
- user roles or permissions;
- unclear or conflicting instructions.

## Mandatory Rules

- Make surgical, minimal and traceable changes.
- Do not commit without explicit authorization.
- Do not push without explicit authorization.
- Do not change healthcare workflows without explicit approval.
- Do not invent clinical or operational rules.
- Do not remove auditability.
- Do not change database integration without explaining impact.
- Preserve GSI HealthTech architecture.
- Preserve GSI ONE as the platform.
- Preserve Avança Hospital as the implementation program/case.

## Required Final Report

Every task must end with:

1. Summary
2. Files changed
3. UI or workflow impact
4. Database/integration impact
5. Healthcare workflow impact
6. Validation performed
7. Risks
8. Pending decisions
9. Commit/push status

## Short User Command

After this file is loaded once, the user may use short commands such as:

"Follow GHAES session mode and perform the task."

or

"Siga o modo GHAES da sessão. Não faça commit nem push."

Technology evolves. Principles endure.
