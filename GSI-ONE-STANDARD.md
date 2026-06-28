# GSI-ONE-STANDARD.md — GSI ONE / Avança Hospital Standard

This document defines local engineering and healthcare workflow rules for the GSI ONE / Avança Hospital repository.

This repository follows GHAES — Global Health AI Engineering Standard.

Reference:
https://github.com/erickgomesal/ghaes

## 1. Product Role

GSI ONE is the digital health platform.

Avança Hospital is the implementation program and hospital use case.

This repository represents the front-end, screens, workflows and prototype behavior used to evolve the system.

## 2. Protected Architecture

Official architecture:

- GSI HealthTech = ecosystem and institutional brand.
- GSI ONE = platform/system.
- Avança Hospital = implementation program/case.
- Avança Hospital Canindé = first practical implementation.

Do not rename or reinterpret this architecture without explicit approval.

## 3. Protected Healthcare Modules

The following modules are protected:

- Dashboard;
- Patients;
- Reception;
- Attendance;
- Call Panel;
- Triage;
- Risk Classification;
- Consultation;
- Nursing Evolution;
- Clinical Observation;
- Pediatric Observation;
- Obstetric Observation;
- Stabilization Room;
- Exams;
- Pharmacy;
- Transfers;
- Indicators;
- Observatory;
- Patient Record;
- Reports;
- Settings.

## 4. Workflow Safety Rules

Changes must not silently alter:

- patient journey;
- timestamps;
- triage flow;
- risk classification logic;
- consultation flow;
- observation flow;
- stabilization flow;
- prescription flow;
- exam flow;
- pharmacy flow;
- transfer flow;
- discharge flow;
- indicators;
- auditability.

Any change affecting healthcare workflow must be explicit, justified and traceable.

## 5. Front-End Rules

- Prefer small, local changes.
- Avoid global CSS changes for local issues.
- Avoid rewriting full files.
- Avoid renaming existing functions unless necessary.
- Preserve existing IDs, classes and actions unless change is required.
- Preserve compatibility with current localStorage and Supabase integration state.

## 6. Database Boundary

This repository must not be used to change:

- Supabase migrations;
- SQL schema;
- RLS policies;
- authentication tables;
- database roles;
- audit_log structure.

Database changes belong to the database repository.

## 7. Validation Checklist

Before delivery, verify:

- screen still opens;
- navigation still works;
- affected action works;
- no unrelated module was changed;
- protected healthcare workflow was preserved;
- database integration was not broken;
- console errors were checked when possible.

## 8. Commit and Push

No commit or push may be performed without explicit authorization.

Commit authorization and push authorization are separate.
