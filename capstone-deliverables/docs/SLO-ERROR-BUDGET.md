# Robot Shop SLO and Error-Budget Policy

**Status:** Proposed lab policy. Replace targets if the course rubric specifies different values.

## Scope
The customer-facing service is the Robot Shop web frontend and its user-facing request path. Dependencies include catalogue, cart, user, payment, shipping, ratings, databases, Redis, and RabbitMQ.

## Service-level indicators (SLIs)
1. **Availability:** successful eligible HTTP requests divided by all eligible HTTP requests, excluding defined health checks and requests rejected by the client before reaching the service.
2. **Latency:** eligible HTTP requests completed within 1 second divided by all eligible HTTP requests.
3. **Monitoring coverage:** expected application services with current scrape targets/log collection. This is diagnostic, not a customer-facing SLO.

## Proposed objectives
- Availability: **99.0% over a rolling 7-day window**.
- Latency: **95% of eligible requests under 1 second over a rolling 7-day window**.

These are proposed educational targets, not measured results.

## Error budget
For a 99.0% availability objective, the error budget is 1.0% of eligible requests in the measurement window. For example, out of 10,000 eligible requests, up to 100 failures would meet the objective. This is an example, not a claim about observed traffic.

## Policy
- Review SLOs after each load test and incident drill.
- If less than 50% of the error budget remains, prioritize reliability work and reduce risky changes.
- If the budget is exhausted, pause nonessential feature work until a corrective action plan is agreed.
- Record each breach with time window, affected user journey, evidence, mitigation, and follow-up owner.
- Do not claim compliance until request metrics have been collected and the calculation is reproducible.

## Measurement caveat
The included alert rules are generic Kubernetes/container alerts, not a complete request-based SLO implementation. To measure the SLIs, instrument the frontend or ingress to expose request totals, failures, and latency histograms, then implement recording rules for the actual metric names.
