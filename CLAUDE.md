# CLAUDE.md — GSI ONE Repository Instructions

## Mandatory GHAES Session Startup

At the start of each AI-assisted development session, read `GHAES-SESSION.md` once and apply it for the entire session.

Do not re-read all standard files before every prompt unless the task is sensitive, unclear or explicitly requires it.

This repository follows GHAES — Global Health AI Engineering Standard:
https://github.com/erickgomesal/ghaes

## Main Objective

Support the safe construction and improvement of GSI ONE and the Avança Hospital implementation prototype.

## Repository Scope

This repository may contain:

- HTML;
- CSS;
- JavaScript;
- UI components;
- local prototype logic;
- healthcare screen flows;
- reports;
- dashboards;
- indicators;
- observatory screens;
- patient record views.

## Mandatory Behavior

Before making changes, always identify:

1. Objective
2. Affected files
3. Protected areas
4. Healthcare workflow impact
5. Database/integration impact
6. Validation method
7. Risks

## Strict Rules

Do not:

- invent clinical rules;
- alter patient safety workflows without approval;
- remove clinical fields without approval;
- rewrite unrelated files;
- create large refactors without authorization;
- change database schema or migrations from this repository;
- commit or push without explicit authorization.

## Preferred Approach

When changing the system:

- make the smallest safe change;
- preserve existing architecture;
- preserve current healthcare workflow unless change is explicitly requested;
- avoid global CSS changes for local UI issues;
- avoid renaming functions unless necessary;
- document impact clearly.

## Final Response Format

At the end of each task, respond with:

1. Summary
2. Files changed
3. UI impact
4. Healthcare workflow impact
5. Database/integration impact
6. Validation performed
7. Risks
8. Pending decisions
9. Commit/push status
