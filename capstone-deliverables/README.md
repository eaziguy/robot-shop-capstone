# Robot Shop Capstone Deliverables

Starter pack for the Robot Shop capstone. Review against your official rubric before submission.

## Contents
- `docs/SLO-ERROR-BUDGET.md` — proposed SLI/SLO definitions and error-budget policy.
- `docs/RUNBOOK.md` — triage and recovery guidance.
- `docs/INCIDENT-DRILL.md` — safe drill procedure.
- `docs/POSTMORTEM-TEMPLATE.md` — fill with verified facts after an actual incident/drill.
- `monitoring/prometheus/alert-rules.yaml` — example infrastructure alerts.
- `monitoring/prometheus/prometheus.yml` — starter scrape configuration.
- `logging/loki/loki-config.yaml` — example single-binary Loki config for a lab.
- `logging/fluent-bit/fluent-bit.conf` — starter container-log input/filter config.
- `tracing/otel-collector-config.yaml` — OpenTelemetry Collector trace pipeline.
- `kubernetes/observability-namespace.yaml` — namespace manifest.

These are starter configurations, not evidence that observability is deployed or working. Validate versions and Kubernetes compatibility before deployment. With an unstable Kind cluster and 8 GB laptop, do not install every component at once. No AWS or paid cloud resources are required.

The postmortem is a template. Do not claim an unperformed drill or unverified incident details as facts.
