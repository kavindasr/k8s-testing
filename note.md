# Cheetsheet
## Pod
|Description | Command |
|-----------------------|-----------------|
|Create new pod     | `k run nginx --image=nginx` |
|Describe pod       |`k describe pod <pod_id>`    |
|Get more details   | `k get pods <pod_name> -o wide`     |
|Create YAML file from command      | `k run redis --image=redis90 --dry-run=client -o yaml > pod.yaml`    |
|Edit running configuration         | `k edit pod <pod_name>` |
|Delete pod         | `k delete pod <pod_name not id>`  |
 
## ReplicationController
|Description | Command |
|-----------------------|-----------------|
|Get replication controller     | `k get replicationcontroller` |