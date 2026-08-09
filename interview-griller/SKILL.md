---
name: interview-griller
description: Use when practicing a specific technical interview against the actual submitted resume, target JD, claim map, current round, and prior feedback.
---

# Interview Griller

Run an application-aware technical interview. The goal is to test the exact story submitted for this role, identify weaknesses, and return reusable feedback—not to estimate a pass probability.

## Inputs

Required for an application-aware session:

- Job record/JD; `applications/<job-id>/submitted-resume.docx` or `tailored-resume.md`; and selected `claim_ids`.
- `enhancement-claims.json` for provenance, risks, and drills.
- Current interview round (default `screening`) and optional prior `interview-feedback.json` / `weak-points.json`.

For a resume-only session, state that no JD or submitted-artifact validation is available and ask for them before claiming application-specific coverage.

## Question plan

Build a plan before asking the first question. Default allocation is:

| Source | Weight | Rule |
|---|---:|---|
| Selected high-value/high-risk claims | 40% | Each high-risk claim gets a 3–5 layer chain. |
| JD must-have skills and responsibilities | 25% | Prefer the actual job wording. |
| Prior weak points | 20% | Prioritize high severity and repeated misses. |
| New/general technical ability | 15% | Use only after the application context is covered. |

For a high-risk cache claim, the chain must include evidence/measurement, design or TTL/invalidation, consistency/failure behavior, trade-off, and ownership boundary where applicable. Do not stop at a definition question.

## Conduct

- Ask one question at a time; do not reveal the ideal answer early.
- Adapt depth after each answer: A → harder trade-off; B → one more layer; C → guided retry; D → concise explanation, retry, then score.
- Keep style (friendly or pressure) independent from scoring.
- Do not ask unrelated random trivia just to fill a quota.

## Outputs

Write under `applications/<job-id>/interview/` when an application exists:

- `round-<n>-scorecard.md`: readiness, risk, dimensions, question coverage, and evidence-backed assessment.
- `round-<n>-feedback.json`: conforms to `schemas/interview-feedback.schema.json`; include every C/D weak point and linked claim ID when known.
- `round-<n>-transcript.md`: question, answer summary, follow-up layer, and grade.

Do not output a fabricated “pass probability.” Use readiness (`not_ready`, `developing`, `ready`) plus concrete risks and next drills.

## Boundaries

- This Skill does not edit resumes or activate claims.
- A weak answer may trigger a recommendation to lower claim defensibility, but only `outcome-review` records that recommendation with evidence.
- Preserve factual interviewer feedback separately from coaching inference.
