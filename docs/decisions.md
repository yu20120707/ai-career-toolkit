# Architecture Decisions

## ADR-001 — Preserve root-level Skill paths

- **Status:** accepted
- **Decision:** Keep `resume-builder/`, `resume-publisher/`, `interview-griller/`, and `job-hunter/` at the repository root.
- **Reason:** The current README instructs users to copy these directories directly. A directory migration would be a breaking change without product value.

## ADR-002 — JSON Schema is the shared contract

- **Status:** accepted
- **Decision:** Use versioned JSON Schema Draft 2020-12 files under `schemas/` for candidate profiles, enhancement claims, jobs, and applications.
- **Reason:** The Skills are prompt-driven but their hand-offs need a deterministic, language-neutral contract. YAML may be used for human-authored workspace files later, but its content must conform to these JSON shapes.

## ADR-003 — Claims retain enhancement provenance

- **Status:** accepted
- **Decision:** Every enhanced high-value statement records its source wording, enhancement types, assumptions, risk, defensibility, and drills.
- **Reason:** This permits reasonable enhancement while making its interview consequences explicit and reusable.

## ADR-004 — Workspace is local-file first

- **Status:** accepted
- **Decision:** The initial `workspace/` format is a portable local folder, not a database or web service.
- **Reason:** It keeps installation simple and makes each application auditable before a UI or persistence service exists.

## ADR-005 — Publisher is a renderer

- **Status:** accepted
- **Decision:** The publisher must not introduce or strengthen claims. It renders a reviewed source and eventually a structured resume model.
- **Reason:** Separating content decisions from layout prevents unnoticed factual drift.
