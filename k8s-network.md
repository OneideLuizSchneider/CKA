#### k8s network

- To get IP(and more info... but...) from the Node:
  - `kubectl get node -o wide`
- Get network info:
  - `ip address`
  - `ifconfig`
- To see only the bridge interfaces:
  - `ip address show type brige`
- To look at ports:
  - `netstat --help`
  - `netstat -npl | grep ...`
  - See the kube-scheduler port:
    - `netstat -npl | grep scheduler`