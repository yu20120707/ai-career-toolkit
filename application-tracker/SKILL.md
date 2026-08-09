---
name: application-tracker
description: Use when recording or updating job applications, submitted resume versions, interview rounds, outcomes, and next actions in a local Career Workspace.
---

# Application Tracker

Persist the auditable state of a job application. This Skill is a file-workflow tracker, not an auto-apply tool.

## Layout

```
applications/<job-id>/
  application.json
  jd.md
  tailored-resume.json
  tailored-resume.md
  submitted-resume.docx
  interview/round-<n>-feedback.json
  outcome.md
```

`application.json` conforms to `schemas/application.schema.json`. It points to immutable artifacts: once a resume is submitted, do not overwrite it; create a new application version or record the newer artifact before submission.

## Workflow

1. Deduplicate by canonicalized company + title + location + source URL. Reuse an existing job ID when it is the same opening.
2. Snapshot the JD and create/update the application record with `discovered` status.
3. Move status only through: `discovered → shortlisted → preparing → applied → screening → interview_1 → interview_2 → final → offer|rejected|withdrawn`. Record `updated_at` and `next_action` on every change.
4. Before `applied`, verify `job_record`, `jd_snapshot`, `tailored_resume`, submitted artifact path, and selected `claim_ids` resolve.
5. Store every interview round separately; never overwrite feedback from an earlier round.

## Boundaries

- Do not submit applications, contact recruiters, or infer an application result.
- Do not replace a submitted resume with a newly tailored version.
- Record unknown fields as unknown or ask; do not fabricate dates, salary, or feedback.

## Regression fixtures

Use `../evals/application-tracker/cases.json` to verify duplicate detection, status transitions, and submitted-artifact locking.
