#### kube-proxy

- kube-proxy allows the communication among PODs inside k8s.
  - Runs in each Node(daemonset)
  - Looks in new services and applies the rules to each Node to forward traffic to those services to the PODs.
