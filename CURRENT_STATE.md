# Current State Baseline

> Baseline captured for Phase 0 on 2026-08-09. This document describes the repository as checked in, not the target architecture.

## Repository shape

The repository currently exposes four root-level Skills. There is no shared workspace, schema contract, fixture suite, or automated evaluation directory.

| Skill | Current input | Current output | Dependencies | Main gap |
|---|---|---|---|---|
| `resume-builder` | Resume file or conversation | `resume.md` | None | Enhanced statements disappear after generation; no claim provenance or risk metadata. |
| `resume-publisher` | Markdown resume | DOCX | `python-docx` | Markdown is the implicit data model; publisher has no structured input contract. |
| `interview-griller` | Resume + interview options | Scorecard, study guide, transcript | None | Cannot target a submitted resume, JD, claim map, or prior feedback. |
| `job-hunter` | Resume + preferences | Job report and JSON | Playwright MCP, sub-agents | Collection and matching are coupled; hard filters and source confidence are not explicit. |

## Current workflow

See [workflow-as-is.md](docs/workflow-as-is.md). The only durable hand-off today is a Markdown resume. `job-hunter` and `interview-griller` read that resume independently, so a later tailored version and the interview questions can drift apart.

## Compatibility constraints

- Keep the four existing root-level Skill directories in place. Moving them to `skills/` would break existing copy-based installations.
- Preserve Markdown resume input for `resume-publisher` during migration.
- Do not make browser automation a requirement for shared data creation.
- Do not add claims in the publisher; content enhancement remains the builder/tailor responsibility.

## Phase 0 conflict list

1. `resume-builder` encourages fabricated specifics (for example exact percentages) while `resume-publisher` requires claims to survive follow-up. A traceable claim contract resolves this without removing reasonable enhancement.
2. `interview-griller` outputs an uncalibrated “通过概率”; the target policy will use readiness, risk, and scorecard evidence instead.
3. `job-hunter` uses a weighted score only. A hard preference hit must be able to fail a role regardless of fit score.
4. Current file locations are root-level, while the target proposal shows `skills/`. This implementation keeps root-level locations and puts shared assets at the repository root.
