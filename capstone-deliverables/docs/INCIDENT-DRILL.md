# Robot Shop Incident Drill

**Type:** Tabletop / controlled lab drill. Mark completed only after it is actually performed.

## Scenario
The frontend is reachable, but ratings and shipping return errors because they cannot connect to MySQL. During the same window, Kubernetes API operations intermittently time out.

## Objectives
- Identify the customer-visible symptom.
- Determine whether the failure is in the frontend, application dependency, database, or Kubernetes control plane.
- Preserve evidence and avoid destructive recovery.
- Communicate status and record follow-up actions.

## Safe procedure
1. Announce the drill and record the start time.
2. Keep the load generator at zero unless the cluster is confirmed stable.
3. Capture `kubectl get pods -A`, `kubectl get events -A --sort-by=.lastTimestamp`, MySQL/ratings/shipping logs, and `kubectl get svc,endpoints -n robot-shop`.
4. State the likely failing dependency and the evidence supporting it.
5. Verify whether MySQL is Ready and whether its Service has an endpoint.
6. If the control plane is unstable, stop changes and focus on preserving evidence.
7. Record the recovery decision and why it is safe.
8. End the drill, document findings, and assign follow-up actions.

## Success criteria
- Evidence is captured before disruptive action.
- MySQL connectivity is treated as a hypothesis and validated rather than assumed.
- Application failure is distinguished from control-plane instability.
- No PVC, Docker volume, namespace, or cluster is deleted.
- Follow-up actions have an owner and due date.

## Results (fill after execution)
- Date/time:
- Participants:
- Actual observations:
- Was the drill successful?:
- Evidence location:
- Follow-up actions and owners:
