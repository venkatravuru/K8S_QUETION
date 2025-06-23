🔹 Scenario 1: Pod in CrashLoopBackOff
✅ Use Case:
Your application Pod keeps restarting right after it starts.

❓ Interview Question:
You deployed a Pod, but it's stuck in CrashLoopBackOff. What steps do you take to troubleshoot and fix it?

💡 Answer:
Check Pod logs:

bash
Copy
Edit
kubectl logs <pod-name>
Check if it’s a config issue: Missing env vars, DB unreachable, crash in startup script.

Describe the Pod to view events:

bash
Copy
Edit
kubectl describe pod <pod-name>
Check liveness probe settings — it may be killing the container too early.

Fix the root issue, update the YAML, and reapply.

🔹 Scenario 2: Pod Stuck in Pending State
✅ Use Case:
You created a Pod, but it's stuck in Pending for several minutes.

❓ Interview Question:
A Pod is not scheduling and remains in Pending. What could be causing this, and how would you resolve it?

💡 Answer:
Describe the Pod:

bash
Copy
Edit
kubectl describe pod <pod-name>
Common causes:

Insufficient node resources (CPU/Memory)

PVC not bound

No matching Tolerations / Affinity issues

Fix it:

Adjust resource requests or limits

Scale the cluster

Modify affinity or taints/tolerations

