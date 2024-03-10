```bash
controlplane ~ ➜  k run nginx-pod --image=nginx:alpine
pod/nginx-pod created # pod/pod_name
```

- View OS - `cat /etc/os-release`
- Log into image - `docker run --entrypoint /bin/bash -it python:3.6`

- Creating secrets. Creating use a yaml is hard (Got some encode mismatch)
1. Create env file that contains all secrets
2. Create secret using the command 
```bash
controlplane ~ ➜  cat data.env 
DB_Host=sql01
DB_user=root
DB_Password=password123

controlplane ~ ➜  k create secret generic db-secret --from-env-file=data.env
secret/db-secret created
```
