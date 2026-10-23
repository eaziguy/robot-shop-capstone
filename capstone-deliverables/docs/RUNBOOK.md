# Robot Shop Incident Runbook

## 1. Safety
- Do not delete namespaces, PVCs, Docker volumes, or the Kind cluster during an incident.
- Do not run `docker system prune` or reset Docker Desktop.
- Keep the load generator scaled to zero while the control plane is unstable.
- Record commands and timestamps in incident notes.

## 2. Initial triage
Run from PowerShell:
```powershell
kubectl get nodes
kubectl get pods -A
kubectl get events -A --sort-by=.lastTimestamp
kubectl get pods -n robot-shop -o wide
kubectl get svc,endpoints -n robot-shop
```
If the API server is timing out or refusing connections, stop application changes and investigate cluster health before deploying monitoring stacks.

## 3. Check MySQL-dependent services
```powershell
kubectl get pods,svc,endpoints -n robot-shop
kubectl logs -n robot-shop deployment/mysql --tail=80
kubectl logs -n robot-shop deployment/ratings --tail=80
kubectl logs -n robot-shop deployment/shipping --tail=80
```
Confirm MySQL is Ready, the Service has endpoints, and credentials/database configuration agree. Do not print or commit secrets.

## 4. Check rollout state
```powershell
helm status robot-shop -n robot-shop
helm get values robot-shop -n robot-shop
helm get manifest robot-shop -n robot-shop
```
Before a change, render locally:
```powershell
helm lint "$HOME\Documents\robot-shop\K8s\helm"
helm template robot-shop "$HOME\Documents\robot-shop\K8s\helm" -n robot-shop > "$HOME\Documents\robot-shop-rendered.yaml"
```
Review the diff and rendered output before running `helm upgrade`.

## 5. Recovery principles
- Fix the earliest failing dependency first (for example, database readiness/connectivity before application probes).
- Make one change at a time and verify pod readiness, service endpoints, and a user journey.
- If a rollout makes things worse, check `helm history robot-shop -n robot-shop` and evaluate a rollback to a known-good revision. Verify the target revision before rolling back.
- Capture logs/events before restarting pods where practical.

## 6. Escalation
Escalate when the API server/etcd is unstable, persistent storage is at risk, data loss is suspected, or recovery requires destructive actions. Record what is known, what is uncertain, and the safest next action.
