---
name: outcome-review
description: Use after a real or simulated interview to convert feedback into persistent weak points and adjust claim defensibility without inventing outcomes.
---

# Outcome Review

Close the learning loop after an interview. Consume application artifacts and feedback, then produce data that the next tailor and interview session can use.

## Inputs

- `application.json`, current status, and interview-round feedback.
- Optional scorecard/transcript from `interview-griller`.
- Claim map referenced by that application.

## Outputs

- `interview/round-<n>-feedback.json` — conforms to `schemas/interview-feedback.schema.json`.
- `weak-points.json` at workspace root: a deduplicated, current list of weak points.
- `outcome.md`: factual result, evidence, next actions, and changed preparation priorities.

## Rules

1. Separate observed feedback from inference. Mark unknown outcomes as unknown.
2. Convert a repeated or severe inability to explain a claim into a weak point linked to the `claim_id`.
3. Recommend lowering a claim's `defensibility` or retiring it only with documented evidence; do not modify source claims silently.
4. Feed high-severity weak points into future tailoring warnings and interview question weighting.
5. Never generate acceptance probabilities or claim that an interviewer made a decision when none is known.
