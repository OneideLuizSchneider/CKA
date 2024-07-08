#### Tips

Aliases:

- alias k=kubectl
- alias kdr='kubectl -o yaml --dry-run=client'

Kubectl:
  - Create and Run a POD:
    - `kubectl run nginx --image=nginx`
  - Create a deployment:
    - `kubectl create deployment --image=nginx nginx`
  - Using `--dry-run=client`and Showing the Yaml `-o yaml`:
    - `kubectl run nginx --image=nginx --dry-run=client -o yaml`
    - `kubectl create deployment --image=nginx nginx --dry-run=client -o yaml`
    - `kubectl create deployment nginx --image=nginx --dry-run=client -o yaml > nginx-deployment.yaml`
  - Create a service:
    - `kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml `
    - `kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml`
  - Filter Labels:
    - `kubectl get pods -l 'environment in (production),tier in (frontend)`
  - Get PODs and their Nodes:
    - `kubectl get pod -o=custom-columns=NAME:.metadata.name,STATUS:.status.phase,NODE:.spec.nodeName`
    or
    - `kubectl get pod -o wide`

Official Doc.: <https://kubernetes.io/docs/home/>