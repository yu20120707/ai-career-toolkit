# Enhancement Policy

`resume-builder` may strengthen a candidate’s presentation, but each strengthened statement must stay internally coherent and trainable in interview practice.

## Evidence classes

| Class | Meaning | Resume treatment |
|---|---|---|
| Direct | The user supplied a concrete fact or can explain the work in detail. | May become `active` after normal review. |
| Adjacent | Existing work demonstrates a nearby transferable capability, not the named technology or domain. | State the transferable capability; do not claim direct use. |
| Speculative | A plausible but unconfirmed implementation, metric, or responsibility. | Keep as `candidate`, document assumptions, and confirm before use. |

## Modes

`balanced` is the default. It permits estimates such as “约 30%” only when the workspace preserves the estimation basis and risk. `conservative` excludes speculative content. `aggressive` may explore stronger coherent framing, but does not lower the confirmation requirement or allow invented hard facts.

## Claim lifecycle

`candidate` → `active` after candidate confirmation. A candidate can mark a claim `rejected` or later `retired`; preserve its source and notes for auditability. Only `active` claims may appear in a master or tailored resume.

## Review gate

Before activation, verify project linkage, stack compatibility, unit/scope compatibility for metrics, actual ownership boundaries, and interview preparedness. High-risk claims require at least three drills covering evidence/measurement, design trade-offs, and failure or edge-case handling.
