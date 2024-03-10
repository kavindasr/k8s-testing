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
|Create new pod     | `k run nginx --image=nginx -e color=pink` |
|Create pod on specific port    | `k run nginx --image=nginx --port=8080`   |
|Describe pod, can find errors       |`k describe pod <pod_id>` or `k describe po <pod_id>`    |
|Get basic details   | `k get pods <pod_name> -o wide`     |
|Create YAML file from command      | `k run redis --image=redis90 --dry-run=client -o yaml > pod.yaml`    |
|Edit running configuration         | `k edit pod <pod_name>` |
|Delete pod         | `k delete pod <pod_name not id>`  |
|View labels        | `k get pods --show-labels` or `k describe pod redis -> Labels`   |
|Start the nginx pod using a different command and custom arguments | `k run nginx --image=nginx --command -- <cmd> `   |
|Execute command inside a pod   | `k exec -it security-context-demo -- sh`    |
- When editing pods some values can't be change. The best way to do it is,
`k get pod pod_name -o yaml > pod.yml` -> edit the file and delete the pod and create a new. If you try to edit invaild filed new changes will save in /tmp directory. Then you can use `k replace --force -f /tmp/kubectl-edit-398200391.yaml`
    > spec: Forbidden: pod updates may not change fields other than `spec.containers[*].image`,`spec.initContainers[*].image`,`spec.activeDeadlineSeconds`,`spec.tolerations` (only additions to existing tolerations),`spec.terminationGracePeriodSeconds` (allow it to be set to 1 if it was previously negative)

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
|Create new service expose port as a clusterip  | `k expose pod redis --port=6379 --name redis-service` (If name is not specified it will create a service with the pod's name)|
|Create a pod and expose through a service  | `k run httpd --image=httpd:alpine --port=80 --expose=true`    |
|Describe service   | `k describe svc httpd` (Endpoint: 10.1.1.1:80)    |

## Evironemnt variables
### ConfigMap
|Description | Command |
|-----------------------|-----------------|
|Create a new config map named my-config based on folder bar   | `k create configmap my-config --from-file=path/to/bar`|
|Create a new config map named my-config with key1=config1 | `k create configmap my-config --from-literal=key1=config1 --from-literal=key2=config2` |
|List all ConfigMaps    | `k get cm` or `k get configmaps`  |
|View configmap values  | `k describe configmap my-configmap`   |

### Secrets
|Description | Command |
|-----------------------|-----------------|
|Create secret  | `k create secret generic app-secret --from-literal=DB_PASS=password`    |
|View secrets   | `k get secret`    |
|View secrets' encoded values   | `k get secret my-secret -o yaml   |
|View only secrets keys | `k describe secret my-secret`  |

## ServiceAccount
|Description | Command |
|-----------------------|-----------------|
|Create service account | `k create serviceaccount my-dashboard` or `k create sa my-dashboard`   |
|Create token for service account   | `k create token my-dashboard` | 

## ETC
- formatting outputs
```
    -o jsonOutput a JSON formatted API object.

    -o namePrint only the resource name and nothing else.

    -o wideOutput in the plain-text format with any additional information.

    -o yamlOutput a YAML formatted API object.
```
