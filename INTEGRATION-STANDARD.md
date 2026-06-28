# INTEGRATION-STANDARD.md — GSI ONE ↔ Supabase Integration Standard

This document defines how the GSI ONE / Avança Hospital front-end must integrate with the Supabase database layer.

This repository follows GHAES — Global Health AI Engineering Standard.

Reference:
https://github.com/erickgomesal/ghaes

## 1. Purpose

The purpose of this standard is to ensure that the transition from local prototype data to Supabase persistence is safe, traceable, reversible and aligned with healthcare workflows.

The integration must preserve:

- patient identity;
- healthcare workflow continuity;
- auditability;
- data integrity;
- user accountability;
- compatibility with existing front-end behavior.

## 2. Repository Boundary

This repository may work on:

- front-end integration logic;
- API calls;
- UI behavior;
- localStorage compatibility;
- mapping between local records and Supabase records;
- user-facing validation and error messages.

This repository must not directly change:

- Supabase migrations;
- SQL schema;
- RLS policies;
- database functions;
- database triggers;
- audit_log structure.

Database changes belong to the database repository:

avanca-hospital-caninde-db

## 3. Local Data and Real Data

The system may contain two types of data during transition:

### Local Prototype Data

Data stored in localStorage for demonstration, UI testing and prototype continuity.

### Supabase Data

Real persisted data stored in the database, subject to RLS, auditability and traceability rules.

Agents must not silently mix these two layers without explaining the mapping.

## 4. Patient Identity Rule

Patient identity must be treated carefully.

When integrating patients with Supabase, the system must preserve:

- local patient ID;
- Supabase patient ID;
- CPF, when available;
- CNS/SUS card, when available;
- name;
- birth date;
- contact information, when applicable.

The field `pacienteSupabaseId` or equivalent must be preserved when linking a local patient to a real database record.

## 5. Deduplication Rule

The system must avoid creating duplicate real patients.

Before inserting a real patient into Supabase, check for existing identity when available.

Recommended order:

1. CPF
2. CNS/SUS card
3. other approved identity rule, only if explicitly defined

Do not deduplicate real patients only by name and birth date unless this rule has been explicitly approved.

## 6. Healthcare Workflow Continuity

Integration must not break or silently alter:

- reception;
- patient registration;
- triage;
- risk classification;
- consultation;
- nursing evolution;
- observation;
- stabilization room;
- prescriptions;
- exams;
- pharmacy;
- transfers;
- discharge;
- indicators;
- patient record.

Any integration change affecting these flows must be explicit, justified and traceable.

## 7. Auditability

Integration must preserve traceability for relevant actions.

When a front-end operation creates or updates real database records, the expected audit behavior must be identified.

Agents must report whether the change affects:

- audit_log;
- timestamps;
- user attribution;
- record history;
- clinical traceability.

## 8. Error Handling

Supabase or network errors must be handled with user-friendly messages.

The system must not:

- create silent failures;
- create partial records without informing the user;
- lose local data unexpectedly;
- expose raw technical errors to end users when a friendly message is possible.

## 9. RLS and Permissions

Front-end changes must respect database security.

The front-end must not assume access that RLS does not allow.

Any error related to permissions must be reported as a possible RLS or role issue and must not be bypassed in the front-end.

## 10. Integration Safety Rules

AI agents must:

- make surgical changes;
- preserve existing UI behavior unless change is requested;
- preserve localStorage compatibility during transition;
- avoid breaking existing demo flows;
- avoid creating real database records without explicit workflow purpose;
- explain database impact even when only front-end files are changed;
- avoid changing multiple modules at once unless approved.

## 11. Validation Checklist

Before delivery, verify:

- affected screen still opens;
- affected action still works;
- localStorage behavior was not unintentionally broken;
- Supabase call was reviewed;
- patient identity mapping was preserved;
- duplicate patient risk was considered;
- error handling was reviewed;
- healthcare workflow impact was described;
- no database schema or RLS change was made from this repository.

## 12. Final Report Requirement

Every integration-related task must end with:

1. Summary
2. Files changed
3. Front-end behavior changed
4. Supabase/database impact
5. Patient identity impact
6. Deduplication impact
7. Healthcare workflow impact
8. Auditability impact
9. Validation performed
10. Risks and pending decisions
11. Commit/push status

## 13. Commit and Push

No commit or push may be performed without explicit authorization.

Commit authorization and push authorization are separate.

Technology evolves. Principles endure.
