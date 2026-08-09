# Changelog

## Unreleased — Phases 3–5

- Added JD-aware `resume-tailor`, application-aware `interview-griller`, `application-tracker`, and `outcome-review` Skills.
- Reworked `job-hunter` around normalized source adapters, hard filters, fit scores, source confidence, deduplication, and freshness.
- Added structured `Resume Model` and interview-feedback schemas; upgraded publisher to render Resume Model JSON with cross-platform font fallbacks while retaining Markdown input compatibility.
- Added regression fixtures for tailor, interviewer, tracker, hunter, and the end-to-end workflow.
- Documented the target architecture and local-file workflow.
