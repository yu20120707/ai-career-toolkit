---
name: resume-tailor
description: Use when adapting a master career profile and approved enhancement claims to a specific job description. Produces a traceable tailored resume without inventing direct experience.
---

# Resume Tailor

Create a job-specific resume from the shared Career Workspace. This Skill selects and reframes approved material; it does not create new unsupported experience.

## Required inputs

- `candidate-profile.json` and `enhancement-claims.json` from `resume-builder`.
- A `job.schema.json` record or the JD text to normalize into one.
- Optional `interview-feedback.json` files and `weak-points.json` from previous rounds.

## Outputs

Write under `applications/<job-id>/` (or an equivalent private workspace):

- `tailored-resume.json` — conforms to `schemas/resume-model.schema.json`.
- `tailored-resume.md` — readable rendering of the same model.
- `tailor-report.md` — JD parse, direct/adjacent/gap map, selected claim IDs, rejected candidates, weak-point warnings, and rationale.

Only include `active` claims. Preserve every selected claim ID in `tailored-resume.json`; do not alter claim text silently.

## Workflow

1. Parse the JD into must-have, preferred, responsibilities, domain, seniority, and keywords.
2. Map each requirement as `direct`, `adjacent`, or `gap` using explicit profile evidence.
3. Select relevant active claims. Promote direct evidence in ordering; reframe adjacent capability as transferable experience, never as use of the named missing technology.
4. Omit or de-emphasize gaps. Add a short learning plan to the report only; never add the gap as a resume skill.
5. Check against weak points: high-severity feedback linked to a claim must either lower its emphasis or be listed as a preparation warning.
6. Generate the structured model and Markdown from the same selected facts. Record why every claim was selected or excluded.

## Non-negotiable rules

- A JD requiring Kafka and a profile containing only RabbitMQ is `adjacent`, not direct Kafka experience.
- Do not activate a `candidate` claim, upgrade a role, or introduce a metric.
- High-risk selected claims must be listed in `tailor-report.md` with their existing drills.
- The report is a decision record, not generic advice.

## Regression fixtures

Use `../evals/resume-tailor/cases.json`. A passing result preserves hard facts, maps adjacent skills correctly, and writes all selected claim IDs to the resume model.
