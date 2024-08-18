## Certified Kubernetes Administrator (CKA) Exam Tips and beyond

Helpful tips to achieve CKA certification.

#### Resources I used for the Exam Preparation

- Kubernetes [Official Documentation](https://kubernetes.io/docs/home/), for sure!
- Killer Shell [CKA Exam Simulator](https://killer.sh/cka)
- ...and the most important:
  - Repeat, Repeat and Repeat...

#### Local Env. for Tests and messing around

- Minikube:
  - <https://minikube.sigs.k8s.io/docs/start/>
  - `minikube start --driver=docker --network-plugin=cni`
  - CNI: 
    - ./help/cilium.md
  - Pause and unpause k8s:
    - `minikube pause`
    - `minikube unpause`