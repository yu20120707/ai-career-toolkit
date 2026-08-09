---
name: job-hunter
description: Use when finding and ranking job opportunities for a Career Workspace. Normalizes source results through adapters, applies hard filters before fit scoring, and records explainable job records.
---

# Job Hunter

Find jobs without tying matching logic to a particular site or browser script. Source collection is replaceable; normalized job records and ranking rules are the contract.

## Inputs

- `candidate-profile.json`; optional active claims for capability evidence.
- Preferences: cities, minimum salary, work mode, company/industry blacklist, target roles, seniority, and freshness window.

## Source-adapter contract

Each adapter returns normalized candidates before ranking:

```json
{"adapter":"official_career|greenhouse|lever|static_html|boss|liepin|browser_fallback","source_url":"https://...","company":"...","title":"...","location":"...","description":"...","posted_at":"ISO-8601 or unknown","captured_at":"ISO-8601","source_confidence":"low|medium|high"}
```

Use `OfficialCareerAdapter`, `GreenhouseAdapter`, `LeverAdapter`, or `StaticHtmlAdapter` first. `BossAdapter`, `LiepinAdapter`, and `BrowserFallbackAdapter` are fallbacks and must report their lower/unknown source confidence. A failed adapter is isolated and recorded; it does not cancel other sources.

## Evaluation order

1. **Normalize and deduplicate** by canonical URL; otherwise company + title + normalized location. Keep the most complete/newest record and list merged sources.
2. **Freshness**: mark records older than the requested window or unknown-date records as stale/unknown. Do not silently rank stale jobs as fresh.
3. **Hard filter**: city, work mode, minimum salary, and blacklist rules produce `pass` or `fail`. A `fail` is excluded from recommendations regardless of fit score.
4. **Fit score (0–100)**: score direct skills, adjacent skills, relevant responsibilities/domain, seniority, and explicit preferences. Report components and gaps; do not hide missing must-haves.
5. **Confidence**: source confidence plus JD completeness yields low/medium/high. A high score with weak evidence remains low confidence.

Write every retained result as `jobs/<job-id>.json` conforming to `schemas/job.schema.json`; `assessment.hard_filter`, `fit_score`, direct skills, adjacent skills, and gaps are mandatory after evaluation. Produce `job-report.md` sorted by hard-filter pass, fit score, freshness, then confidence.

## Boundaries

- No automatic application, messaging, or credential sharing.
- Browser automation is a fallback, not a dependency of ranking logic.
- Do not make compensation or reputation claims without source attribution and capture time.
