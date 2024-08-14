# CKA

Helpful tips to achieve CKA certification

- To test it locally with Minikube:
  - <https://minikube.sigs.k8s.io/docs/start/>
  - `minikube start --driver=docker --network-plugin=cni`
  - CNI: 
    - ./help/cilium.md
  - Pause and unpause k8s:
    - `minikube pause`
    - `minikube unpause`