## k8s Cluster Architecture

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

#### kube-apiserver

- It's the main component in k8s.
- The is responsible for:
  - Authenticate User
  - Validate Request
  - Retrieve data
  - Update ETCD
  - Scheduler
  - Kubelet

#### kube-controller-manager

- The Kubernetes controller manager is a daemon that embeds the core control loops shipped with Kubernetes. In applications of robotics and automation, a control loop is a non-terminating loop that regulates the state of the system. In Kubernetes, a controller is a control loop that watches the shared state of the cluster through the apiserver and makes changes attempting to move the current state towards the desired state. Examples of controllers that ship with Kubernetes today are the replication controller, endpoints controller, namespace controller, and serviceaccounts controller.

#### kube-proxy

- kube-proxy allows the communication among PODs inside k8s.
  - Runs in each Node(daemonset)
  - Looks in new services and applies the rules to each Node to forward traffic to those services to the PODs.

#### kube-scheduler

- The Kubernetes scheduler is a control plane process which assigns Pods to Nodes.
- The scheduler determines which Nodes are valid placements for each Pod in the scheduling queue according to constraints and available resources.
- The scheduler then ranks each valid Node and binds the Pod to a suitable Node.
- Multiple different schedulers may be used within a cluster; kube-scheduler is the reference implementation.

#### Replication Controller

Replication Controller make sure to create all pods needed in a deployment for example in the cluster.

#### kubelet

- kubelet is some kind of captain of the ship :D
  - Runs in the worker nodes
  - Register Node
  - Create PODs
  - Monitor Node & PODs
