```
# 1. Verify connectivity & version
kubectl cluster-info
kubectl version

# 2. See all nodes (machines) and their status
kubectl get nodes -o wide
# -o wide adds internal/external IPs, OS image, container runtime

# 3. See which nodes are control-plane vs worker
kubectl get nodes --show-labels
# or list only workers:
kubectl get node --selector='!node-role.kubernetes.io/control-plane'

# 4. See what's running on each node
kubectl get pods --all-namespaces -o wide

# 5. List all namespaces
kubectl get namespaces

# 6. Full resource overview in one shot
kubectl get all --all-namespaces

# 7. Resource usage (requires metrics-server)
kubectl top nodes
kubectl top pods --all-namespaces

# 8. Recent events (errors, scheduling, etc.)
kubectl get events --all-namespaces --sort-by=.lastTimestamp
```

Useful follow-ups once you've spotted something interesting: 


| Command | What it tells you |
|---|---|
| `kubectl describe node <name>` | CPU/memory capacity, taints, conditions, assigned pods |
| `kubectl describe pod <name> -n <ns>` | Events, container specs, volume mounts, scheduling history |
| `kubectl get pod <name> -o yaml` | Full manifest (useful for understanding config) |
| `kubectl get svc --all-namespaces` | Exposed services and their types (ClusterIP, NodePort, LoadBalancer) |
| `kubectl get ingress --all-namespaces` | Ingress rules / external DNS entry points |
| `kubectl get storageclass` | Available storage classes for PVCs |
| `kubectl config view` | Your current kubeconfig (contexts, users, clusters) |
