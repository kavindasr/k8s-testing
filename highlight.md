```bash
controlplane ~ ➜  k run nginx-pod --image=nginx:alpine
pod/nginx-pod created # pod/pod_name
```

- View OS - `cat /etc/os-release`
- Log into image - `docker run --entrypoint /bin/bash -it python:3.6`
