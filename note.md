# Cheetsheet
## General
|Description | Command |
|-----------------------|-----------------|
|View all api-resources and versions    | `k api-resources \| grep replicaset` |
|View all details   | `k get all` |
|List all services in namespace     | `k get svc -n=marketing`    |
|Dry run    | `kubectl run nginx --image=nginx --dry-run=client -o yaml > nginx-pod.yaml` |

## Pod
|Description | Command |
|-----------------------|-----------------|
|Create new pod     | `k run nginx --image=nginx` |
|Describe pod, can find errors       |`k describe pod <pod_id>`    |
|Get basic details   | `k get pods <pod_name> -o wide`     |
|Create YAML file from command      | `k run redis --image=redis90 --dry-run=client -o yaml > pod.yaml`    |
|Edit running configuration         | `k edit pod <pod_name>` |
|Delete pod         | `k delete pod <pod_name not id>`  |
|View labels        | `k get pods --show-labels` or `k describe pod redis -> Labels`   |

## ReplicationController & Replicaset
|Description | Command |
|-----------------------|-----------------|
|Get replication controller     | `k get replicationcontroller` |
|Get replicaset     | `k get replicaset` or `k get rs`  |
|Change/ scale replicaset   | `k replace -f <yml_file>` |
|Scale replicaset           | `k scale --replicas=6 -f <yml_file>` or `k scale --replicas=6 replicaset replicaset_name` |
|Delete replicaset          | `k delete replicaset <name>` or `k delete rs replicaset-1 replicaset-2` or (using labels) `k delete pod -l name=busybox-pod` |
|Extract yaml file          | `k get replicaset new-replica-set -o yaml`    |

## Deployments
|Description | Command |
|-----------------------|-----------------|
|Get deployments     | `k get deploy` or `k get deployments` |
|Create deployment(Imperative command)  | `kubectl run nginx --image=nginx --dry-run=client -o yaml > nginx-pod.yaml` |

## namespaces
|Description | Command |
|-----------------------|-----------------|
|Create namespace   | `k create namespace dev` or `k create ns dev` |
|List namespaces    | `k get ns`    |
|Create pod in namespace or can include in metadata     | `k create -f pod.yml --namespace=dev` |
|Get pods in namespace  | `k get pods --namespace=dev` , `k get pods -A (get pods in all namespaces)`  |
|Set namespace to dev   | `k config set-context $(k config current-context) --namespace=dev`    |
|Count pods in namespace    | `k get pods -n=research \| grep -c -v NAME` |

- Calling service - `db-service.dev.svc.cluster.local`
    - db-service(service name), dev(namespace), svc(service), cluster.local(default domain name)

## Service
|Description | Command |
|-----------------------|-----------------|
|Create service   | `k create namespace dev` or `k create ns dev` |

## ETC
- formatting outputs
```
    -o jsonOutput a JSON formatted API object.

    -o namePrint only the resource name and nothing else.

    -o wideOutput in the plain-text format with any additional information.

    -o yamlOutput a YAML formatted API object.
```
