#### Minikube

- Start a basic Cluster with Docker and CNI:
  - `minikube start --driver=docker --network-plugin=cni`
- Pause it:
  - `minikube pause`
- Add a worker Node:
  - `minikube node add --worker`