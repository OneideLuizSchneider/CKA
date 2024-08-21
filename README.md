# Certified Kubernetes Administrator (CKA) Exam Tips and beyond

Helpful tips to achieve CKA certification.

## Resources I used for the Exam Preparation

- Kubernetes [Official Documentation](https://kubernetes.io/docs/home/), for sure!
- Killer Shell [CKA Exam Simulator](https://killer.sh/cka)
- ...and the most important:
  - Repeat, Repeat and Repeat...

## Local Env. for Tests and messing around

- Minikube:
  - <https://minikube.sigs.k8s.io/docs/start/>
  - `minikube start --driver=docker --network-plugin=cni`
  - CNI: 
    - ./help/cilium.md
  - Pause and unpause k8s:
    - `minikube pause`
    - `minikube unpause`

## CKA Curriculum until 2024-08-30

- **Troubleshooting 30%**
  - Evaluate cluster and node logging
  - Understand how to monitor applications
  - Manage container stdout & stderr logs
  - Troubleshoot application failure
  - Troubleshoot cluster component failure
  - Troubleshoot networking
- **Cluster Architecture, Installation & Configuration 25%**
  - Manage role based access control (RBAC)
  - Use Kubeadm to install a basic cluster
  - Manage a highly-available Kubernetes cluster
  - Provision underlying infrastructure to deploy a Kubernetes cluster
  - Perform a version upgrade on a Kubernetes cluster using Kubeadm
  - Implement etcd backup and restore
- **Services & Networking 20%**
  - Understand host networking configuration on the cluster nodes
  - Understand connectivity between Pods
  - Understand ClusterIP, NodePort, LoadBalancer service types and endpoints
  - Know how to use Ingress controllers and Ingress resources
  - Know how to configure and use CoreDNS
  - Choose an appropriate container network interface plugin
- **Workloads & Scheduling 15%**
  - Understand deployments and how to perform rolling update and rollbacks
  - Use ConfigMaps and Secrets to configure applications
  - Know how to scale applications
  - Understand the primitives used to create robust, self-healing, application deployments
  - Understand how resource limits can affect Pod scheduling
  - Awareness of manifest management and common templating tools
- **Storage 10%**
  - Understand storage classes, persistent volumes
  - Understand volume mode, access modes and reclaim policies for volumes
  - Understand persistent volume claims primitive
  - Know how to configure applications with persistent storage
- Doc:
  - <https://github.com/cncf/curriculum/>
