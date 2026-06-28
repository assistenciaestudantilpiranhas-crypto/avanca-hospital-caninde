# AGENTS.md — GSI ONE / Avança Hospital

This repository follows GHAES — Global Health AI Engineering Standard.

Reference:
https://github.com/erickgomesal/ghaes

## Project Context

This repository contains the front-end, prototype screens, healthcare flows and local application logic for the GSI ONE / Avança Hospital ecosystem.

## Architecture

Official ecosystem architecture:

- GSI HealthTech = institutional ecosystem and umbrella brand.
- GSI ONE = digital health platform.
- Avança Hospital = implementation program and hospital use case.
- This repository = interface, screens, local logic and healthcare workflow prototype.

## Protected Healthcare Flows

AI agents must not alter these flows without explicit approval:

- patient registration;
- reception;
- triage;
- risk classification;
- medical consultation;
- nursing evolution;
- clinical observation;
- pediatric observation;
- obstetric observation;
- stabilization room;
- prescriptions;
- exams;
- pharmacy;
- transfers;
- discharge;
- indicators;
- observatory;
- patient record;
- reports.

## Mandatory Rules

All AI agents must follow these rules:

1. Follow GHAES principles.
2. Make surgical changes.
3. Never rewrite large files unnecessarily.
4. Never change healthcare workflows without explicit approval.
5. Never remove clinical fields without approval.
6. Never remove auditability or traceability.
7. Never invent clinical or operational rules.
8. Never modify database files from this repository.
9. Never commit without explicit authorization.
10. Never push without explicit authorization.

## Delivery Format

Every AI task must end with:

- files changed;
- what changed;
- what was not changed;
- UI impact;
- healthcare workflow impact;
- database/integration impact;
- validation performed;
- risks and pending points.
