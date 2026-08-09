# Shared Schemas

These schemas are the Phase 1 contract between Skills. Every record includes `schema_version: "1.0"`; additive changes require a compatible version update and a decision-log entry.

| Schema | Producer | Primary consumers |
|---|---|---|
| `candidate-profile.schema.json` | `resume-builder` | tailor, job hunter, publisher, interview griller |
| `enhancement-claim.schema.json` | `resume-builder`, `resume-tailor` | interview griller, application tracker, outcome review |
| `job.schema.json` | job hunter | application tracker, resume tailor |
| `application.schema.json` | application tracker | interview griller, outcome review |
| `resume-model.schema.json` | resume tailor | publisher, application tracker, interview griller |
| `interview-feedback.schema.json` | interview griller, outcome review | resume tailor, interview griller |

Rules:

- IDs are stable and never reused for a different entity.
- `original` is the user-provided or previously approved wording; `enhanced` is the proposed/approved stronger wording.
- A `high` interview-risk claim requires at least three drill questions.
- The application record stores paths to immutable submitted artifacts rather than copying their contents.
- The Resume Model is a reviewed presentation contract. It may reference active claim IDs, but it cannot create claim provenance.
