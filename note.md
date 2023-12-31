# Cheetsheet
## Pod
- Create new pod - `kubectl run nginx --image=nginx`
- Describe pod - `kubectl describe pod <pod_id>`
- Get more details - `kubectl get pods <?pod_name> -o wide`
- Create YAML file from command - `kubectl run redis --image=redis90 --dry-run=client -o yaml > pod.yaml`
- Edit running configuration - `kubectl edit pod <pod_name>`
 
