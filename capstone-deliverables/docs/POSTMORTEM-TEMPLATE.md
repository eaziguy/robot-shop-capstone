# Blameless Incident Postmortem — Robot Shop

> Template only. Replace prompts with verified observations after an actual incident review or drill. Do not submit prompts as factual incident results.

## Summary
- Incident date/time:
- Duration:
- Severity:
- User impact:
- Services affected:

## What happened?
Describe observable symptoms and timeline. Separate confirmed facts from hypotheses.

## Timeline (UTC or clearly stated timezone)
| Time | Event / observation | Evidence |
|---|---|---|
| TBD | Alert or user symptom detected | Link/log |
| TBD | Investigation started | Notes |
| TBD | Root cause confirmed or narrowed | Evidence |
| TBD | Mitigation applied | Change/revision |
| TBD | Service verified | Test result |

## Root cause and contributing factors
- Confirmed root cause:
- Contributing factors:
- Unknowns / evidence still needed:

## Impact
Quantify failed requests, duration, and affected user journeys if measurements exist. If not measured, state that impact could not be quantified.

## What went well?
- TBD

## What could be improved?
- TBD

## Corrective actions
| Action | Priority | Owner | Due date | Status |
|---|---|---|---|---|
| Add dependency connectivity checks for MySQL-backed services | High | TBD | TBD | Open |
| Add request-level availability and latency instrumentation | High | TBD | TBD | Open |
| Document safe response to API server/etcd instability | High | TBD | TBD | Open |

## Blameless principle
Focus on system conditions, safeguards, observability, and process improvements rather than individual blame.
