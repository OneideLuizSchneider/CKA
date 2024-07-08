#### k8s Version and Upgrades

- Versions:
- v1.30.0

| MAJOR             | MINOR        | PATCH     |
| :---------------- | :------:     | --------: |
|                   |   Features   | Bug Fixes |
|                   |   Functionalities   |  |


##### Upgade k8s

Run to see what versions are available and which components you need to upgrade:
  - `kubeadm upgrade plan`
- Next, Upgrade the kubeadmin itself
  - `apt-get upgarde -y kubeadm=1.30.1-00`
  - `kubeadm upgrade apply v1.30.1`
- Next, Upgrade kubelet:
  - `apt-get upgarde -y kubelet=1.30.1-00`
  - `systemctl restart kubelet`
- To confirm, run:
  - `k get nodes`
- After go on every Worker Node and uograde them:
  - `kubectl drain node_name`
  - `apt-get upgarde -y kubeadm=1.30.1-00`
  - `apt-get upgarde -y kubelet=1.30.1-00`
  - `kubeadm upgrade node config --kubelet-version v1.30.1`
  - `systemctl restart kubelet`
  - Now make the Node schedulable again:
    - `kubectl uncordon node_name`


Some docs:
- <https://kubernetes.io/docs/concepts/overview/kubernetes-api/>
- <https://github.com/kubernetes/community/blob/master/contributors/devel/sig-architecture/api-conventions.md>
- <https://github.com/kubernetes/community/blob/master/contributors/devel/sig-architecture/api_changes.md>
