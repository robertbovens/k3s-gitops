# k3sup

> *Note*: this document is a work in progress

## Install k3s with k3sup

```bash
k3sup install --ip "192.168.42.41" \
    --k3s-version "v1.17.0+k3s.1" \
    --user "devin" \
    --k3s-extra-args "--node-taint k3s-controlplane=true:NoExecute --no-deploy servicelb --no-deploy traefik --no-deploy local-storage --no-deploy metrics-server"

k3sup join --ip "192.168.42.42" \
    --server-ip "192.168.42.41" \
    --k3s-version "v1.17.0+k3s.1" \
    --user "devin" \
    --k3s-extra-args "--node-taint k3s-storage=true:NoExecute"

k3sup join --ip "192.168.42.43" \
    --server-ip "192.168.42.41" \
    --k3s-version "v1.17.0+k3s.1" \
    --user "devin" \
    --k3s-extra-args "--node-taint k3s-storage=true:NoExecute"

k3sup join --ip "192.168.42.44" \
    --server-ip "192.168.42.41" \
    --k3s-version "v1.17.0+k3s.1" \
    --user "devin" \
    --k3s-extra-args "--node-taint k3s-storage=true:NoExecute"

k3sup join --ip "192.168.42.46" \
    --server-ip "192.168.42.41" \
    --k3s-version "v1.17.0+k3s.1" \
    --user "devin"

kubectl label node k3s-worker-a node-role.kubernetes.io/worker=worker
kubectl label node k3s-worker-b node-role.kubernetes.io/worker=worker
kubectl label node k3s-worker-c node-role.kubernetes.io/worker=worker
kubectl label node k3s-worker-d node-role.kubernetes.io/worker=worker
```