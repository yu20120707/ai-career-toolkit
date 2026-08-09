# Workflow

1. Run `resume-builder` once to create `candidate-profile.json`, `enhancement-claims.json`, and a master resume. Confirm any claim before it becomes `active`.
2. Run `job-hunter` with profile and preferences. Only `hard_filter: pass` records proceed to tailoring.
3. Run `resume-tailor` with one JD. It creates a `tailored-resume.json`, Markdown version, and claim-selection report in `applications/<job-id>/`.
4. Run `resume-publisher` from the JSON model, then use `application-tracker` to snapshot the JD and lock the submitted DOCX before changing status to `applied`.
5. Run `interview-griller` against the actual application record. It uses selected claims, JD requirements, and prior feedback.
6. Run `outcome-review` after each real or simulated round. It writes feedback and weak points that alter the next tailor/griller plan.

## Workspace layout

```
workspace/
  candidate-profile.json
  enhancement-claims.json
  jobs/job_<id>.json
  applications/job_<id>/
    application.json
    jd.md
    tailored-resume.json
    tailored-resume.md
    submitted-resume.docx
    interview/round-1-feedback.json
    outcome.md
  weak-points.json
```

Validate every JSON hand-off against its schema before the next Skill consumes it. Never overwrite a submitted artifact or mutate claim provenance to match later prose.
