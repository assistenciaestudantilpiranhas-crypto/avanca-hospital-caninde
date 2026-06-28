# CODEX.md — GSI ONE Repository Instructions

## Mandatory GHAES Session Startup

At the start of each AI-assisted development session, read `GHAES-SESSION.md` once and apply it for the entire session.

Do not re-read all standard files before every prompt unless the task is sensitive, unclear or explicitly requires it.

This repository follows GHAES — Global Health AI Engineering Standard:
https://github.com/erickgomesal/ghaes

## Allowed Work

Codex may assist with:

- HTML changes;
- CSS adjustments;
- JavaScript fixes;
- UI behavior;
- screen flow improvements;
- front-end validation;
- reports;
- indicators;
- observatory screens;
- patient record UI;
- local prototype logic.

## Not Allowed Without Authorization

Codex must not:

- change database migrations;
- change Supabase schema;
- weaken authentication or permissions;
- remove clinical fields;
- invent clinical or operational rules;
- refactor large files unnecessarily;
- change unrelated modules;
- commit or push.

## Required Delivery

Every task must report:

- changed files;
- affected modules;
- UI impact;
- healthcare workflow impact;
- database/integration impact;
- validation performed;
- risks;
- whether commit or push was performed.
