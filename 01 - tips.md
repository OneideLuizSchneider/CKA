#### Tips

Aliases:

- `alias k=kubectl`
- `alias kdr='kubectl -o yaml --dry-run=client'`
- `source <(kubectl completion bash) # set up autocomplete in bash into the current shell, bash-completion package should be installed first.`
- `echo "source <(kubectl completion bash)" >> ~/.bashrc # add autocomplete permanently to your bash shell.`
- `complete -o default -F __start_kubectl k`

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
  - `kubectl get nodes -o wide`
  - List Clusters in the config:
    - `kubectl config get-clusters`
  - Count Lines
    - `... wc -l`
    - `ls | wc -l`
    - `sed "1d"` removes the first line
    - `kubectl get pods | sed "1d" | wc -l`
    - `k get nodes | sed "1d" | wc -l`
    - ....
  - Remove a string with `sed`:
    - string: `current-context: minikube`
    - removing `minikube` from it:
      - `cat ~/.kube/config | grep current | sed -e "s/current-context: //"`, result -> `minikube`

Official Doc.: <https://kubernetes.io/docs/home/>
