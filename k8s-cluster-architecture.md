#### k8s Cluster Architecture

- Master
  - Manages, Plan, Schedule, Monitor, Nodes
  - ETCD
    - is a distributed reliable key-value store that is Simple, Secure & sFast
  - kube-apiserver
    - The kube-apiserver services the REST operations and provides the frontend to the cluster shared state through which all other components interact
  - kube-controllermanager
    - The kube-controller-manager runs as a pod in your control plane. It's config file is located in /etc/kubernetes/manifests , a kube-controller-manager. yaml .
  - kube-scheduler
    - The Kubernetes scheduler is a control plane process which assigns Pods to Nodes. The scheduler determines which Nodes are valid placements for each Pod in the scheduling queue according to constraints and available resources.
- WorkerNodes
  - Where the applications/containers run
  - kubelet
    - Kubelet plays an essential role in the Kubernetes framework, managing and coordinating pods and nodes. Its features include pod deployment, resource management, and health monitoring, all contributing considerably to a Kubernetes cluster's operational stability.
  - kube-proxy
    - Kube-Proxy is a network proxy that runs on each node in a Kubernetes cluster. It is responsible for maintaining network connectivity between services and pods.
